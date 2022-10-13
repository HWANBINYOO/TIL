# meta
해당 문서에 대한 정보인 메타데이터(metadata)를 정의할 때 사용한다

### 속성

- charset
    - 해당 문서의 `문자 인코딩 방식`을 명시한다
    ```html
    <mata charset="문자셋">
    ```

- name 
    - `메타데이터이름` 을 명시한다
    - 속성값 : viewport , keywors , description , author , robots , viewport
    ```html
    <mata name="정보 이름" content="필수">
    ```
    - `viewport`
        - <b>반응형 웹 구현을 위해 필요한 매타태그</b>다
        - 너비는 보고 있는 기기의 너비이면 그에 맞춰 초기 화면 배율을 1로 지정한다는 의미입니다.

- content
    - name속성이나 http-equiv 속성과 관련된 값(value)을 명시한다
    ```html
    <meta name="필수" content="정보 텍스트">
    ```

- http-equiv
    - content 속성에 명시된 값에 대한 HTTP 헤더를 제공한다
    ```html
    <meta http-equiv="속성값">
