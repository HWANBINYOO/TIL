# useEffect

컴포넌트가 렌더링 될 때마다 특정 작업(Sied effect)을 실행할 수 있도록 한다

### Side effect
Side effect는 component가 렌더링 된 이후에 비동기로 처리되어야 하는 부수적인 효과들을 뜻한다

```js
useEffect(함수, [배열]);
```

ex)

```js
1
useEffect(() => {
  console.log("렌더링 될때마다 실행");
},[]);

2
useEffect(() => {
  console.log("맨 처음 렌더링될 때 한 번만 실행");
},[]);

3
useEffect(() => {
  console.log(name);
  console.log("name이라는 값이 업데이트 될 때만 실행");
},[name]);
```


## useEffect 무한루프 상황

### 종속성 배열에 종속성을 전달하지 않을 경우
```js
function App() {
  const [count, setCount] = useState(0);
  useEffect(() => {
    setCount((count) => count + 1);
  });
  return (
    <div className="App">
      <p> value of count: {count} </p>
    </div>
  );
}
```
1. 첫 번째 렌더링에서 React는 count 값을 확인한후 useEffect 함수를 실행한다
2. useEffect는 setCount 메소드를 호출하고 count Hook의 값을 업데이트한다
3. React는 UI를 다시 렌더링하여 업데이트된 count 값을 표시한다
4. UI가 재렌더링 되었기 때문에, useEffect는 모든 렌더 사이클에서 실행되므로 또 다시 setCount 함수를 호출한다 -> 무한반복

#### 해결방법
```js
useEffect(() => {
  setCount((count) => count + 1);
}, []);
```

### 함수를 종속성으로 사용할 경우
```js
function App() {
  const [count, setCount] = useState(0);

  function logResult() {
    return 2 + 2;
  }
  useEffect(() => {
    setCount((count) => count + 1);
  }, [logResult]);
  return (
    <div className="App">
      <p> value of count: {count} </p>
    </div>
  );
}
```
1. useEffect는  디펜던시가 업데이트되었는지 확인하기 위해  얕은 비교(shallow comparison)를 실행한다
2. 각 렌더 동안 React가 logResult의 참조를 재정의한다
3. 각 사이클마다 useEffect 함수가 다시 트리거된다 -> 무한반복

#### 해결방법
useCallback Hook을 사용해 참조 값이 동일하게 유지되게한다
```js
const logResult = useCallback(() => {
  return 2 + 2;
}, []); // logResult가 메모된다
useEffect(()=> {
  setCount((count)=> count+1);
},[logResult]); //logResult 참조가 동일하게 유지되므로 무한 루프 오류가 없어진다
```

### 배열을 종속성으로 사용할 경우
```js
const [count, setCount] = useState(0);
const myArray = ["one", "two", "three"];

useEffect(() => {
  setCount((count) => count + 1); //이전처럼 Count 값을 증가시킨다
}, [myArray]); //배열 변수를 디펜던시로 전달
```
1. React는 디펜던시의 참조가 변경되었는지 확인하기 위해 얕은 비교를 사용한다
2. myArray에 대한 참조가 각 렌더에서 계속 변경되므로 useEffect는 setCount 을 실행한다
3. myArray의 불안정한 참조 값으로 인해 React는 모든 렌더 사이클에서 useEffect를 호출한다 -> 무한반복

#### 해결방법
useRef을 사용해 참조가 변경되지 않도록 변경 가능한 객체가 반환된다


### 객체(Object)를 종속성으로 사용할 경우
```js
const [count, setCount] = useState(0);
const person = { name: "Rue", age: 17 };
useEffect(() => {
  setCount((count) => count + 1);
}, [person]);
return (
  <div className="App">
    <p> Value of {count} </p>
  </div>
);
```
1. React는 얕은 비교를 통해 person의 참조 값이 변경되었는지 확인한다
2. 렌더링할 때마다 person 객체의 참조 값이 변경되므로 React는 useEffect를 다시 실행한다
3. 따라서 모든 업데이트 주기마다 setCount가 호출된다 -> 무한 반복

#### 해결 방법
useMemo를 사용해이 디펜던시가 변경될 때 메모된 값을 계산하고 각 렌더링 중에 상태의 참조 값이 변경되지 않도록해준다
```js
const person = useMemo(
  () => ({ name: "Rue", age: 17 }),
  [] //디펜던시가 없으므로 값이 변경되지 않는다.
);
useEffect(() => {
  setCount((count) => count + 1);
}, [person]);
```

### 잘못된 디펜던시를 전달할 경우
```js
const [count, setCount] = useState(0);
useEffect(() => {
  setCount((count) => count + 1);
}, [count]);

return (
  <div className="App">
    <button onClick={() => setCount((count) => count + 1)}>+</button>
    <p> Value of count{count} </p>
  </div>
);
```
 count 값이 업데이트 될 때마다, React가 useEffect를 호출 -> 무한 반복
 
 #### 해결방법
 ```js
const [count, setCount] = useState(0);
useEffect(() => {
  setCount((count) => count + 1);
}, []);
 ```





