# useMemo 


### Memoization
memoization이란 기존에 수행한 연산의 결과값을 어딘가에 저장해두고 동일한 입력이 들어오면 재활용하는 프로그래밍 기법이다

ex)


아래 컴포넌트는 prop으로 넘어온 x와 y 값을 compute 함수에 인자로 넘겨서 z 값을 구한 후, 그 결과값을 div 엘리먼트로 감싸 출력해준다
```js
function MyComponent({ x, y }) {
  const z = compute(x, y);
  return <div>{z}</div>;
}
```
만약에, compute 함수가 값을 리턴하는데 시간이 몇초 이상 오래 걸린다면 컴포넌트가 재랜더링이 될때마다 이 함수가 호출이 되므로 지속적으로 UI에서 지연이 발생한다
```js
function MyComponent({ x, y }) {
  const z = useMemo(() => compute(x, y), [x, y]);
  return <div>{z}</div>;
}
```
x와 y 값이 이 전에 랜더링했을 때와 동일할 경우, 이 전 랜더링 때 저장해두었던 결과값을 재활용합니다. 하지만, x와 y 값이 이 전에 랜더링했을 때와 달라졌을 경우, 
`() => compute(x, y)` 함수를 호출하여 결과값을 새롭게 구해 z에 할당해준다


##  memoization 하기 위해서 사용되는 React hook 함수쓸떄 유의할점

일반적으로 소프트웨어의 성능 최적화에는 그에 상응하는 대가가 따르기 마련이다. 따라서, 
성능 최적화를 할때는 얻을 수 있는 실제 성능 이점이 지불하는 대가에 비해서 미미하지 않은지에 대해서 반드시 따지고 사용해야 한다

예를 들어 ,useMemo hook 함수를 납용하면, 컴포넌트의 복잡도가 올라가기 때문에 코드를 읽기도 어려워지고 유지보수성도 떨어지게 된다
또한 useMemo가 적용된 레퍼런스는 재활용을 위해서 가바지 컬렉션(garbage collection)에서 제외되기 때문에 메모리를 더 쓰게 된다
