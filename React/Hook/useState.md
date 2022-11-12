# useState
컴포넌트 안에서 변경될 값을 사용하기 위한 React Hook 이다

```js
const [상태 값 저장 변수, 상태 값 갱신 함수] = useState(상태 초기 값);
```


## 사용법
```js
import React, { useState } from 'react';

function Counter() {
  const [number, setNumber] = useState(0);

  const onIncrease = () => {
    setNumber(preNum => preNum + 1);
  }

  const onDecrease = () => {
    setNumber(preNum => preNum - 1);
  }

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

```js
 setNumber( number + 1) 
```
 원래 setNumber 파라미터에는 위와 같이 업데이트 할 새로운 값을 넣어주는데,
```js
setNumber( preNum => preNum + 1)
```
위와 같이 기존 값을 값을 업데이트 하는 함수를 넣어 값을 업데이트 할 수도 있다

이와 같은 함수형 업데이트는 컴포넌트를 최적화 할 때 주로 사용한다

## 객체값 관리하기

```js
import React, { useState } from 'react';

function InputSample() {
  const [inputs, setInputs] = useState({ name: '', nickname: ''});
  const { name, nickname } = inputs;
  
  const onChange = (e) => {
    const { value, name } = e.target;
    setInputs({ ...inputs, [name]: value });
  };
  const onReset = () => { setInputs({ name: '', nickname: '', }) };

  return 
    <div>
      <input  placeholder="이름" onChange={onChange} value={name} />
      <input placeholder="닉네임" onChange={onChange} value={nickname} />
      <button onClick={onReset}>초기화</button>
      <b> 소개: </b> {name} ({nickname})
    </div>
  ;
}
export default InputSample;

```
```js
setInputs({ ...inputs, [name]: value });
```
이렇게 기존 객체를 복사하여 새로운 객체에 업데이트 작업을 하는 것을 `불변성 유지`라 한다

불변성을 지켜줘야만 리액트가 컴포넌트의 상태가 업데이트 됐음을 감지할 수 있고  필요한 부분만을 리렌더링 할 수 있기 때문이다

(기존 상태를 직접 수정하는 경우 리렌더링이 되지 않는다)









