# 타입변환
개발자에 의해 의도적으로 값의 타입을 변환하는 것을 `명시적 타입 변환(Explicit coercion)`또는 `타입 캐스팅(Type casting)`이라 한다

개발자의 의도와는 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동 변환되기도 한다. 이를 `암묵적 타입 변환(Implicit coercion)` 또는 `타입 강제 변환(Type coercion)`이라고 한다

## 암묵적 타입 변환

### 문자열 타입으로 변환
문자열 연결 연산자 표현식을 평가하기 위해 문자열 연결 연산자의 피연산자 중에서 문자열 타입이 아닌 피연산자를 문자열 타입으로 암묵적 타입 변환한다
```js
1 + '2'   // "12"
0 + ''    // "0"
//위 예제의 + 연산자는 피연산자 중 하나 이상이 문자열이므로 문자열 연결 연산자로 동작한다
```

### 숫자 타입으로 변환
산술 연산자 표현식을 평가하기 위해 산술 연산자의 피연산자 중에서 숫자 타입이 아닌 피연산자를 숫자 타입으로 암묵적 타입 변환한다

피연산자를 숫자 타입으로 변환할 수 없는 경우는 산술 연산을 수행할 수 없으므로 NaN을 반환한다
```js
+'10'       // 10
+'string'   // NaN
+true       // 1
```

### 불리언 타입으로 변환
 제어문의 조건식을 평가 결과를 불리언 타입으로 암묵적 타입 변환한다
 
 
불리언 타입이 아닌 값을 Truthy 값(참으로 인식할 값) 또는 Falsy 값(거짓으로 인식할 값)으로 구분한다. 즉, Truthy 값은 true로, Falsy 값은 false로 변환된다

#### false 로 평가되는 Falsy값
- false , undefined , null , 0, -0 , NaN , ''(빈문자열)

## 명시적 타입 변환

### 문자열 타입으로 변환
1. String 생성자 함수를 new 연산자 없이 호출하는 방법
2. Object.prototype.toString 메소드를 사용하는 방법
3. 문자열 연결 연산자를 이용하는 방법
```js
console.log(String(1));       // "1"
console.log((1).toString());  // "1"
console.log(1 + '');          // "1"
```

### 숫자 타입으로 변환
1. Number 생성자 함수를 new 연산자 없이 호출하는 방법
2. parseInt, parseFloat 함수를 사용하는 방법(문자열만 변환 가능)
3. \+ 단항 연결 연산자를 이용하는 방법
4. \* 산술 연산자를 이용하는 방법
```js
console.log(Number('0'));     // 0
console.log(parseInt('0'));   // 0
console.log(+'0');            // 0
console.log('0' * 1);         // 0
```
### 불리언 타입으로 변환
1. Boolean 생성자 합수를 new 연산자 없이 호출하는 방법
2. !부정 논리 연산자를 두번 사용하는 방법
```js
console.log(Boolean('x'));  // true
console.log(Boolean(''));   // false
console.log(!!'x');         // true
console.log(!!'');          // false
```

## 단축평가
논리 연산을 수행할 때 만약 어느 한 쪽에서 이미 논리 연산의 결과가 확정되었다면 다음 연산을 이어가지 않고 즉시 평가를 완료하는 것이다

단축 평가는 아래의 규칙을 따른다
<table>
  <thead>
    <tr>
      <th style="text-align: center">단축 평가 표현식</th>
      <th style="text-align: left">평가 결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: center">true  || anything</td>
      <td style="text-align: left">true</td>
    </tr>
    <tr>
      <td style="text-align: center">false || anything</td>
      <td style="text-align: left">anything</td>
    </tr>
    <tr>
      <td style="text-align: center">true  &amp;&amp; anything</td>
      <td style="text-align: left">anything</td>
    </tr>
    <tr>
      <td style="text-align: center">false &amp;&amp; anything</td>
      <td style="text-align: left">false</td>
    </tr>
  </tbody>
</table>

### 사용예시

#### 객체가 null인지 확인하고 프로퍼티를 참조할 때
```js
let elem = null;

console.log(elem.value);         // TypeError: Cannot read property 'value' of null
console.log(elem && elem.value); // null
```
만약 객체가 null인 경우, 객체의 프로퍼티를 참조하면 타입 에러(TypeError)가 발생하는데 단축 평가를 사용하면 에러를 발생시키지 않는다

#### 함수의 인수(argument)를 초기화할 때
```js
function getStringLength(str) {
  str = str || '';
  return str.length;
}

getStringLength();     // 0
getStringLength('hi'); // 2
```
함수를 호출할 때 인수를 전달하지 않으면 매개변수는 undefined를 가질때 단축평가를 사용해 매개변수의 기본값을 설정하면 에러를 방지할 수 있다


