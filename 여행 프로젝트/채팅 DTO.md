## 채팅 DTO

✅ 어떤 DTO를 먼저 만들어야 하나?
채팅 메시지 전송/조회용 DTO

ChatMessageRequestDTO: 메시지 전송 요청용

ChatMessageResponseDTO: 메시지 응답용

멘션 처리용 DTO

MentionUserDTO 또는 ChatMessageMentionDTO

읽음 처리용 DTO

ChatMessageReadDTO: 누가 언제 읽었는지 정보

(추가적으로)

ChatRoomInfoDTO, ChatroomLikeCountDTO, ChatroomNoticeDTO 등도 필요


✅ 4. 설계 팁
DTO는 엔티티와 1:1로 대응하지 않아도 됩니다.

화면에 보여줘야 하는 정보가 무엇인지 먼저 정의하고, 그것에 맞게 DTO를 구성하세요.

@Builder, @Getter, @NoArgsConstructor 등을 Lombok으로 설정해두면 편합니다.

필요시 중첩 구조 (nested DTO) 로도 표현 가능합니다.

요청용(Request) 과 응답용(Response) 을 명확하게 나누세요.



## 채팅방 DTO

✅ 정리: 채팅방 생성 기능 요구사항
항목	필수 여부	비고
채팅방 제목 (title)	✅ 필수	

썸네일 이미지 (thumbnailImage)	❌ 선택	파일 업로드

공지사항 내용 (noticeContent)	❌ 선택 공지 등록용

설명글 (description)	❌ 선택	

해시태그 리스트 (hashtags)	❌ 선택	여러 개 가능



```java
package com.test.foodtrip.domain.chat.dto;

import java.util.List;

import org.springframework.web.multipart.MultipartFile;

import jakarta.validation.constraints.NotBlank;
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Getter;
import lombok.NoArgsConstructor;

@Getter
@NoArgsConstructor
@AllArgsConstructor
@Builder
// 사용자가 채팅방 입력용 DTO (제목, 첨부파일, 공지사항, 설명, 해시태그) 
public class ChatRoomCreateRequestDto {
    
    @NotBlank(message = "채팅방 제목은 필수입니다.")
    private String title;

    private MultipartFile thumbnailImage; // 첨부파일

    private String noticeContent;         // 최초 공지사항 (선택)

    private String description;           // 설명글 (선택)

    private List<String> hashtags;        // 해시태그 리스트 (선택)
}
```

만약, @NotBlank 이어야하는 값이 @NotNull 이 설정되어 공백이 들어오게되면 큰 문제가 발생할 수 있기 때문입니다.

중간에 DTO 를 사용해야하는 이유에 대해서 설명을 드렸습니다.

테스트를 추가할 때도 각 DTO 를 분리하게 되면 각각의 request 에 따라 테스트 코드를 추가해줄 수 있기 때문에 요청을 모두 검증할 수 있어, 테스트 코드에 대한 커버리지가 높아질 수 있습니다.

채팅방 @NotBlank 

@NotBlank
@NotBlank 는 null 과 "" 과 " " 모두 허용하지 않습니다.

