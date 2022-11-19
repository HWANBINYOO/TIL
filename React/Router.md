# React-Router

손쉽게 싱글 페이지 애플리케이션을 만들 수 있는 라이브러리이다

## Route
특정 경로에 원하는 컴포넌트를 보여준다

```js
<Route path="주소규칙" element={보여 줄 컴포넌트 JSX} />
```

Route 컴포넌트는 Routes 컴포넌트 내부에서 사용되야한다
 ```js
<Routes>
  <Route path="/" element={<Home />} />
  <Route path="/about" element={<About />} />
</Routes>
```
### 루트경로 접속시 (/)
```js
<Route path="/" element={<Main />}></Route>
```

###  상세 페이지 접속시 (/product/*)
```js
<Route path="/product/*" element={<Product />}></Route>
```



## Link
다른 페이지로 이동하는 링크를 보여준다
```js
<Link to="경로">링크 이름</Link>
```

## useParams
/product/:productId 와 같이 경로에 : 를 사용하여 설정한다
```js
<Route path="/product/:productId" element={<Product />}></Route>
 ```
useParams를 통해 productId를 받아 활용 가능

 ```js
const Product = () => {
  const { productId } = useParams();
  return <h3>{productId}번</h3>
}
```

## useLocation
- hash : 주소의 #문자열 뒤의 값
- pathname : 현재 주소 경로
- search : ?를 포함한 쿼리스트링
- state : 페이지로 이동시 임의로 넣을 수 있는 상태 값
- key : location 객체의 고유 값, 초기값은 default, 페이지가 변경될 때 마다 고유의 값이 생성됨

ex)

http://localhost:3000/product/1?search=productName&q=demo#test

```js
const Product = () => {
  const location = useLocation();
  return (
    <ul>
        <li>hash : {location.hash}</li>         // #test
        <li>pathname : {location.pathname}</li> // product/1
        <li>search : {location.search}</li>     // ?search=productName&q=demo
        <li>state : {location.state}</li>       // 
        <li>key : {location.key}</li>           // default
    </ul>
  );
}
```
## useSearchParams
 Query String 을 state 처럼 쓸 수 있게 해준다
 ```js
 const [searchParams, setSearchParams] = useSearchParams();
```

### searchParams 사용

http://localhost:3000/Edit?id=10&mode=dark

```js
const Product = () => {
  const [searchParams, setSearchParams] = useSearchParams();

  const id = searchParams.get('id');      // 10
  const mode = searchParams.get('mode');  // dark
};
```
### setSearchParams 사용
```
<button onClick={() => setSearchParams({ who: "hhhh" })}>Query String 바꾸기</button> // http://localhost:3000/Edit?who=hhhh
```

## useNavigate
Link 컴포넌트를 사용하지 않고 다른 페이지로 이동을 해야 하는 경우나 뒤로가기 등에 사용한다

ex)
```js
const Product = () => {
  const navigate = useNavigate();
  return (
  <ul>
    <li><button onClick={() => navigate(-2)}>두페이지 전</button></li>
    <li><button onClick={() => navigate(-1)}>한페이지 전</button></li>
    <li><button onClick={() => navigate(1)}>한페이지 앞</button></li>
    <li><button onClick={() => navigate(2)}>두페이지 앞</button></li>
    <li><button onClick={() => navigate('/')}'/' 경로</button></li>
    <li><button onClick={() => navigate('/hello',{replace: true})}>'hello' 경로(replace : 페이지이동할떄 히스토리 여부)</button></li>
  </ul>
  );
}
```
