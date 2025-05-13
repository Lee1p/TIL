### 채팅방(Chatroom) 엔티티 설계
📌 "채팅방 그 자체에 대한 정보만 담당하는 테이블"
채팅방 기본 고유 ID가 존재, 그리고 채팅방 제목, 설명글, 공지사항  </br> -> 공지사항, 설명글은 채팅방 1개당 1개만 존재 (공지사항 및 설명글 수정은 방장만 가능함.)
채팅방 제목은 음.. 따른 플랫폼 참고하니까 수정이 가능하게 두는 편인데, 설계 단순화 및 채팅방 생성을 더 할 수 있으니까 제목은 그대로 유지하면서 설계를 할려고한다.</br>
대신 공지사항 및 설명글은 수정이 가능하고 단순 수정이 아니라 수정한 공지의 히스토리로 통계, 감사 로그 활용 즉 , 공지사항 테이블은 따로 만들어서 fk로 참조할거임. </br>
```sql
CREATE TABLE Chatroom ( 
  chatroom_id           NUMBER PRIMARY KEY, -- 채팅방 고유 ID
  title                 VARCHAR2(100) NOT NULL CHECK (LENGTH(title) BETWEEN 2 AND 100), --	채팅방 제목 (필수, 수정 불가, 길이 제약: 2자 이상 30자 이하)
  thumbnail_image_url   VARCHAR2(255), -- 썸네일 이미지 경로 (URL 기반, 직접 저장 아님)
  is_deleted            CHAR(1) DEFAULT 'N' CHECK (is_deleted IN ('Y', 'N')), -- 채팅방 삭제 여부 
  created_at            DATE DEFAULT SYSDATE, -- 채팅방 생성일 
  latest_notice_id      NUMBER, -- 최신 공지사항 ID

  CONSTRAINT fk_chatroom_latest_notice FOREIGN KEY (latest_notice_id)
    REFERENCES Chatroom_Notice_History(notice_id)
);
```

### 채팅방(Chatroom_User) 사용자 엔티티 설계

📌 "사용자가 어떤 채팅방에 참여 중인지, 어떤 역할을 가지고 있는지를 추적하는 관계 테이블"

1명의 사용자는 여러개의 방을 생성할 수 있음. (1:N관계) </br>
우리 채팅방 사용자 권한은 방장,매니저,일반으로 구성되어있다. 사용자 역할은 <b>채팅방마다 다르게 적용</b>해야 한다. </br>
음.. 생각한거는 일단 그래서 Entity 속성값으로 역할 즉 , role 이 check로 owner, manager, member로 할 생각이다.

🔹 하나의 사용자 → 여러 채팅방 참여 가능
🔹 하나의 채팅방 → 여러 사용자 참여 가능
👉 즉, 다대다(N:N) 관계

</br>

 joined_at (입장 시간)
언제 채팅방에 입장했는지 기록

통계 용도 (예: “하루 방문자 수”, “누가 먼저 들어왔는가”)

정렬/조회 가능 (예: 방에 늦게 들어온 사람 따로 표시 등)

 left_at (퇴장 시간)
언제 나갔는지를 기록

이게 있어야 재입장 시, 이전에 나갔던 시점 이후의 메시지만 다시 보여줌.

입장/퇴장 반복 시에도 마지막 퇴장 시각을 추적 가능

last_read_message_id는 이전에 본 메시지 이후로 새로운 메시지가 있다면 → “안 읽은 메시지”로 표시해줘야 함

채팅방 목록에서 🔴 뱃지 숫자 표시하려면 → 어디까지 읽었는지 알아야 계산 가능

last_read_message_id는
“이 사용자가 이 채팅방에서 어디까지 메시지를 읽었는지”를 저장해서,
안 읽은 메시지를 판단하고, 알림을 제어하는 핵심 필드


```sql
CREATE TABLE chatroom_user (
    chatroom_user_id     NUMBER PRIMARY KEY, -- 고유 관계 ID (시퀀스 관리)

    chatroom_id          NUMBER NOT NULL,    -- 참여한 채팅방 ID (FK → chatroom)
    member_id            NUMBER NOT NULL,    -- 참여한 사용자 ID (FK → members)

    role                 VARCHAR2(10) DEFAULT 'MEMBER' 
                         CHECK (role IN ('OWNER', 'MANAGER', 'MEMBER')),
                         -- 채팅방 내 역할 (방장, 매니저, 일반)

    profile_image_url    VARCHAR2(255),       -- 채팅방 내 사용자별 프로필 이미지

    joined_at            DATE DEFAULT SYSDATE, -- 채팅방 입장 시각
    left_at              DATE,                -- 채팅방 퇴장 시각 (nullable)
    is_active            CHAR(1) DEFAULT 'Y' 
                         CHECK (is_active IN ('Y', 'N')),
                         -- 채팅방 접속 여부 (실시간 목록 판단용)

    is_kicked            CHAR(1) DEFAULT 'N' 
                         CHECK (is_kicked IN ('Y', 'N')), -- 강제 퇴장 여부
    kicked_at            DATE,                 -- 강제 퇴장 시각 (nullable)

    last_read_message_id NUMBER,              -- 마지막 읽은 메시지 ID (읽음 처리, 알림 뱃지용)

    CONSTRAINT fk_cu_chatroom FOREIGN KEY (chatroom_id)
        REFERENCES chatroom(chatroom_id),

    CONSTRAINT fk_cu_member FOREIGN KEY (member_id)
        REFERENCES members(member_id)
);


```

## 공지사항 엔티티 설계
하나의 채팅방(Chatroom)에는 공지사항 이력이 여러 개 저장됨 1:N 관계
공지사항 읽음 여부를 사용자 단위로 기록하지 않음 -> 추후에ㅔ 필요할 경우 추가할 예정임.
공지사항이 수정되면 모든 채팅방 참여자에게 알림 1회 발송 , 읽었는지 여부 기록 X , 알림 발송 시점에서만 처리 
공지사항 배경화면은 추후에 필요하면 추가

```sql
CREATE TABLE Chatroom_Notice_History (
    notice_id      NUMBER PRIMARY KEY, --고유 공지
    chatroom_id    NUMBER NOT NULL, -- 소속 채팅방 ID 

    content        VARCHAR2(100 CHAR) CHECK (LENGTH(content) <= 100),         -- 공지사항: 한글 기준 100자
    description    VARCHAR2(200 CHAR) CHECK (LENGTH(description) <= 200),     -- 설명글: 한글 기준 200자

    created_at     DATE DEFAULT SYSDATE, -- 생성 일시

    CONSTRAINT fk_notice_chatroom 
        FOREIGN KEY (chatroom_id) REFERENCES Chatroom(chatroom_id)
);


```

 특징 요약
각 공지사항은 하나의 채팅방에 소속됨 (1:N)

content와 description은 둘 다 수정될 수 있으며, 수정 시 새로운 공지 레코드 추가

채팅방의 최신 공지는 Chatroom.latest_notice_id 컬럼으로 연결됨

읽음 여부는 저장하지 않음 → 알림은 공지 수정 시 서버에서 1회만 전송


### 인기 채팅방
우리 카테고리중에 인기를 클릭하면 현재 최신 인기 순서가 제일 높은 채팅방부터 내림차순으로 보여줄려고함. 인기 채팅방 기준은 채팅방 내부에 좋아요/즐겨찾기 한 사용자의 수를 기준으로 할 것이다.
중복 방지를 위해 UNIQUE 제약, , 인기 카테고리 기준에서는 좋아요 수 기준으로 할려고함.

✅ 1명의 사용자는 하나의 채팅방에 대해 최대 1개의 좋아요만 가능하며, 여러 채팅방에 각각 좋아요를 누를 수 있음.
좋아요를 취소해도 DB에 기록은 남고, is_active = 'N'으로 상태만 비활성화됨
인기 채팅방 목록을 기반으로 신규 유저 유입을 유도


 Chatroom_Like 테이블 설계하고 <br>
 ```sql
CREATE TABLE chatroom_like (
    like_id        NUMBER PRIMARY KEY,                          -- 고유 좋아요 ID (시퀀스로 관리)
    chatroom_id    NUMBER NOT NULL,                             -- 좋아요가 눌린 채팅방 ID
    member_id      NUMBER NOT NULL,                             -- 좋아요를 누른 사용자 ID

    is_active      CHAR(1) DEFAULT 'Y' 
                   CHECK (is_active IN ('Y', 'N')),             -- 좋아요 상태 (Y: 눌림, N: 취소됨)

    liked_at       DATE DEFAULT SYSDATE,                        -- 처음 좋아요를 누른 시각
    updated_at     DATE,                                        -- 좋아요 상태가 마지막으로 변경된 시각

    CONSTRAINT uq_like UNIQUE (chatroom_id, member_id),         -- 사용자당 채팅방당 좋아요는 1회만 가능
    CONSTRAINT fk_like_chatroom FOREIGN KEY (chatroom_id) 
        REFERENCES chatroom(chatroom_id),                       -- 채팅방 외래키
    CONSTRAINT fk_like_member FOREIGN KEY (member_id) 
        REFERENCES members(member_id)                           -- 사용자 외래키
);


```

이렇게 만들려고함. 채팅방에 대해 좋아요 한 번만 가능 -> 복합 PK로 중복 방지 </br>


### 강퇴 시간 
단순히 "강퇴당했는가(Y/N)"만 저장하면, 언제 강퇴됐는지는 알 수 없음 </br>
 “강퇴된 사용자는 해당 방에 재입장 불가”  -> 강퇴 시점을 저장하면, 그 이후 입장을 막거나 로그로 확인 가능
```sql
is_kicked      CHAR(1) DEFAULT 'N' CHECK (is_kicked IN ('Y', 'N')),
kicked_at      DATE
```


### ✅ 메시지(Message) 테이블

하나의 채팅방에는 여러 사용자가 참여할 수 있음. 이 메시지 테이블에는 채팅방 안에서 실제 주고받는 채팅 메시지를 저장 </br>
메시지 테이블에서 수십만~수백만 건 이상이 되는 테이블을 어떻게 관리할지 생각을해봐야한다.
인덱스, 파티셔닝 전략으로 고민하는게 좋을듯 

전체적인 정리 
"한 명의 회원은 여러 개의 채팅방에 참여할 수 있고, 각 채팅방에서 여러 개의 메시지를 보낼 수 있다."

2. 메시지는 "어떤 방에서", "누가", "무엇을 말했는가"만 기록하면 된다
chatroom_id: 어떤 방에서

member_id: 누가

message_content: 무엇을

👉 이 3가지 정보면 메시지


```SQL

CREATE TABLE chat_message (
    message_id       NUMBER PRIMARY KEY,
    chatroom_id      NUMBER NOT NULL,
    member_id        NUMBER NOT NULL,
    
    message_type     VARCHAR2(20 CHAR) DEFAULT 'TEXT'
                     CHECK (message_type IN ('TEXT', 'IMAGE', 'VIDEO', 'LOCATION', 'SYSTEM')),

    message_content  CLOB,                     -- 텍스트 메시지 / 시스템 메시지 / 위치 설명글
    file_url         VARCHAR2(255),            -- 첨부파일 경로 (이미지, 영상 등)
    file_type        VARCHAR2(50),             -- MIME 타입 (image/png 등)

    latitude         NUMBER(9,6),              -- 위치 위도
    longitude        NUMBER(9,6),              -- 위치 경도
    location_name    VARCHAR2(100),            -- 장소 이름 (예: 강릉 초당 순두부 거리)

    sent_at          DATE DEFAULT SYSDATE,

    CONSTRAINT fk_msg_chatroom FOREIGN KEY (chatroom_id) REFERENCES chatroom(chatroom_id),
    CONSTRAINT fk_msg_member FOREIGN KEY (member_id) REFERENCES members(member_id)
);


```



------------------------------
✅ 그럼 chatroom_user_id는 언제 쓰냐?
쓰임새	예시
실시간 참여 여부 판단	현재 채팅방 유저 목록 표시
역할 기반 권한 체크	강퇴, 매니저 위임 등
채팅방 프로필 추적	방마다 다른 프로필 이미지 설정 시 표시용


### 해시태그 테이블

"채팅방 생성자가 여러 해시태그를 등록할 수 있고, 해시태그 하나는 여러 채팅방에서 사용될 수 있다"

🔹 하나의 채팅방 → 여러 해시태그 가능 (1:N)
🔹 하나의 해시태그 → 여러 채팅방에서 사용 가능 (1:N)

=> 즉, 채팅방과 해시태그는 **N:M (다대다)** 관계!

요구사항 분석을 기반으로 하나의 채팅방은 최대 5개의 해시태그를 가짐
하나의 해시태그는 여러 채팅방에서 공유될 수 있음.
✅ 대소문자 구분 없이 검색 (모두 소문자로 변환해 저장/검색)


```sql
CREATE TABLE hashtag (
    hashtag_id   NUMBER PRIMARY KEY, -- 해시태그 고유 ID
    tag          VARCHAR2(30) UNIQUE NOT NULL -- 해시태그 텍스트 
);
```

```sql
CREATE TABLE chatroom_hashtag (
    chatroom_id   NUMBER NOT NULL,
    hashtag_id    NUMBER NOT NULL,

    CONSTRAINT pk_chatroom_hashtag PRIMARY KEY (chatroom_id, hashtag_id),
    CONSTRAINT fk_ch_hashtag FOREIGN KEY (hashtag_id) REFERENCES hashtag(hashtag_id),
    CONSTRAINT fk_ch_chatroom FOREIGN KEY (chatroom_id) REFERENCES chatroom(chatroom_id)
);
```


