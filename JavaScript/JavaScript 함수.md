## JavaScript function 

⭐ JavaScript 에서는 자료형을 명시적으로 표현이 불가능하다.
ex) -number, string, boolean, object.. 


## 함수 선언

함수 선언은 호이스팅(hoisting)의 영향을 받기 때문에, 함수 선언은 코드의 어디서든 호출 가능

호이스팅이란, 함수가 코드의 어느 위치에서든 호출 될 수 있음을 의미한다. 예를들어 아래 test() 함수를
선언하기전에 test(); 를 먼저 선언하고 그 아래 함수를 작성해도 된다는 뜻이다.

함수 선언할때는 function 키워드와 함께 함수 이름 명시하여 정의

```javascript
function test() {
  console.log("Hello,Wolrd!");
}

test(); // "Hello, Wolrd!" 출력
```

## 변수의 영역

1. 전역 변수
2. 지역 변수

지역 변수 특징: 자바스크립트는 <b>"함수"</b>만 영역으로 인식한다.

num1 = 100; 이런식으로 var 를 제외하고도 선언할 수도있다. 단, 함수 안에 var,let 선언문없이 
사용할경우 지역변수가 아닌 전역변수가된다. <b>(권장하지않은방법)</b>

EX)

```javascript
function m1() {
            console.log(num1);
            var num2 = 200; //지역 변수. m1을 영역
            console.log(num2);
        }
  if (num1 > 0) {
            var num3 = 300; //지역 변수(X), 전역 변수(O)
            console.log(num3);
        }
if는 함수가 아니기때문에 지역 변수가 아니다.

```


### 형변환 함수

1. number parseInt(value)
  -value를 정수 형태를 가지는 number로 반환
2. number parseFloat(value)
  -value를 실수 형태를 가지는 number로 변환

EX)
```javascript
        var n1 = 3.14;
        console.log(parseInt(n1)); // 결과값 : 3 

        var n2 = '300';
        console.log(typeof n2); // string
        console.log(parseInt(n2), typeof parseInt(n2)); 결과값: 300, number 
```

### 자바스크립트 이벤트 

이벤트 적용하는 방법은 크게 세 가지가 있다. 
1. HTML 태그에서 직접 설정하는 방식 (인라인 방식) / 비추천

```javascript
<button onclick="alert('버튼이 클릭되었습니다!')">클릭</button>
```
2. 자바스크립트에서 onXXX 속성을 사용하는 방식(이벤트 핸들러 방식)

```javascript
<button id="myButton">클릭</button>

<script>
  document.getElementById("myButton").onclick = function() {
    alert("버튼이 클릭되었습니다!");
  };
</script>
```

3.  addEventListener() 메서드를 사용하는 방식 ✨추천

```javascript
<button id="myButton">클릭</button>

<script>
  document.getElementById("myButton").addEventListener("click", function() {
    alert("버튼이 클릭되었습니다!");
  });
</script>
```
