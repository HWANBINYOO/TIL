# SWR

데이터를 가져오기 위한 React Hooks이다

도중에 에러를 반환하더라도 캐시된 데이터를 활용할 수 있게 함으로써 불필요한 데이터 호출과 렌더링에 시간을 쓰지 않고 효율적으로 동작한다

```js
const { data, error, isValidating, mutate } = useSWR(key, fetcher, options)
```

파라미터

- `key`: 요청을 위한 고유한 키 문자열(또는 함수 | 배열 | null) 
- `fetcher`: 데이터를 가져오기 위한 함수를 반환하는 Promise
- `options`: SWR hook을 위한 옵션 객체

반환값

- `data`: fetcher가 이행한 주어진 키에 대한 데이터(로드되지 않았다면 undefined)
- `error`: fetcher가 던진 에러 성공시에는 undefined
- `isValidating`: 요청이나 갱신 로딩의 여부
- `mutate(data?, shouldRevalidate?)`: 캐시 된 데이터를 뮤테이트하기 위한 함수


## 전역 설정하기
SWRConfig를 통해 모든 SWR hook에 대한 전역 설정이 가능하다

```js
function App () {
  return (
    <SWRConfig 
      value={{
        refreshInterval: 3000,
        fetcher: (resource, init) => fetch(resource, init).then(res => res.json())
      }}
    >
      <App />
    </SWRConfig>
  )
}
```

## 자동 갱신

서비스의 특징과 상황에 맞추어 잘 켜고 끄고 하는게 가장중요하다

### revalidate

캐시된 데이터가 아닌 새로운 request로 새로운 데이터를 불러오는 것

- `revalidateOnFocus`: 페이지에 다시 포커스했을 때 갱신
- `refreshInterval`: 다중 기기, 다중 사용자로 인해 탭이 변경될 때 최종적으로 동일한 데이터를 렌더링
- `refreshWhenHidden, refreshWhenOffline`: 웹 페이지가 화면상에 있지 않거나 네트워크 연결이 없어도 데이터를 가져오게 한다. 기본적으로는 비활성화되어 있다
- `revalidateOnReconnect`: 사용자가 컴퓨터를 잠금 해제하고 동시에 인터넷이 아직 연결되지 않았을 때, 데이터를 항상 최신으로 보장하기 위해 네트워크가 회복될 때 자동으로 갱신하게 한다다. 기본적으로 비활성화되어 있다
- `revalidateIfStale`: 컴포넌트 마운트 시, stale data(이미 캐시된 데이터)가 존재할 경우 SWR이 갱신을 할지 말지를 제어할 수 있다

### mutation

useSWRConfig로부터 mutate 함수를 얻을 수 있고 SWR hook에게 갱신 메시지를 전역으로 브로드캐스팅할 수 있다

```js
import useSWR, { useSWRConfig } from 'swr'

function App () {
  const { mutate } = useSWRConfig()

  return (
    <div>
      <Profile />
      <button onClick={() => {
        // 쿠키를 만료된 것으로 설정
        document.cookie = 'token=; expires=Thu, 01 Jan 1970 00:00:00 UTC; path=/;'

        // 이 키로 모든 SWR에게 갱신하도록 요청
        mutate('/api/user')
      }}>
        Logout
      </button>
    </div>
  )
}
```


