# middleware

처음 유저가 보낸 요청과 종착지 사이에 있는 소프트웨어이다. 유저의 정보를 DB에 보낼 때 중간에서 미들웨어를 거친다

사용자의 수신 요청에 따라 rewriting, redirecting, 헤더 추가 또는 HTML 스트리밍을 통해 response를 수정할 수 있다

```js
import type { NextRequest, NextFetchEvent } from "next/server";

export function middleware(request: NextRequest, event: NextFetchEvent) {
  console.log("전역 미들웨어입니다.");
}
```

## Bot 제한
request.ua(user agent) 내부에 isBot이 담겨 있으며, boolean으로 표현된다

이것으로 홈페이지에 접근한 대상이 봇일 때 렌더링 전에 차단할 수 있다
```js
import type { NextRequest, NextFetchEvent } from "next/server";
import { NextResponse } from "next/server";

export function middleware(request: NextRequest, event: NextFetchEvent) {
  if (req.ua?.isBot) {
    return new Response("bot은 접근 불가.", { status: 403 });
  }
}
```
## 비로그인 유저 제한
request의 cookies를 이용해, 쿠키(혹은 세션)가 없다면 로그인 페이지로 강제 이동시킨다.

때문에 페이지로 접근을 시도했어도, 해당 페이지가 렌더링 되기 전에 로그인 페이지로 리다이렉트하므로 잠깐 동안의 페이지 노출까지 방지할 수 있다.

```js
import type { NextRequest, NextFetchEvent } from "next/server";
import { NextResponse } from "next/server";

export function middleware(request: NextRequest, event: NextFetchEvent) {
  
  if (!request.url.includes("/login") && !request.cookies.session) {
    return NextResponse.rewrite(new URL("/login", request.url));
  }
}
```

