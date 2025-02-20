## CSS 상속

css는 부모 요소에 지정한 속성값을 자식 요소에게도 상속해서 적용한다.

예시: 
```css
<style>
        #parent {
            border: 5px solid black;
            background-color: gold;
            color: blue;
            width: 200px;
            font-weight: bold;
        }
        #child {
            border: 5px solid cornflowerblue;
            background-color: transparent;
        }

<div id="parent">
        부모의 내용물입니다.
        <div id="child">자식의 내용물입니다.</div>
        부모의 내용물입니다.
     </div>
```

<p>여기서 상속되는 부분은 <b> 텍스트와 관련된 속성만 상속된다. <br>
</b> 즉, 폰트 컬러, 사이즈, 폰트 종류 등등..</p>
나머지 속성은 상속이 안된다. <br> 그러나, 상속이 되지 않는 프로퍼티라고해서 꼭 상속을 받을 수 없는 것은 아니다.
<br>inherit를 쓰면 상속 받기 가능. 
