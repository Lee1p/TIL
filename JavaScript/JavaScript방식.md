## JavaScript 방식

<p> <b>1. 이벤트 핸들러(Event Handler) </b>b> == 이벤트<br> - 대부분의 태그 > onXXX 속성 제공 <br> - 태그에 직접 자바스크립트 작성
</p>


HTML 태그의 속성에 직접 이벤트 핸들러를 작성하는 방식
```javascript
<button onclick="alert('버튼이 클릭되었습니다!')">클릭하세요</button>
```

<p> <b>2.임베디드 방식 </b></p> <br> - <script> 태그 
<p>HTML 문서 안에 <script> 태그를 사용하여 직접 JavaScript 코드를 작성하는 방식</p>

```javascript
    <h1>안녕하세요!</h1>
    <button onclick="showMessage()">클릭하세요</button>

    <script>
        function showMessage() {
            alert("버튼이 클릭되었습니다!");
        }
    </script>
```

<p> <b>3. 외부 방식 </b </p>
<p>JavaScript 코드를 별도의 .js 파일로 저장하고, <script> 태그를 사용해 HTML 파일에서 불러오는 방식</p>

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>외부 자바스크립트</title>
    <script src="script.js"></script>
</head>
<body>

    <h1>안녕하세요!</h1>
    <button onclick="showMessage()">클릭하세요</button>

</body>
</html>
```

<p> 외부 자바스크립트 파일 (script.js)</p>

```javascript
function showMessage() {
    alert("버튼이 클릭되었습니다!");
}
```
