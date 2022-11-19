# React에서의 이벤트처리

## html과 차이점

React 이벤트 이름은 소문자 대신 camelCase를 사용한다 (`onclick` -> `onClick`)

JSX에 문자열 대신 함수를 전달한다 (`onclick="activateButton()"` ->  `onClick={activateButton)`)

## 주의할점
DOM 요소에만 이벤트 설정이 가능하다 

div, button, input, form, span 등의 DOM 요소에는 이벤트 설정이 가능하지만, 리액트의 컴포넌트에는 불가능하다
```js
function App() {
  const sayHi = function () {
    alert('hello');
  }
  return  <Component onClick={sayHi} name="홍길동" nickname="홍홍" />  // 이벤트가 실행되지 않는다
}
```

## 이벤트 핸들러 네이밍

on접두사를 붙여서 onEvent, Event Handler function에는 handle접두사를 붙여서 handleEvent로 네이밍 하는 것이 일반적이다
```js
const handleClick = () => console.log('button click')
<button className='subjectBtn' onClick={handleClick} />
```

### 여러개의 동일한 컴포넌트들이 존재하는 경우

이때에는 다음 아래와 같이 handleEvent + 컴포넌트로 네이밍한다
```js
const handleClickTitleBtn = () => console.log('title button click')
const handleClickSubTitleBtn = () => console.log('subTitle button click')
const handleClickNameInput = () => console.log('name button click')

<button className='titleBtn' onClick={handleClickTitleBtn} />
<button className='subTitleBtn' onClick={handleClickSubTitleBtn} />
<input className='nameInput' onClick={handleClickNameInput} />
```
