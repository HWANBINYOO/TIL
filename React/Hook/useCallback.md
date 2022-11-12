# useCallback 

함수를 메모이제이션(memoization)하기 위해서 사용되는 hook 함수다

첫번째 인자로 넘어온 함수를, 두번째 인자로 넘어온 배열 내의 값이 변경될 때까지 저장해놓고 재사용할 수 있게 해준다
```js
const memoizedCallback = useCallback(함수, 배열);
```

ex)

어떤 React 컴포넌트 함수 안에 함수가 선언이 되어 있다면 이 함수는 해당 컴포넌트가 랜더링될 때 마다 새로운 함수가 생성된다
```js
const add = () => x + y;
```
하지만 useCallback()을 사용하면 ,  x 또는 y 값(이 함수가 의존하는 값들) 이 바뀌면 새로운 함수가 생성되어 add 변수에 할당되고, 
x와 y 값이 동일하다면 다음 랜더링 때 이 함수를 재사용한다
```js
const add = useCallback(() => x + y, [x, y]);
```
사실 컴포넌트가 랜더링될 때마다 함수를 새로 선언하는 것은 성능 상 큰 문제가 되지 않는다
따라서 단순히 컴포넌트 내에서 함수를 반복해서 생성하지 않기 위해서 useCallback()을 사용하는 것은 큰 의미가 없거나 오히려 손해인 경우도 있다

## useCallback 을 사용해야 할때

### 의존 배열로 함수를 넘길 때
userEffect 에서 fetchUser함수를써서 user값을 받아올떄 , fetchUser는 함수이기 때문에 userId 값이 바뀌든 말든 컴포넌트가 랜더링될 때 마다 새로운 참조값으로 변경된다

하지만 useEffect() 함수가 호출되어 user 상태값이 바뀌고 그러면 다시 랜더링이 되고 그럼 또 다시 useEffect() 함수가 호출되는 악순환이 반복된다
```js
import React, { useState, useEffect } from "react";

function Profile({ userId }) {
  const [user, setUser] = useState(null);

  const fetchUser = () =>
    fetch(`https://your-api.com/users/${userId}`)
      .then((response) => response.json())
      .then(({ user }) => user);

  useEffect(() => {
    fetchUser().then((user) => setUser(user));
  }, [fetchUser]);
}
```
이런 상황일떄 useCallback() hook 함수를 이용하면 컴포넌트가 다시 랜더링되더라도 useEffect()에 넘어온 함수는 userId 값이 변경되지 않는 한 재호출 되지 않게 된다
```js
import React, { useState, useEffect } from "react";

function Profile({ userId }) {
  const [user, setUser] = useState(null);

  const fetchUser = useCallback(
    () =>
      fetch(`https://your-api.com/users/${userId}`)
        .then((response) => response.json())
        .then(({ user }) => user),
    [userId]
  );

  useEffect(() => {
    fetchUser().then((user) => setUser(user));
  }, [fetchUser]);
}
```
