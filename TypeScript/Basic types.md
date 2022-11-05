# 기본 타입

## String , Number , Boolean
```js
let str: string = 'hi';
let num: number = 10;
let isLoggedIn: boolean = false;


```

## Object
타입을 object로 정의하면, any 타입처럼 모든 타입의 값을 할당할 수 있다
```js
const MyStatus: object = { name: 'types', age: 2022 };
```

## Array
```js
let arr: number[] = [1,2,3];
let arr: Array<number> = [1,2,3];
```

## Tuple
튜플은 배열의 길이가 고정되고 각 요소의 타입이 지정되어 있는 배열 형식을 의믜한다
```js
let arr: [string, number] = ['hi', 10];
```

## Enum
특정 값(상수)들의 집합을 의미한다

### 숫자 열거형
```js
enum MyStatus {
  sleep,
  study,
  play,
  work,
}
console.log(MyStatus.study) //1
```
### 문자 열거형 
```js
enum MyStatus {
    sleep = '자는중';
    study = '공부하는중';
    play = '노는중';
    work = '일하는중';
};
console.log(MyStatus.study) // 공부하는중
```
- 객체와의 차이
  - object 는 코드내에서 새로운 속성을 자유롭게 추가할 수 있지만, enum 은 선언할때 이후에 변경할 수 없다
  - object 의 속성값은 모든 타입이 올 수 있지만, enum 의 속성값으로는 문자열 혹은 숫자만 허용된다


## Any
모든 타입에 대해서 허용한다는 의미를 갖고 있다

## Void
변수에는 undefined와 null만 할당하고, 함수에는 반환 값을 설정할 수 없는 타입이다
```js
function 함수(): void {
  console.log('보이드');
}
```

## Null and Undefined

## Never
값을 리턴하지 않을 때 사용한다.
```js
// 이 함수는 절대 함수의 끝까지 실행되지 않는다는 의미
function neverEnd(): never {
  while (true) {

  }
}
```






