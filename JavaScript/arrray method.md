# Javascript 배열함수

## forEach
배열의 모든 요소 반복하는 메서드이다

모든 원소들을 모두 출력해야 할떄 for 문을 대체 시킬 수 있다
```js
const a = [1,2,3,4,5];

for (let i = 0; i < a .length; i++) {
  console.log(a[i]);
}

a.forEach(i => console.log(i));
```

## map
배열의 모든 요소를 이용하여 새로운 배열을 반환하는 메서드이다
```js
let a = [1, 2, 3, 4, 5];
let newNumbers = a.map((number) =>   console.log(number));
```

## filter
배열에서 특정 조건을 만족하는 값들만 따로 추출하여 새로운 배열을 반환하는 배서드이다
```js
const a = [1,2,3,4,5];
 
const b = a.filter((s) => { s%2 === 0; })
console.log(b); // [2, 4]
```

## reduce
배열의 각 요소에 대해 리듀서(reducer) 함수를 실행하고 하나의 결과값을 반환한다
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
해당 구간 인덱스의 요소를 다른 요소로 바꾸거나 삭제하고 새로운 배열을 반환한다
 ```js
const a = [1,2,3,4,5];
  
const b = a.splice(0,2);
  
console.log(b); [1,2]
console.log(a); [3,4,5]
```

## slice
slice 메서드는 splice와는 다르게 해당 구간 인덱스만을 가지는 새로운 배열을 반환한다

만약 인자가 음수 값을 가질 경우 배열의 마지막부터 계산한다
```js
const a = [1,2,3,4,5];
  
const b = a.slice(1,3);
  
console.log(b); // [2,3]
console.log(a); // [1,2,3,4,5]
```

## shift pop unshift push
이 메서드들은 배열의 제일 앞 인덱스에 추가하거나 삭제하고 마지막 인덱스에 추가하거나 삭제한다
```js
const a = [1,2,3,4,5];

// a.shift();     // [2,3,4,5]
// a.pop();       // [1,2,3,4]
// a.unshift(10); // [10,1,2,3,4,5]
// a.push(11);    // [1,2,3,4,5,11]
```
## indexOf
배열의 요소 값을 indexOf 를 쓰면 해당 값이 몇번째 인덱스 인지 알려준다
```js
const a = ['호랑이', '사자', '고양이', '멍멍이'];
console.log(a.indexOf('고양이')); // 2
```

## findIndex
배열에서 조건에 맞는 값이 몇번째 인덱스 인지 알려준다
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
findIndex 메서드와 매우 유사하지만 차이점은 findIndex는 인덱스를 리턴하지만 find는 값을 리턴한다
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
배열을 하나의 문자열로 만든다
```js
var test = ['a', 'b', 'c'];
var result1 = test.join(); // a,b,c
var result2 = test.join('');// abc
```
