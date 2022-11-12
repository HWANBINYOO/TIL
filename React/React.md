# React
사용자가 조작하기 위한 UI를 만들도록 도와주는 component 기반 프론트앤드 라이브러리다

싱글 페이지 애플리케이션이고 , 모바일 애플리케이션 개발 시 사용될 수 있다


## 특징

### `Component 기반 구조`
Component 기반 구조를 이용해 유지보수, 관리, 재사용이 용이해지진다

### `Data Flow`
데이터의 흐름이 한 방향(부모 -> 자식)으로 흐르는 단반향 데이터 (one-way data flow) 이다

부모의 데이터를 바꿔줄떈 state를 이용한다

### `JSX(JavaScript eXtension)`
React에서 HTML을 표현할 때, JSX를 사용한다. 

외관상 HTML 같은 마크업 언어를 리터럴로 입력하는 것으로 보이는데, 빌드 시 Babel에 의해 자바스크립트로 변환된다. 

자바스크립트 코드를 HTML처럼 표현할 수 있기 때문에 용이한 개발이 가능하다.


### `Virtual Dom`

HTML 코드를 작성하고 HTML 파일을 열게 되면, HTML 코드들이 DOM을 만들고 코드가 수정되면 전체 DOM을 새롭게 만들어 비효율적이다

React Virtual DOM은 변경된 부분만 DOM의 반영하는 방식으로 작업해 효율성과 속도를 높인다


### `Props and State`
Props는 부모 컴포넌트에서 자식 컴포넌트로 전달해 주는 데이터다

State는 컴포넌트 내부에서 선언하며 내부에서 값을 변경할 수 있다
