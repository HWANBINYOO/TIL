# tilde(~), double tilde(~~)

## tilde(~)

tilde 연산자는 비트연산자로 NOT의 기능을 한다

아래와 같이 2진수일 때 0과 1만 뒤바꾸면 된다

```js
const a = 5;     // 0000000000000101
console.log(~a); // 1111111111111010
// expected output: -6

const b = -3;    // 1111111111111101
console.log(~b); // 0000000000000010
// expected output: 2
```

## double tilde(~~)

tilde를 2번 반복해주는 것이다

### 1. Math.floor() 대신 사용된다
숫자에 `~`연산을 하게되면 소수점들은 버려지게되서 `Math.floor()` 처럼 활용할 수 있다

#### 장점
속도가 가장 빠르다

[The Mysterious Double Tilde (~~) Operation](https://dev.to/asadm/the-mysterious-double-tilde-operation-mih) 에
크롬, Safari,iPhone XS 각각 `Math.floor`, `~~`, `parseInt` 의 속도를 비교한 결과가 있는데 ~~ , Math.floor, parseInt 순으로 ~~가 가장 빠른 퍼포먼스를 보여줬다.
 
#### 단점
복잡한 코드 또는 협업하는 과정에서는 가독성이 좋진않다

### 2. undefined 또는 null을 0으로 변환할 때 사용된다

ex) 배열[1,1,1,2,2,3,3,3,3]을 각 숫자가 몇개인지 객체에 저장하고싶을때

```js
const arr = [1,1,1,2,2,3,3,3,3]
const obj1 = {}

arr.forEach(v=>{
  if(obj1[v]) obj1[v]+=1
  else obj1[v]=1
})
//obj1 {1: 3, 2: 2, 3: 4}
```

위와같이 NaN 오류가 나오기때문에 obj에 key값이 있는지 확인해주는 작업이 필요하다

```js
const obj2 = {}
arr.forEach(v=>obj2[v]= ~~obj2[v]+1)
//obj2 {1: 3, 2: 2, 3: 4}
```
`~~`를 활용해 다시 코드를 작성하면 `undefined`가 나올 수 있는 상황을 `~~`연산자를 이용해서 간단하게 해결할 수 있다





