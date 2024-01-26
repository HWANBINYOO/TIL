

## React.memo

React.memo()는 컴포넌트가 동일한 props로 렌더링 될 때 리렌더링을 방지할 수 있게하는 [고차 컴포넌트(Higher-Order Component)](https://ko.legacy.reactjs.org/docs/higher-order-components.html)다.   
즉, 메모화된 버전의 컴포넌트로 해당 컴포넌트의 props가 변경될 때만 리렌더링을 할 수 있다.

## 구조

```ts
const MemoizedComponent = memo(Component, arePropsEqual?)
```
**Component** : 메모할 구성 요소다. `memo` 는 이 구성 요소를 수정하지 않고, 대신 메모한 새 구성 요소를 반환한다. 함수 및 `forwardRef` 구성 요소를 포함하여 유효한 React 구성 요소는 허용된다.

**arePropsEqual**(선택사항) : 구성 요소의 이전 소품과 새 소품의 두 가지 인수를 수용하는 기능이다. 이전 소품과 새 소품이 동일한 경우, 즉 구성 요소가 동일한 출력을 렌더링하고 새 소품과 기존 소품과 동일한 방식으로 동작하는 경우 `true`를 반환해야 한다. 그렇지 않은 경우에는 `false`를 반환해야 한다.


## 사용예시

React.memo는 인자로 들어간 컴포넌트에 어떤 props가 입력되는지 확인하고 입력되는 모든 props의 신규 값을 확인한 뒤 이를 기존의 props의 값과 비교하도록 리액트에게 전달하고 props의 값이 바뀐 경우에만 리렌더링이 된다.   
그리고 부모 컴포넌트가 변경되었지만 해당 컴포넌트의 props 값이 바뀌지 않았다면 리렌더링은 건너뛰게 된다.

```ts
import React, { memo } from 'react';

const Component = ({ show } : { show : boolean }) => {
  console.log('Component 가 리렌더링됩니다.');
  return (
    <div> {show ? '안녕' : ''} </div>
  );
};

export default memo(Component);
```

이렇게 감싸주면 props가 변경될 때만 리렌더링을 하고 감싸준 컴포넌트의 자식 컴포넌트까지 불필요한 리렌더링을 막을 수 있다.   

추가적으로, React.memo 에서 두번째 파라미터에 propsAreEqual 이라는 함수를 사용하여 특정 값들만 비교를 하는 것도 가능하다.

```ts
export default React.memo(
  Component,
  (prevProps, nextProps) => prevProps.show === nextProps.show
);
```



## 주의사항
이 memo 메서드는 부모 컴포넌트가 변경이 발생할 때마다 해당 컴포넌트로 이동하여 기존 props 값과 새로운 props의 값을 비교하게 된다.   
그러면 리액트는 기존의 props 값을 저장할 공간과 비교하는 작업이 필요해진다.   
따라서, 이 효율은 어떤 컴포넌트를 최적화하느냐에 따라 달라지게 되서  상황에 따라 적절히 사용하는 것이 중요하다.   

> 컴포넌트가 무겁지 않고 다른 props로 자주 렌더링된다면 React.memo()가 필요하지않다.




