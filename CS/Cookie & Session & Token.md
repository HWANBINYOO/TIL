# Cookie & Session & Token
서버가 클라이언트 인증을 확인하는 방식은 대표적으로 쿠키, 세션, 토큰 3가지 방식이다

## Cookie 인증

쿠키는 `Key-Value 형식`의 문자열 덩어리이다

쿠키에는 `이름, 값, 만료 날짜, 경로 정보`가 들어있다

Response Header의 Set-Cookie 속성을 사용하면 클라이언트에 쿠키를 만들 수 있다

### 과정

클라이언트가 서버에 요청을 보내면 서버는 `응답 헤더의 Set-Cookie`에 담으면 클라이언트는 요청을 보낼 때마다 쿠키를 `요청 헤더의 Cookie`에 담아 보내고,

서버는 쿠키에 담긴 정보를 바탕으로 해당 요청의 클라이언트가 누군지 식별하는 방식이다

### 단점

요청 시 쿠키의 값을 그대로 보내기 때문에 유출 및 조작 당할 위험이 존재한다(보안 취약)

쿠키에는 용량이작아 많은 정보를 담을 수 없다

쿠키의 사이즈가 커질수록 네트워크에 부하가 심해진다

## Session 인증

### 과정

쿠키와는 달리 서버의 저장소를 이용하고 유저가 사이트에 접근했을 시 `유저의 session-id`만을 생성하여 클라이언트 측에 담아주고,

서버쪽으로 요청이 들어왔을시 session-id(쿠키) 값을 받아 사용자를 인식 및 인증하는 방식이다

쿠키와는 달리 서버측에 데이터가 저장되니 보안상에서 더 안전하다

### 단점

브라우저를 닫을 시 사라진다

서버의 자원을 이용하기에 그만큼 서버속도가 느려질 수 있다.


## Token 인증

### 과정

서버가 클라이언트 측에 토큰을 전달해준다 그 후 클라이언트는 토큰을 저장하여 서버측에 요청을 할 때마다 이 토큰을 포함하여 전달하면

서버가 그 토큰을 가지고사용자를 인식 및 인증하는 방식이다

### 단점

토큰을 탈취당하면 대처하기 어렵다 (따라서 사용 기간 제한을 설정하는 식으로 극복한다)

Payload 자체는 암호화되지 않기 때문에 유저의 중요한 정보는 담을 수 없다

## JWT (JSON Web Token)

JWT란 인증에 필요한 정보들을 암호화시킨 JSON 토큰을 의미한다

### 과정

서버가 클라이언트 측에 `Access Token 와 refresh Token` 을 발급해주고 서버측에 요청을 할 때마다 `Access Token` 포함하여 전달하면

서버에서는 암호화된 토큰을 복호화 사용자를 인식 및 인증하는 방식이다

Access Token 만료시 refresh Token을 이용해 Access Token 재발급을 해준다

refresh Token 만료시 로그아웃이 되게 한다

### 단점

Self-contained : 토큰 자체에 정보를 담고 있으므로 양날의 검이 될 수 있다

Store Token : stateless 특징을 가지기 때문에, 토큰은 클라이언트 측에서 관리하고 저장한다. 때문에 토큰 자체를 탈취당하면 대처하기가 어렵게 된다
