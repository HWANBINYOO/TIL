## Array.from

객체나 이터러블한 객체를 배열로 만들어주는 메소드이다

ex)

```js
1;
Array.from("Tei");
//["T", "e", "i"]

2;
Array.from([1, 2, 3], (x) => x + x);
//[2, 4, 6]

3; //1부터 15까지의 수를 원소로 갖는 배열생성할때
const arr = Array.from(Array(31), (_, index) => index + 1);
```

### 자바스크립트 배열의 length

```js
Array.from(
  { length: 20 }, // 유사배열
  () => Array(5).fill(1) // 각각의 배열에 적용할 함수
); // [1,1,1,1,1]
```

### 유사 배열 객체를 배열로 만들떄

```js
Array.from({ 0: "찬민", 1: "희진", 2: "태인", length: 3 })); // [ '찬민', '희진', '태인' ]
```
