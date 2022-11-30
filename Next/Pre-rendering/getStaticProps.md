# getStaticProps

항상 서버에서 실행되고 클라이언트에서는 실행되지 않는다

getStaticProps는 정적 HTML을 생성하므로 들어오는 request(예: 쿼리 매개변수 또는 HTTP 헤더)에 액세스할 수 없다

getStaticProps는 빌드시 고정되는 값으로 빌드 이후에는 수정이 불가능하다

```js
import { GetStaticProps } from 'next'

export default function Blog({ posts }) {
  console.log(posts)
}

export const getStaticProps: GetStaticProps = async (context) => {
  const res = await fetch('https://.../posts')
  const posts = await res.json()
  
  if (!data) {
    return {
      notFound: true,
    }
  }

  return {
    props: {
      posts,
    },
  }
}

```
