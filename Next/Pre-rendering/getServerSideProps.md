# getServerSideProps

페이지에서 getServerSideProps(서버 측 렌더링)라는 함수를 export 하면 
getServerSideProps 를 먼저 실행후 반환된 데이터를 사용하여 각이 페이지를 미리 랜더링한다

getServerSideProps 는 계속 데이터가 바뀌어야하는 페이지의 경우 사용한다

```js
import { GetServerSideProps } from 'next'

export default function Page({ data }) {
  console.log(data)
}

export const getServerSideProps: GetServerSideProps = async (context) => {
  
  const res = await fetch(`https://.../data`)
  const data = await res.json()

  // data 없을 땐 리턴값을 달리함
   if (!data) {
    return {
      redirect: {
        destination: '/',
        permanent: false,
      },
    }
  }
  
  return {
    props: {
      data: data
    }
  }
}

```
## context 구성

`params`: params를 라우트 파라미터 정보(다이나믹 라우트 페이지라면)

`query` : 쿼리스트링

`req` : HTTP request object

`res` : HTTP response object

`err` : HTTP error object



## return 값 종류

`props` : 해당 컴포넌트로 리턴할 값 (선택적)

`redirect` : 값 내부와 외부 리소스 리디렉션 허용한다 (선택적) 무조건 { destination: string, permanent: boolean } 의 꼴이어야 한다

`notFound` : Boolean값, 404status를 보내는 것을 허용한다 (선택적)


## 단점

getServerSideProps를 이용해서 데이터를 불러오는 도중에 에러가 나면 에러가 나는 과정에서 유저는 아무 UI도 볼 수 없게된다

