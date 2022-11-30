# Pre-rendering

Next.js가 사전에 각 페이지의 HTML을 생성하는 방식이다(SEO 에 좋음)


## CSR과 차이

기존 React.js 에서 렌더링 방식(csr)
초기 로드 시 빈 화면이 나온다. 그래서 페이지가 모두 로드되는 속도가 느린편이다

![image](https://user-images.githubusercontent.com/82823150/204708612-103fa765-be90-4d77-a861-fc5cc49cb4df.png)

Next.js에서의 Pre-Rendering은 미리 생성한 HTML 파일을 초기 로드 시에도 표시해 미리 생성한 HTML 화면을 볼 수 있다

![image](https://user-images.githubusercontent.com/82823150/204708592-95c4ef71-2973-4a44-a001-0481e23611c0.png)


#### Hydration : 페이지가 브라우저에 의해 로드되면 , js코드가 완전히 동작가능한 페이지로 만들어주는것(컴포넌트들이 초기화되고 , 버튼들이 눌러지는것)


## Static Generation

HTML을 빌드 타임에 생성한다. pre-render된 HTML은 그 다음에 각 request 마다 재사용된다

![image](https://user-images.githubusercontent.com/82823150/204698270-fc821070-5d48-4644-a84c-fa49b74df1ab.png)


## Server-side Rendering

HTML을 각 request가 일어날 때마다 생성한다

![image](https://user-images.githubusercontent.com/82823150/204698288-16352736-6264-4b41-8ff2-b7b27d4996b1.png)


> 개발 모드(yarn run dev)에서는 Static Generation을 사용하는 페이지라도 모든 페이지가 Server-side Rendering 함
