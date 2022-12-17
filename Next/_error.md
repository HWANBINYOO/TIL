# 에러 페이지 만들기

넥스트에서 빌드된 프로덕션 환경에서 에러가 발생한다면 넥스트는 커스텀 에러 페이지로 넘어가게 할 수 있다

## custom 500 page

Pages 폴더에 `_error.js` 파일을 만들게 되면 에러가 발생하였을때 페이지를 보여주게 된다

개발 모드에서는 서버 에러가 나면 로그를 보여줘서 프로덕션 모드에서 확인해야 한다

```tsx
// _error.js
function Error({ statusCode }) {
  return (
    <p>
      {statusCode
        ? `An error ${statusCode} occurred on server`
        : 'An error occurred on client'}
    </p>
  )
}

Error.getInitialProps = ({ res, err }) => {
  const statusCode = res ? res.statusCode : err ? err.statusCode : 404
  return { statusCode }
}

export default Error
```

## custom 404 page

404 page는 자주 사용되는 에러 페이지

자주 사용되는 에러 페이지를 서버에서 렌더링 하면 서버의 부하가 증가

이로인해 비용이 증가하고, 사용자들은 느리다는 느낌을 받아서 
404는 Next.js가 제공하는 static 404 page를 사용해 처리하는것이 좋다


```js
// pages/404.js
const NotFound = () => {
  return <p>404 페이지 입니다.</p>;
}

exort default NotFound;
```
