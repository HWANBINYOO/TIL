# Promise

프로미스는 자바스크립트 비동기 처리에 사용되는 객체이다

```js
let promise = new Promise(function(resolve, reject) {
  // executor (제작 코드, '가수')
});
```
executor : 결과를 최종적으로 만들어내는 제작 코드를 포함한다

resolve(value) : 일이 성공적으로 끝난 경우 그 결과를 나타내는 value와 함께 호출한다

reject(error) : 에러 발생 시 에러 객체를 나타내는 error와 함께 호출한다

ex)
```js
const promise = new Promise((resolve, reejct) => {
  // doing sth heavy work (network or read file)
  console.log("doing sth...");
  setTimeout(() => {
    resolve("Noah"); // 성공했을 때 Noah라는 값을 return하게 된다.
    reejct(new Error("no network")); // 실패했을 때는 "no network'라는 값을 return하게 된다. 
    //new Error는 자바스크립트에서 제공하는 클래스다.
  }, 2000);
});
```

## Consumer
return된 Promise를 받은 후에 then, catch, finally로 값을 가공해준다

```js
promise
.then((value) => {  // resolve 일떄
  console.log(value);
})
.catch((error) => { // reject 일떄
  console.log(error);
})
.finally(() => {    //  성공하든 실패하든 상관없이 실행하고 싶은 기능
  console.log("anyway finally");
});
```
