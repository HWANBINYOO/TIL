# Javascript 배열함수

## forEach
배열의 `모든 요소 반복`하는 메서드이다

모든 원소들을 모두 출력해야 할떄 for 문을 대체 시킬 수 있다
```js
const a = [1,2,3,4,5];

for (let i = 0; i < a .length; i++) {
  console.log(a[i]);
}

a.forEach(i => console.log(i));
```

## map
배열의 `모든 요소를 이용하여 새로운 배열을 반환`하는 메서드이다
```js
let a = [1, 2, 3, 4, 5];
let newNumbers = a.map((number) =>   console.log(number));
```

## filter
배열에서 `특정 조건을 만족하는 값`들만 따로 추출하여 새로운 배열을 반환하는 배서드이다
```js
const a = [1,2,3,4,5];
 
const b = a.filter((s) => { s%2 === 0; })
console.log(b); // [2, 4]
```

## reduce
배열의 각 요소에 대해 리듀서(reducer) 함수를 실행하고 `하나의 결과값을 반환`한다
```js
배열.reduce((누적값, 현잿값, 인덱스, 요소) => {
  return 결과;
}, 초깃값);
```
ex)
```
const a = [1,2,3,4,5];
let sum = a.reduce((accumulator, current) => accumulator + current, 0);
```

## splice
해당 구간 인덱스의 요소를 다른 요소로 바꾸거나 삭제해서 `원본 배열 자체를 수정`한다
 ```js
const a = [1,2,3,4,5];
  
const b = a.splice(0,2);
  
console.log(b); [1,2]
console.log(a); [3,4,5]
```

## slice
slice 메서드는 splice와는 다르게 `해당 구간 인덱스만을 가지는 새로운 배열을 반환`한다

만약 인자가 음수 값을 가질 경우 배열의 마지막부터 계산한다
```js
const a = [1,2,3,4,5];
  
const b = a.slice(1,3);
  
console.log(b); // [2,3]
console.log(a); // [1,2,3,4,5]
```

## shift pop unshift push
이 메서드들은 배열의 `제일 앞 인덱스에 추가하거나 삭제`하고 `마지막 인덱스에 추가하거나 삭제`한다
```js
const a = [1,2,3,4,5];

// a.shift();     // [2,3,4,5]
// a.pop();       // [1,2,3,4]
// a.unshift(10); // [10,1,2,3,4,5]
// a.push(11);    // [1,2,3,4,5,11]
```
## indexOf
배열의 요소 값을 indexOf 를 쓰면 해당 값이 `몇번째 인덱스 인지` 알려준다
```js
const a = ['호랑이', '사자', '고양이', '멍멍이'];
console.log(a.indexOf('고양이')); // 2
```

## findIndex
배열에서 `조건에 맞는 값이 몇번째 인덱스 인지` 알려준다
```js
const a = [
   { name : '호랑이' },
   { name : '사자' },
   { name : '고양이' },
   { name : '멍멍이' }
]
console.log(a.findIndex(ary => ary.name === '고양이')); // 2
```

## find
findIndex 메서드와 매우 유사하지만 차이점은 `findIndex는 인덱스를 리턴하지만 find는 값을 리턴`한다
```js
const a = [
  { name : '호랑이' , grade: 'A' },
  { name : '사자'   , grade: 'B' },
  { name : '고양이' , grade: 'C'},
  { name : '멍멍이' , grade: 'D'}
]
console.log(a.find(ary => ary.name === '고양이')); // {name: '고양이' , grade:'C' }
```

## join
배열을 `하나의 문자열로` 만든다
```js
var test = ['a', 'b', 'c'];
var result1 = test.join(); // a,b,c
var result2 = test.join('');// abc
```

## sort
`배열의 요소들을 정리`해준다

### 숫자정렬

```js
let numbers = [1, 10, 2, 20, 3, 30];
```

- 오름차순

```js
numbers.sort((next, prev) => next - prev);[1,2,3,10,20,30]
```

- 내림차순

```js
numbers.sort((next, prev) => prev - next); //[30,20,10,3,2,1]
```
### 문자정렬

```js
let strArray = ["BA", "BB","AA", "AB", "CB", "CA"];
```

- 오름차순
 ```js
strArray.sort();
```
- 내림차순
```js
strArray.sort(function compare(a, b) {
  return a == b ? 0 : a > b ? -1 : 1;
});
```

## some 
콜백함수를 받아 `배열의 원소 중에 하나라도 해당 함수를 만족`한다면 그 시점에서 `배열의 순환을 끝내고`바로 true를 반환한다

```js
const arr = [1,2,3,4,5];
console.log(arr.some((value) => value > 2)) // true
console.log(arr.some((value) => value > 6)) // false
```

## every
some 과 반대로 `배열의 원소 중에 하나라도 만족하지 않는 원소`가 있다면 그 시점에서 `배열의 순환을 끝내고`바로 false를 반환한다

```js
const arr = [1,2,3,4,5];
console.log(arr.every((value) => value > 3)) // false
```

