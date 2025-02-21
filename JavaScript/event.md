## 이벤트

### 마우스 이벤트(Mouse Events)
종류: 
click	요소를 클릭할 때 발생<br>
dblclick	요소를 더블 클릭할 때 발생<br>
mousedown	마우스 버튼을 눌렀을 때 발생<br>
mouseup	마우스 버튼을 뗐을 때 발생<br>
mousemove	마우스를 움직일 때 계속 발생<br>
mouseenter	마우스가 요소 위로 들어왔을 때 발생 <br>
mouseleave	마우스가 요소에서 벗어났을 때 발생 <br>
mouseover	마우스가 요소 위로 들어왔을 때 발생 <br>
mouseout	마우스가 요소에서 벗어났을 때 발생<br>
contextmenu	마우스 오른쪽 버튼을 클릭할 때 발생 (컨텍스트 메뉴)<br> 

click, dblclick, mouseenter, mosueover 등등 다양한 마우스 이벤트 존재

### EX)  예제: 마우스 올리기(mouseenter) & 벗어나기(mouseleave)
```javascript
<div id="box" style="width: 200px; height: 100px; background-color: lightblue; text-align: center; line-height: 100px;">
    마우스를 올려보세요!
</div>

<script>
    var box = document.getElementById("box");

    box.addEventListener("mouseenter", function() {
        box.style.backgroundColor = "orange";
        box.textContent = "마우스가 들어옴!";
    });

    box.addEventListener("mouseleave", function() {
        box.style.backgroundColor = "lightblue";
        box.textContent = "마우스를 올려보세요!";
    });
</script>

```
### 키보드 이벤트
종류:
keydown	키를 누를 때 발생 (길게 누르면 계속 반복 발생) <br>
keyup	키를 뗄 때 발생 <br>
keypress	키를 누를 때 발생 <br>

⭐ ketdown 이랑 keyup을 주로 사용 이제 <b> keypress </b> 는 더 이상 권장하지않음 ;

### EX) 예제: keyup으로 키 떼기 감지
(키를 눌렀다가 뗄 때 입력한 키가 화면에 표시됨)

```javascript
<input type="text" id="inputField" placeholder="여기에 입력하세요" />
<p id="result">입력한 키: </p>

<script>
    document.getElementById("inputField").addEventListener("keydown", function(event) {
        document.getElementById("result").textContent = "입력한 키: " + event.key;
    });
</script>

```
