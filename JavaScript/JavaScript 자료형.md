## JavaScript 자료형
## 1. number 
<p> -숫자형(정수, 실수)</p>
예제: let num = 10; <br>
자바스크립트에서는 정수와 실수를 구분하지 않고 모두 <b>number</b> 타입으로 처리한다.
<br>

## 2. string
<p> -문자 or 문자열</p>
예제: let str = "Hello";<br>
문자열은 작은따옴표('), 큰따옴표("), 백틱(`)을 사용하여 표현할 수 있다. 차이점없음 선호하는거 사용
<br>

## 3. boolean
<p> -논리형</p>
예제: let isTrue = true; <br>
true 또는 false 값을 가진다. 조건문에서 많이 사용함.
<br>

## 4. object
<p> -객체형 <br>-자바스크립트에는 클래스가 없다.(ES6 > 클래스 추가) 
<br>-객체 지향 언어(X) > 객체 기반 언어(O)</p>

## 5. 기타(상수)
  a. null<br>
  b. undefined(값이 할당되지 않음)<br>
  c. NaN(not a number)

## 변수,상수

자바스크립트에서 변수를 선언하는 방식은 <b>var, let, const 3가지 방식</b>  <br>

<b>var(과거 방식)</b>: 재할당, 재선언 가능<br>
```javascript
var name = "Alice";
console.log(name); // "Alice"

var name = "Bob";  // 재선언 가능
console.log(name); // "Bob"
```

<b>let(ES6부터 등장,권장)</b>: 재할당 o , 재선언 불가능<br>
```javascript
let city = "Seoul";
console.log(city); // "Seoul"

city = "Busan";  // 재할당 가능
console.log(city); // "Busan
```

<b>const(상수)</b>: 재할당 불가능, 재선언 불가능 <br>
```javascript
const PI = 3.14;
console.log(PI); // 3.14
// PI = 3.1415;  // ❌ 에러 발생 (재할당 불가)

// const PI = 3.1415;  // ❌ 에러 발생 (재선언 불가)
```

값을 변경해야 한다면 let 사용

값을 변경할 필요가 없다면 const 사용

var 와 let 중에 변수 선언시에 let 을 사용하자 이유 예시로 var test1 = "hello" 로 정의하고,
정의되어있다는 사실을 인식하지 못하고 다시 재정의하면 문제가 발생할 수 있다. 그래서 var 선언에 대한
개선을 반영한 let이 현재 변수 선언에서 선호되고 있다.

또한 var는 블록을 무시하고 함수 전체에서 접근 가능하지만, let은 선언된 블록 내에서만 사용됨.
  
