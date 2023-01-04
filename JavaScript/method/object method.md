## object 관련 메서드


## for ...in
for...in 구문은 객체의 key값에 접근할 수 있지만, value값에 접근하는 방법은 제공 하지 않는다

자바스크립트에서 객체속성들은 내부적으로 사용하는 숨겨진 속성들을 가지고 있다
```js
var obj = {
    a: 1, 
    b: 2, 
    c: 3
};

for (var key in obj) {
    console.log(key, obj[key]); // a 1, b 2, c 3
}
```

## Object.keys()

Object.keys() 메소드는 객체의 키만 담은 배열을 반환한다
```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.keys(object1)); // ["a", "b", "c"]
```
## object.values()
Object.values() 메소드는 객체의 값만 담은 배열을 반환한다

이 배열은 for...in 구문과 동일한 순서를 갖지만 배열로 리턴한다는 특징을 갖는다
```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.values(object1)); // ["somestring", 42, false]
```

## Object.entries()

[키, 값] 쌍을 담은 배열을 반환한다
```js
const object1 = {
  a: 'somestring',
  b: 42,
  c: false
};

console.log(Object.entries(object1)) // [ ["a","somestring"], ["b",42], ["c", false] ]
```

## Object.assign({},obj1,obj2)

객체를 병합해서 반환하는 메소드, 키의 값이 일치하면 덮어쓰기를 한 후에 객체로 반환을 한다

```js
const obj1 = {
  1: "철수",
  2: "훈이",
  3: "유리"
};

const obj2 = {
  1: "철",
  2: "훈이",
  3: "유리"
};

console.log(Object.assign({},obj1,obj2)) // { 1: "철", 2: "훈이", 3: "유리"} 
```


