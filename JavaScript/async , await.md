# async 와 await

async/await 키워드를 사용하면 비동기 코드를 마치 동기 코드처럼 보이게 작성할 수 있다

## Promise를 통한 비동기 코딩의 문제점

```js
function fetchAuthorName(postId) {
  return fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`)
    .then((response) => response.json())
    .then((post) => post.userId)
    .then((userId) => {
      return fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
        .then((response) => response.json())
        .then((user) => user.name);
    });
}

fetchAuthorName(1).then((name) => console.log("name:", name)); // name: Leanne Graham
```
### 예외 처리
예외 처리를 try/catch 대신에 catch() 메서드를 사용한다 

만약 동기 코드와 비동기 코드가 섞여 있을 경우 예외 처리가 난해해지거나 예외 처리를 누락하는 경우가 생기기 쉽다

### 들여쓰기

실제 프로젝트에서는 샘플 코드와 같이 간단한 구조가 아닌 복잡한 구조의 비동기 처리 코드를 작성하게 된다

따라서, then() 메서드의 인자로 넘기는 콜백 함수 내에서 조건문이나 반복문을 사용하거나 
여러 개의 Promise를 병렬로 또는 중첩해서 호출해야하는 경우들을 다단계 들여쓰기를 해야할 경우에 코드 가독성은 점점 떨어지게 된다


## async 와 await 사용법
function 앞에는 async 을 붙이고 await 는 async 키워드가 붙어있는 함수 내부에서만 사용할 수 있다

await 키워드를 사용하면 일반 비동기 처리처럼 바로 실행이 다음 라인으로 넘어가는 것이 아니라 결과값을 얻을 수 있을 때까지 기다려준다

```js
async function fetchAuthorName(postId) {
  const postResponse = await fetch(
    `https://jsonplaceholder.typicode.com/posts/${postId}`
  );
  const post = await postResponse.json();
  const userId = post.userId;
  const userResponse = await fetch(
    `https://jsonplaceholder.typicode.com/users/${userId}`
  );
  const user = await userResponse.json();
  return user.name;
}

fetchAuthorName(1).then((name) => console.log("name:", name));
```

## 예외 처리

동기/비동기 구분없이 try/catch로 일관되게 예외 처리를 할 수 있는 부분도 async/await를 사용해서 코딩했을 때의 큰 이점 중 하나다

```js
async function fetchAuthorName(postId) {
  const postResponse = await fetch(
    `https://jsonplaceholder.typicode.com/posts/${postId}`
  );
  const post = await postResponse.json();
  const userId = post.userId;

  try {
    const userResponse = await fetch(
      `https://jsonplaceholder.typicode.com/users/${userId}`
    );
    const user = await userResponse.json();
    return user.name;
  } catch (err) {
    console.log("Faile to fetch user:", err);
    return "Unknown";
  }
}

fetchAuthorName(1).then((name) => console.log("name:", name));
```










