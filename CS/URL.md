# URL

URL은 일련의 규칙에 따라 웹에 있는 자원의 주소를 표현하는 문자열이다

![image](https://user-images.githubusercontent.com/82823150/202588351-277f8885-e112-4df3-b2d6-4f2619562afb.png)

## Scheme(스킴)

통신 프로토콜을 정의하는 부분이다

## Authority(도메인 & 포트)

### Domain

요청해야 할 웹 서버를 정의한 것이다

주로 도메인 네임을 통해 표현하지만 IP 주소를 사용해도 된다

#### Domain name

ip는 사람이 이해하고 기억하기 어렵기 때문에 각 ip에 이름을 부여한 것이다

ex)

naver.com -> 220.95.233.172

google.com -> 66.249.66.26

### Port

포트는 해당 웹 서버의 리소스에 접근할 때 사용할 포트 번호를 정의한다

ex) HTTP → 80 , HTTPS → 443

## Path to resource(리소스 경로)

URL이 가리키는 실제 자원이 위치한 경로를 표현하는 부분이다

## Parameters(파라미터)

웹 서버에서 요청을 처리하는 데 사용하라고 넘겨주는 추가 정보를 key-value 쌍으로 정의하는 부분이다

URL 파라미터의 시작은 ? 심볼을 통해 확인할 수 있고 여러 key-value 쌍을 & 심볼을 통해 이을 수 있다

## Anchor(앵커)

URL이 가리키는 리소스 내부의 특정 위치를 나타내는 부분이다
