# 나머지 매개변수

함수가 정해지지 않은 수의 매개변수를 배열로 받을 수 있다

JavaScript에서 가변항 함수를 표현할 때 사용한다

## 객체에서의 rest

```js
const purpleCuteSlime = { name: '슬라임', attribute: 'cute', color: 'purple'};

const { color, ...rest } = purpleCuteSlime;
console.log(color); // purple
console.log(rest);  // { name: '슬라임', attribute: 'cute'}
```
추출한 값의 이름이 꼭 rest 일 필요는 없다
```js
const purpleCuteSlime = { name: '슬라임', attribute: 'cute', color: 'purple'};

const { color, ...cuteSlime  } = purpleCuteSlime;
console.log(color); // purple
console.log(cuteSlime);  // { name: '슬라임', attribute: 'cute'}
```

## 배열에서의 rest

배열 비구조화 할당을 통하여 원하는 값을 밖으로 꺼내고, 나머지 값을 rest 안에 넣었다
```js
const numbers = [0, 1, 2, 3, 4, 5, 6];

const [one, ...rest] = numbers;

console.log(one);   // 0
console.log(rest);  // [1, 2, 3, 4, 5, 6]
```
## 함수 파라미터에서의 rest

함수의 파라미터가 몇개가 될 지 모르는 상황에서 rest 파라미터를 사용하면 매우 유용하다
```js
function sum(...rest) {
  console.log(rest) // [1, 2, 3, 4, 5, 6]
  return rest.reduce((acc, current) => acc + current, 0);
}

const numbers = [1, 2, 3, 4, 5, 6];

const result = sum(...numbers);
console.log(result); // 21
```

