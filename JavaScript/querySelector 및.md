### 2월 25일 

querySelector 함수 : CSS 선택자를 사용하여 첫 번째 일치하는 요소를 반환 
querySelectorAll 함수 :  DOM 요소들을 선택하는 메소드, CSS 선택자와 일치하는 모든 요소를 반환 <br>

여기서 이제 같은 id 또는 class 일 경우 스크립트의 최상단 요소만 로직에 포함한다.<br>

<b>ex)</b>

```javascript
<div class="box" > test </div>
<div class="box" > test test </div>

let a = document.querySelector(".box");
console.log(a);

--> <div class="box" > test </div> 첫 번째 요소 반환

여기서 querySelectorAll 함수를 사용하면 모든 요소를 반환한다.

```

<br>
Document.querySelectorAll()는 요소를 배열형태로 받아오기 때문에 index를 이용하여 특정 요소를 선택하는 것이 가능
<br>
<br>
<br>




```javascript
 <table id="tbl1">

        <tr>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
        <tr>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
            <td></td>
        </tr>
</table>

<script>
 
        let list = document.querySelectorAll('#tbl1 td'); 

    

        let listLength = list.length;

        for (let i= 0; i < listLength; i++) {
            list[i].addEventListener("click", function(event) {
            event.target.innerHTML = '<img src="images/rect_icon01.png">';
            });
        }
        // event.target은 반드시 addEventlistner 내부에서만 사용 가능.
        // event.target을 사용하려면 event 객체가 존재해야함.
        

</script>


```

<br>
위에 코드는 테이블의 각 셀을 클릭하면, 셀 내부에 이미지를 삽입하는 기능을 구현한 예제 <br>

#tbl1 테이블 안의 모든 <td> 요소를 선택 (NodeList를 반환 배열과 유사) <br>

event.target : 이벤트가 발생한 특정 요소를 가리킴 , 동적 이벤트 처리 및 이벤트 위임에 유용하게 사용 <br>
예를들어 버튼을 생성하고 버튼을 클릭할 때마다, 이벤트를 적용하면 원하는 요소에 정확한 항목을 찾아서 사용 
