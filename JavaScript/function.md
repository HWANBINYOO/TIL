# 함수
어떤 목적을 가진 작업들을 수행하는 코드들이 모인 블럭이다

## 함수 정의

###  함수 선언문
```js
function 함수명(매개변수 목록) {
  return 함수몸체;
}
```


### 함수 표현식

자바스크립트의 함수는 일급 객체이므로 아래와 같은 특징이 있다.
1. 무명의 리터럴로 표현이 가능하다.(익명함수)
2. 변수나 자료 구조(객체, 배열…)에 저장할 수 있다.
3. 함수의 파라미터로 전달할 수 있다.
4. 반환값(return value)으로 사용할 수 있다.
```js
// 기명 함수 표현식
var foo = function multiply(a, b) {
  return a * b;
};
// 익명 함수 표현식
var bar = function(a, b) {
  return a * b;
};
console.log(foo(10, 5)); // 50
console.log(multiply(10, 5)); // Uncaught ReferenceError: multiply is not defined
```
