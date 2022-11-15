# Next

React 라이브러리의 프레임워크이다

SEO(Search Engine Optimization)를 위한 Server-Side Rendering(SSR)을 가능하게 하기 때문에 사용한다

## next.js가 제공하는 주요 기능

### automatic routing
pages 폴더에 있는 파일은 해당 파일 이름으로 라우팅된다 (pages/page1.tsx -> localhost:3000/page1)


### _document.tsx
meta 태그를 정의하거나, 전체 페이지에 관려하는 컴포넌트이다
```js
// pages/_document.tsx
import Document, { Html, Head, Main, NextScript } from "next/document";
export default class CustomDocument extends Document {
  render() {
    return (
      <Html>
        <Head>
          // 모든페이지에 아래 메타테크가 head에 들어감 
          // 루트파일이기에 가능한 적은 코드만 넣어야함 전역 파일을 엉망으로 만들면 안된다
          // 웹 타이틀, ga 같은것 넣음
          <meta property="custom" content="123123" />
        </Head>
        <body>
          <Main />
        </body>
        <NextScript />
      </Html>
    );
  }
}
 ```

### _app.tsx
이곳에서 렌더링 하는 값은 모든 페이지에 영향을 준다

_app.tsx은 클라이언트에서 띄우길 바라는 전체 컴포넌트 → 공통 레이아웃임으로 최초 실행되며 내부에 컴포넌트들을 실행한다
```js
function MyApp({ Component, pageProps }) {
  return <Component {...pageProps} />;
}
export default MyApp;
```

 ### 동적 url
가변적으로 변하는 url에 대해 동적 url을 지원해서 [] 문법으로 동적 페이지를 생성하는 동적 url을 만들 수 있다
 
localhost:3000/123 으로 접속시 id 가 123으로 나온다
  
pages/[값].tsx 왼쪽 페이지 구조의 값은 router.query.값과 동일하다
```js
// pages/[id].tsx

import { useRouter } from "next/router";

export default () => {
  const router = useRouter();

  return (
    <>
      <h1>post</h1>
      <p>postid: {router.query.id}</p>
    </>
  );
}
 ```
 
 
 
 
 
 
 
