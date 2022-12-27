# DOM

DOM은 Document Object Model(문서 객체 모델) 의 약자로 HTML문서를 브라우저가 이해할 수 있도록 만든 Tree 자료구조이다

<img width="718" alt="image" src="https://user-images.githubusercontent.com/82823150/209622434-962a4f3a-3384-4509-973a-4fc322ed93f3.png">

## DOM 조작하기

### 요소찾기

```js
document.getElementById("아이디") //요소 ID로 요소 찾기
document.getElementByTagName("태그 이름") //태그 이름으로 요소 찾기
document.getElementByClassName("클래스 이름") //클래스 이름으로 요소 찾기
document.querySelectorAll("선택자") //CSS 선택자 전부 찾기
document.querySelector("선택자") //CSS 선택자 중 첫 번째 하나만 찾기
```

### 요소 조회

선택한 DOM 요소를 조회할 수 있는 속성으로 두 가지가 있다


```js
const content = document.getElementsByTagName('p')[0];

content.textContent; // 선택한 요소의 HTML 요소를 제거한 순수한 텍스트 데이터의 값 ex) HTML
content.innerHTML; // 선택한 요소의 HTML 태그를 그대로 제공하여 보안에 취약 ex) <b>HTML</b>
```

### 요소 수정

선택한 요소를 수정할 때는 새로운 값을 조회한 그대로 할당하면 된다

```js
content.textContent = "HTML 수정";
content.innerHTML = "<i>HTML</i> 수정";
```

### 요소 생성 및 추가

createElement를 사용하여 새로운 요소를 만든다

```js
const p1 = document.createElement('p');
const p2 = document.createElement('p');
p1.textContent = "foo";
p2.textContent = "bar";
```
이렇게 만들어진 요소는 메모리에만 존재하기 때문에 메소드를 생성하여 DOM에 추가해야 한다

```js
const parent = document.getElementById("parent");

// 요소를 부모 요소의 자식 요소로 추가 
parent.appendChild(p2);

const firstChild = parent.childNodes[0];
parent.insertBefore(p1, firstChild); // 삽입할 자식 요소, 삽입할 위치
```

createTextNode를 사용하여 텍스트 노드를 추가할 수도 있다

```js
// ul 태그 아래에 새로운 li 요소를 생성하기
let textToAdd = document.createTextNode("추가할 텍스트");
let liToAdd = document.createElement("li");
listToAdd.appendChild(textToAdd);

let ulContainer = document.getElementsByTagName("ul")[0];
ulContainer.appendChild(listToAdd);
```

### 요소 삭제
```js
// ul 태그 아래에 존재하는 두 번째 li 요소를 삭제
let itemToRemove = document.getElementsByTagName("li")[1];
let ulContainer = document.getElementsByTagName("ul")[0];
ulContainer.removeChild(itemToRemove);
```

### 요소 교체

Node.replaceChild() 메소드는 특정 부모 노드의 한 자식 노드를 다른 노드로 교체한다

```js
// <div>
//  <span id="childSpan">foo bar</span>
// </div>

let sp1 = document.createElement("span");
sp1.id = "newSpan";

let sp1_content = document.createTextNode("컨텐츠 생성");
sp1.appendChild(sp1_content);

// 교체돼야 할 노드를 찾기
let sp2 = document.getElementById("childSpan");
let parentDiv = sp2.parentNode;

// 노드교체
parentDiv.replaceChild(sp1, sp2);

// 결과:
// <div>
//   <span id="newSpan">new replacement span element.</span>
// </div>
```
