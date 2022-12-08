# Recoil

hook처럼 리액트의 상태를 간단하게 변경하고 이용 가능하다

## RecoilRoot

컴포넌트들이 전역상태를 사용하기 위해선 RecoilRoot 컴포넌트를 부모 컴포넌트로 가져야한다

```js
import React from 'react';
import {RecoilRoot} from 'recoil';
function App() {
  return (
    <RecoilRoot>
      <CharacterCounter />
    </RecoilRoot>
  );
}
```

## Atom

Atoms는 상태의 단위이며, 업데이트와 구독이 가능하다

atom이 업데이트되면 각각의 구독중인 컴포넌트는 새로운 값을 반영하여 다시 렌더링 된다

```js
const textState = atom({
  key: 'textState', // unique ID (다른 atoms/selectors을 구별하기 위해서)
  default: '', // default value (aka initial value)
});
```


## useRecoilState

useRecoilState는 useState와 사용법이 동일하다
아톰의 상태를 설정할 수 있고, 변경 시킬 수 도 있다

```js
  const [text, setText] = useRecoilState(textState);
```

useRecoilValue : 아톰을 조회할 때만 사용

useSetRecoilState : 아톰을 변경만 시킬떄

useResetRecoilState : 아톰을 초기값으로 변경시킬떄


## selector

atom 또는 selector 를 기반으로 새롭게 결과를 구성해주는 순수함수다

```js
import { atom, selector } from 'recoil';

const jobListState = atom({
  key: 'jobListState',
  default: [],
});

const completedJobsSelector = selector({
  key: 'completedJobsSelector',
  get: ({ get }) => {
    const jobList = get(jobListState);
    const completed = jobList.filter((v) => v.isDone);
    return completed;
  },
});
```


