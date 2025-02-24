### JavaScript Function

    - "함수는 1급 객체이다."
            - 함수를 객체처럼 취급한다. > 값으로 사용할 수 있다.

            1. 함수를 변수나 데이터 구조에 담을 수 있다.(저장)
            2. 함수를 매개변수로 전달할 수 있다.
            3. 함수를 반환값으로 사용할 수 있다.

            *** 값(변수,상수)이 들어가는 모든 위에 함수가 들어갈 수 있다. 
```javascript
 1. 함수 선언문
       function m1() {
           alert('m1');
       }
       m1();

  2. 함수 표현식(리터럴)
    function 함수명() {
      alert('익명함수');
}) (); // 즉시 호출


```

### BOM 과 DOM 

```

            1. BOM, Browser Object Model
                - 트리 구조
                - 고정된 트리 + 일부 태그 조작
                - 기능 부족


            2. DOM, Document Object Model
                - 트리 구조
                - 모든 태그 조작
                - 기능 풍부
            
            DOM
            - BOM > name 식별자만 사용 가능
            - DOM > name, id, class 등.. > 태그 검색 범위 확장
            - CSS 조작 가능
            - 콘텐츠 조작 가능
            - DOM Levle 1 > DOM Levle 2 > DOM Level 3 

            BOM의 최상위 객체 > window
            DOM의 최상위 객체 > document

            여태 자바스크립트 작업?
            1. 태그 검색

            DOM에서 제공하는 태그 검색 도구(함수)
            1. id 검색 > document.getElementById('id')
            2. class 검색 > document.getElementsByClassName('class')
            3. name 검색 > document.getElemnetByName('name')
            4. 태그명 검색 > document.getElementsByTagName('tag');
            ----------------------------------------------------------
            5. CSS 선택자 검색
                - ES6 추가(2014년) > 이전에는 각종 라이브러리 사용
                - document.querySelector('선택자') > 단수 반환 
                - document.querySelectorAll('선택자') > 복수 반환
```

### Content

```
 BOM or DOM > 태그 조작
            1. 태그 검색(BOM, DOM)
            2. 속성 조작(BOM, DOM)
            3. 콘텐츠 조작(BOM(X), DOM(O))
            4. 이벤트 조작(BOM, DOM)

            Content
            - 시작 태그와 끝 태그 사이의 내용물(PCDATA, Element)조작
            1. innerText
                - 시작 태그와 끝 태그 사이의 내용을 읽기/쓰기
                - 문자열로 취급(태그 인식X)
                - 비표준(MS)

            2. innerHTML
                읽기: 요소의 HTML 내용(자식 요소 포함)을 가져오기
                쓰기: 요소의 HTML 내용을 변경
            3. textContent
                - 시작 태그와 끝 태그 사이의 내용을 읽기/쓰기
                - 문자열로 취급(태그 인식X)
                - 표준

            ---------------------------------------------------------
            4. outerText
            5. outerHTML
```

