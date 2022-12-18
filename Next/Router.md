# Next.js Route


## Link

next/link의 Link를 사용해 페이지를 이동할 수 있다

```js
import Link from 'next/link'

function Home() {
  return (
    <ul>
      <li>
        <Link href="/">Home</Link>
      </li>
      <li>
        <Link href="/about">About Us</Link>
      </li>
      <li>
        <Link href="/blog/hello-world">Blog Post</Link>
      </li>
    </ul>
  )
}

export default Home
```

- `href(필수)` : 이동할 경로 또는 URL
- `as` : 브라우저 URL 표시 줄에 표시 될 경로
- `passHref` : Link가 href 속성을 child에게 보낸다 (기본값은 false)
- `prefetch` : 백그라운드에서 페이지를 미리 가져온다. 뷰포트에 있는 모든 항목이 미리 로드 되며, prefetch={false}을 전달하여 비활성화 할 수 있다. 
false 여도 마우스를 hover 하면 프리페치가 계속 발생한다. 정적 생성을 사용하는 페이지는 더 빠른 페이지 전환을 위해 데이터와 함께 JSON 파일을 미리 로드한다. 프리 페치는 프로덕션에서만 활성화된다 (기본값은 true)
- `replace` :  history 스택에 새 URL을 추가하지 않고 현재 상태만 교체한다 (기본값은 false)
- `scroll` : 기본값은 true로 페이지 이동 후 상단으로 스크롤한다 (기본값은 true)
- `shallow` : getStaticProps, getServerSideProps, getInitialProps 를 실행하지 않고 현재 페이지의 경로를 업데이트한다 (기본값은 false)
- `locale` : 활성 locale 이 자동으로 앞에 추가된다

## useRouter

next/router 의 useRouter 를 사용해 router 객체에 접근할 수 있다

 ```js
 import { useRouter } from 'next/router';

export default function Home() {
  const router = useRouter();
  console.log(router);
  // ...
}
```

- `pathname` : `string` : 현재 경로로 /pages 의 페이지 경로이며(파일명), basePath 또는 locale 은 포함되지 않는다
- `query` : `object` : 동적 라우트 매개변수를 포함하는 객체로 구문 분석된 쿼리 문자열
- `asPath` : `string` : basePath 또는 locale 없이 브라우저에 표시되는 경로(query 포함)
- `isFallback` : `boolean` : 현재 페이지의 fallback 모드 여부
- `basePath` : `string` : 활성화된 basePath
- `locale` : `string` : 활성화된 locale
- `locales` : `string\[\]` : 지원되는 모든 locale
- `isReady` : `boolean` : 라우터 필드가 클라이언트 측에서 업데이트되고 사용할 준비가 되었는지 여부. useEffect 메소드 내에서만 사용해야하며 서버에서 조건부로 렌더링 하는 데에 사용해야 한다
- `isPreview` : `boolean` : 애플리케이션의 미리보기 모드 여부

### router.push

클라이언트 사이드의 라우팅 처리를 할 수 있는 기능이고  Next/link 대신 사용할 수 있다

router.push는 외부 url 사용시에는 적합하지 않다. a tag의 target="_blank" 를 사용하거나 window.location을 사용하는 것이 낫다

```js
router.push(url, as, options)
```

- url(필수) : 이동할 경로
- as : 브라우저에서 표시된 경로
- options
  - scroll : 페이지 이동 후 상단으로 스크롤(기본값은 true)
  - shallow : getStaticProps, getServerSideProps, getInitialProps 를 실행하지 않고 현재 페이지의 경로를 업데이트(기본값은 false)
  - locale : 새 페이지의 로케일 표시

### router.replace

router.push와 비슷하게 동작하지만, 라우터 히스토리 스택에 새로운 url을 추가하지 않는다. 대신 기존에 있던 현재 페이지 route를 새로운 url로 대체한다

### router.back

히스토리에서 전단계로 이동한다. window.history.back() 와 같이 동작한다





