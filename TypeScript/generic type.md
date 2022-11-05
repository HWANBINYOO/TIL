# 제네릭
여러 가지 타입에서 동작하는 컴포넌트를 생성하는데 사용한다


## 제네릭을 사용하는 이유
ex)

여기 text라는 파라미터에 어떤 값을 넘겨 받아도  그대로 text를 반환하는 함수가있다
```js
function getText(text) {
  return text;
}

getText('hi'); // 'hi'
getText(10); // 10
```

제네릭을 사용하면 함수를 호출할 때 아래와 같이 함수 안에서 사용할 타입을 넘겨줄 수 있다

함수의 인자와 반환 값에 모두 T 라는 타입을 추가했다
```js

function getText<T>(text: T): T {
  return text;
}

// 이렇게 선언한 함수는 아래와 같이 2가지 방법으로 호출할 수 있다
1
getText<string>('hi');
getText<number>(10);
2
getText('hi');
getText(10);

```

## 제네릭 인터페이스

```js
interface GenericLogTextFn {
  <T>(text: T): T;
}
function logText<T>(text: T): T {
  return text;
}
let myString: GenericLogTextFn = logText; // Okay

// 인터페이스에 인자 타입을 강조
interface GenericLogTextFn<T> {
  (text: T): T;
}
function logText<T>(text: T): T {
  return text;
}
let myString: GenericLogTextFn<string> = logText;

```








