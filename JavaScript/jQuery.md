### jQuery


```html

DOM 방식에서 

<div id="box1" class="box">상자1</div>
<div id="box2" class="box">상자2</div>
<div id="box3" class="box">상자3</div>

클래스 찾을때 querySelectorAll 이랑 getElementsBy
ClassName 으로 찾을수있는데 get은 좀 옛날방식 for each사용 안됨 .

getElementsByClassName = 유사 배열임 (순수배열X)

얘를 real배열로 만들수있는 방법이있음. 

 Array.from(document.getElementsByClassName('box')).forEach(box => {
                box.style.backgroundColor = 'gold';
            });

이렇게 Array를 사용하면 진짜 배열이되어서 foreach 사용가능

이제 제이쿼리 방식

jQuery('.box') <- 이렇게하면 아까 dom 방식이랑 같음 . 진짜 배열아님 유사배열

jQuery는 모든 기능을 함수로만 제공한다. 

jQuery는 모든 기능을 함수로만 제공한다. 
jQuery는 검색한 결과가 1개든, N개든 > 무조건 일괄적용

jQuery('.box').css('color','green');

여기서 제이쿼리의 큰 장점: 루프를 안돌려도됨 실제로는 루프를 돌리고있지만 .css 함수안에 감춰놓아서 사용자가 신경을안써도된다. 작업속도가 빨라지고 코드가 간결해짐 .


ex)

//태그 선택자
// jQuery('div').css('color', 'blue');

//아이디 선택자
// jQuery('#btn1').css('color', 'blue');

//클래스 선택자
// jQuery('.box').css('color','blue');

 //기타 등등
 jQuery('h1, div:nth-child(odd)').css('color','blue'); 

nth-child(odd)는 홀수에만 색상을 블루로 적용된다.

 <!-- ex02.html-->
    <h1>jQuery() 함수</h1>


    <input type="button" value="버튼1" id="btn1">
    <hr>
    <div id="box1" class="box">상자1</div>
    <div id="box2" class="box">상자2</div>
    <div id="box3" class="box">상자3</div>

근데 헷갈릴만한점 div:nth-child(odd) 는 홀수 적용인데 이 함수를 실행하면 2번째 상자에 blue가 된다. 

이유는 형제를 찾을때 h1 , input , hr 태그 부터 1,2,3 이렇게 색상을 입히니까 즉, 상자2가 5번째 홀수로 적용된다.

헷갈리지말자. 만약에 상자1,상자3에 색상을 입힐려면 이 div태그 바깥에 하나의 div태그로 또 감싸주면 의도한대로 된다.


 jQuery와 JavaScript DOM 방식의 객체 차이를 비교

jQuery 객체는 jQuery 메서드로만 조작할 수 있다 ***

제이쿼리 형변환


            //jQuery 객체 > (형변환) > BOM(DOM) 객체
            //c[0].style.color = 'white'; 

제이쿼리는 일단 모든 요소를 배열로 받는다. 그래서  형변환을 해서 원하는 태그에 속성을 정할려면 배열꺼내와서 속성지정 







```
