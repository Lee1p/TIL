## 개발 유형 테스트 (개발 분야 선택)

이제 사용자가 개발 경험이 있는지 여부를 선택하는 코딩 경험 질문 페이지 예/아니오 </br>

세샨 기반으로 접근을 제어하였다.

사용자의 세션 정보(userSeq)를 통해 로그인된 사용자만 접근할 수 있도록 처리

팀원 UserDAO에서 이제 우리 DB값 userSeq 존재 여부로 판단, 로그인하지 않은  사용자는 로그인 페이지로 리다이렉트
```java
HttpSession session = req.getSession();
if (session.getAttribute("userSeq") == null) {
    resp.sendRedirect("/devmap/user/login.do");
    return;
}

```


```java
int userSeq = (int) session.getAttribute("userSeq");
UserDTO user = userDAO.selectUser(userSeq);
req.setAttribute("user", user);

```

그 다음에 세션에서 가져온 user시퀀스를 이용해 , 조회된 사용자 정보를 JSP에서 사용할 수 있도록 request 객체에 담아 전달

```html
<p class="greeting">안녕하세요. ${user.name}님 진심으로 반갑습니다.</p>
<p class="question">
    <b>Q. "${user.name}"님은 코딩 경험이 있으십니까?</b>
</p>

```

JSP 에서 사용자 이름을 활용해서 인삿말과 질문 문장을 동적으로 구성하고 전달받은 사용자 정보를 표시한다.


```html
<form action="/devtest/CodingQuestion.do" method="POST">
    <button type="submit" name="experience" value="yes">예</button>
    <button type="submit" name="experience" value="no">아니요</button>
</form>
```
예/아니요 버튼을 누르면 experience=yes 또는 experience=no 값이 POST로 전송하고

doPost()에서 이 값을 받아서 다음 경로로 리다이렉트 처리하였다.


```java
if ("yes".equals(experience)) {
    resp.sendRedirect(req.getContextPath() + "/devtest/DevFieldSelection.do");
} else {
    resp.sendRedirect(req.getContextPath() + "/devtest/DevFieldSelectionNoExp.do");
}

```

사용자가 예/아니오를 선택하면, 그 값에 따라 다음 페이지로 이동하게하였다.

"예" 코딩 경험이 있는 사용자 , "아니오" 코딩 경험이 없는 사용자로 로직을 처리하였다.


★일단 우리 요구사항은 로그인한 사용자만 접근 가능하도록 해야 하기때문에 세션을 기반으로 접근을 제어하였다.
사용자 맞춤 인삿말을 출력하려면 로그인한 사용자의 정보를 불러와야 하기 때문에, 로그인 여부 체크는 필수였다.

 나중에 사용자 응답(예/아니오)을 DB에 저장해야 할 수도 있다고 생각했는데, 현재는 단순 흐름 제어만 하므로 보류했다.
→ 이후 테스트 결과 저장 로직이 생긴다면 이 부분도 수정이 필요함.
