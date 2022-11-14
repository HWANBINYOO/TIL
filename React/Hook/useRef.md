# useRef

react에서 특정 DOM에 접근하게 해준다


```js
const refContainer = useRef(initialValue);
```

ex)
```js
import React, { useState, useEffect, useRef } from "react"
function App() {
  const [name, setName] = useState("")
  const inputRef = useRef("")
  console.log("render")
  const focus = () => { inputRef.current.focus() }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focus}>focus</button>
    </>
  )
}
export default App

```
```js
 inputRef.current.focus()
```
Ref객체의 .current값은 선택한 DOM을 가리키게 된다

## useRef 로 리렌더링 방지

```js
import React, { useState } from "react"

function App() {
  const [name, setName] = useState("")
  const [currentName, setCurrentName] = useState("")

  console.log("render")

  return (
    <>
      <input value={name} onChange={e => setName(e.target.value)} />
      <button onClick={() => setCurrentName(name)}>submit</button>
      <div>name : {currentName}</div>
    </>
  )
}
export default App
```
이렇게 하면 input 창에 입력되는 state 요소가 변경될때마다 불필요한 렌더링이 된다

#### 해결방법
ref를 통해 불필요한 렌더링을 줄일 수 있다
 
 화면을 처음 받아올 때와 제출 버튼을 눌렀을 때만 rendring이 일어난다
```js
import React, { useState, useRef } from "react"

function App() {
  const [currentName, setCurrentName] = useState("")
  const inputRef = useRef("")

  console.log("render")

  return (
    <>
      <input ref={inputRef} />
      <button onClick={() => setCurrentName(inputRef.current.value)}>제출</button>
      <div>name : {currentName} </div>
    </>
  )
}
export default App
```



