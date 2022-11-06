# 스프레드 연산자

기존 배열이나 객체의 전체 또는 일부를 다른 배열이나 객체로 빠르게 복사할 수 있다

함수 호출
```js
myFunction(...iterableObj);
```

배열 리터럴과 문자열
```js
[...iterableObj, '4', 'five', 6];
```

객체 리터럴
```js
let objClone = { ...obj };
```

ex)
```js
//배열
const fruitOne = ['apple', 'banana'];
const fruitTwo = ['grape', 'peach'];

const fruitAll = [...fruitOne, ...fruitTwo];
console.log(fruitAll); // ['apple', 'banana', 'grape', 'peach']

//객체
const user = { name: 'Kim', city: 'Seoul' };

user = { ...user, age: 28 };
console.log (user); // { name: 'Kim', city: 'Seoul', age: 28 }

```
