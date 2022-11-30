# getStaticPaths

동적라우팅 + getStaticProps를 원할 때 사용한다

동적 경로를 사용하는 페이지에서 getStaticPaths(정적 사이트 생성)라는 함수를 export할 때
Next.js는 getStaticPaths에 의해 지정된 모든 경로를 정적으로 미리 렌더링한다

getStaticPaths는 getStaticProps와 함께 사용해야 한다

```js
export default function Post({ posts }) {
  console.log(posts)
}

export const getStaticPaths = async () => {
  const res = await fetch('https://.../posts')
  const posts = await res.json()

  // pre-render할 Path
  const paths = posts.map((post) => ({
    params: { id: post.id },
  }))

  return { paths, fallback: false }
}

export const getStaticProps = async ({ params }) => {
  const res = await fetch(`https://.../posts/${params.id}`)
  const post = await res.json()

  return { props: { post } }
}
```
### paths : 빌드타임에 pre-rendering할 경로들

### fallback : blocking

getStaticPaths에서 반환되지 않은 새 경로는 SSR과 동일하게 HTML이 생성될 때까지 기다렸다가 이후 요청을 위해 캐시되어
path당 한 번만 발생함 fallback: 'blocking'은 기본적으로 생성된 페이지를 업데이트하지 않는다

생성된 페이지를 업데이트하려면 fallback: blocking과 함께 ISR을 사용해야한다

### fallback : false

getStaticPaths가 반환한 경로만 빌드하고 paths에 등록되지 않은 경로로 들어가면 404 페이지가 된다

이 옵션은 생성할 경로가 적거나 새 페이지 데이터가 자주 추가되지 않는 경우에 유용하다

### fallback : true

paths에 등록되지 않은 경로로 들어가면 404 페이지가 되는 대신에 별도의 컴포넌트를 보여줄 수 있다(router.isFallback으로 감지)
 
그 후 getStaticProps 를 통해 데이터를 가져오고 props를 가져오면 정적 페이지를 생성한후 한번 렌더링 후부터 pre-render에 포함된다
(계속적으로 상품이 등록될 때 유용한 기능이다)
