# 타입 별칭

 특정 타입이나 인터페이스를 참조할 수 있는 타입 변수를 의미한다
 
 ## 예시
 
 ```js
 // string 타입을 사용할 때
const name: string = 'capt';

// 타입 별칭을 사용할 때
type MyName = string;
const name: MyName = 'capt';
```
```
type Developer = {
  name: string;
  skill: string;
}

제네릭 o
type User<T> = {
  name: T
}
```

## 타입 별칭의 특징
타입 별칭은 새로운 타입 값을 하나 생성하는 것보단 타입에 대해 나중에 쉽게 참고할 수 있는 이름을 부여하는 것과 같다


## type vs interface

### 확장하는 방법(상속)

interface는 extends로 확장한다
```js
interface AnimalInterface {
  species: string
  height: number
}

interface AfricaAnimal extends AnimalInterface {
  continent: string
}
```

type은 특수문자&로 확장한다
```js
type AnimalType = {
  species: string,
  height: number,
}
type AfricaAnimal = AnimalInterface & {
  continent: string
}
```
## 선언적 확장
type은 새로운 속성을 추가하기 위해서 다시 같은 이름으로 선언할 수 없지만, interface는 항상 선언적 확장이 가능하다

```js
interface Animal {
  weight: number;
}

interface Animal {
  height: number;
}

const tiger: Animal = {
  weight: 100,
  height: 200,
};
console.log(tiger);

type _Animal = {
  weight: number;
};

type _Animal = {//error : 식별자가 중복됨
  height: string;
};
```



