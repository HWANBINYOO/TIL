# 타입스크립트란

타입스크립트는 자바스크립트에 타입을 부여한 언어이다

자바스크립트의 확장된 언어라고 볼 수 있다

## 왜 타입스크립트를 써야할까

### 에러의 사전 방지
TypeScript는 정적 타입을 지원하므로 컴파일 단계에서 오류를 포착할 수 있는 장점이 있다


아래와 같이 의도하지 않은 코드의 동작을 예방할수 있다
```js
// math.js
function sum(a, b) {
  return a + b;
}
sum(10, 20); // 30
sum('10', '20'); // 1020
```

```js
// math.ts
function sum(a: number, b: number) {
  return a + b;
}
sum('10', '20'); // Error: '10'은 number에 할당될 수 없습니다.
```
### 코드 자동 완성과 가이드

js 로 작성할시 total이라는 변수의 타입이 코드를 작성하는 시점에 number 라는 것을 자바스크립트가 인지하지 못하고있어서 미리보기가 안뜨게 된다
```js
// math.js
function sum(a, b) {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```
하지만 ts는 변수 total에 대한 타입이 지정되어 있기 때문에 VSCode에서 해당 타입에 대한 API를 미리 보기로 띄워줄 수 있다
```js
function sum(a: number, b: number): number {
  return a + b;
}
var total = sum(10, 20);
total.toLocaleString();
```
