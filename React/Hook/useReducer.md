# useReducer

useState 보다 좀 더 복잡한 상태 관리가 필요한 경우 reducer를 사용한다

```js
const [state, dispatch] = useReducer(reducer, initialState);
// state : 사용할 상태
// dispatch : state의 업데이트를 일으키기 위해 사용하는 함수
// reducer : state와 action를 받아 새로운 state를 반환하는 함수
// initialState : 초기 state
```
ex)
useState 사용
```js
import React, { useState } from "react";
function Counter() {
  const [number, setNumber] = useState(0);
  
  const onIncrease = () => { setNumber((prevNumber) => prevNumber + 1) };
  const onDecrease = () => { setNumber((prevNumber) => prevNumber - 1) };

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={onIncrease}>+1</button>
      <button onClick={onDecrease}>-1</button>
    </div>
  );
}
export default Counter;
```

useReducer 사용
```js
import React, { useReducer } from "react";

function reducer(state, action) {
  switch (action.type) {
    case "INCREMENT":
      return state + 1;
    case "DECREMENT":
      return state - 1;
    default:
      return state;
  }
}

function Counter() {
  const [number, dispatch] = useReducer(reducer, 0);

  return (
    <div>
      <h1>{number}</h1>
      <button onClick={() =>  dispatch({ type: "INCREMENT" })}>+1</button>
      <button onClick={() => dispatch({ type: "DECREMENT" })}>-1</button>
    </div>
  );
}
export default Counter;
```
