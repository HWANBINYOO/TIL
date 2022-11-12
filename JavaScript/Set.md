# Set 객체

 중복을 제거한 값들의 집합이다
 
 ### Set 객체 선언
 ```js
 const set  = new Set();              // Set(0) {}
 const set1 = new Set([1, 2, 3, 3]); //Set(3) {1, 2, 3}
 const set2 = new Set('hello');      //Set(4) {"h", "e", "l", "o"}
 ```
 
 ## Set 객체 사용
 
 - 요소 추가: add
 - 요소 확인: has
 - 요소 제거: delete
 - 요소의 개수 반환: size
 - 모든 요소 제거: clear

```js
set.add(1).add(5)add("hi) ; // Set { 1, 5, 'hi' }
set.has('hi');      // true
set.delete('hi');   // Set { 1, 5 }
set.size;           // 2
set.clear();        // Set { }

```

ex)

배열에서 중복된 요소를 제거할떄

```js
// 배열의 중복 요소 제거
const uniq = array => array.filter((v, i, self) => self.indexOf(v) === i);
console.log(uniq([2, 1, 2, 3, 4, 3, 4])); // [2, 1, 3, 4]

// Set을 사용한 배열의 중복 요소 제거
const uniq = array => [...new Set(array)];
console.log(uniq([2, 1, 2, 3, 4, 3, 4])); // [2, 1, 3, 4]
```
