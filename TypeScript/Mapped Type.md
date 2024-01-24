## 맵드 타입(Mapped Type)

맵드 타입이란 기존에 정의되어 있는 타입을 새로운 타입으로 변환해 주는 문법을 의미한다.

주로 기존 interface의 모든 속성을 Optional 속성 또는 ReadOnly 로 만들 때 사용한다.


## 기본 문법
```ts
{ [ P in K ] : T }
{ [ P in K ]? : T }
{ readonly [ P in K ] : T }
{ readonly [ P in K ]? : T }
```


## 기본 예제
아래와 같이 헐크, 토르, 캡틴을 유니온 타입으로 묶어주는 Heroes라는 타입이 있다.
```ts
type Heroes = 'Hulk' | 'Thor' | 'Capt';
```
여기서 이 세 영웅의 이름에 각각 나이까지 붙인 객체를 만들고 싶다고 한다면 아래와 같이 변환할 수 있습니다.
```ts
type HeroProfiles = { [K in Heroes]: number };
const heroInfo: HeroProfiles = {
  Hulk: 54,
  Thor: 1000,
  Capt: 33,
}
```
그러면 HeroProfiles의 타입은 아래와 같이 정의됩니다.
```ts
type HeroProfiles = {
  Hulk: number;
  Thor: number;
  Capt: number;
}
```

## 실용예제 1
실제로 서비스를 개발할 때는 위와 같은 코드보다는 아래와 같은 코드를 더 많이 사용하게 된다.
```ts
type Subset<T> = {
  [K in keyof T]?: T[K];
}
```

위 코드는 키와 값이 있는 객체를 정의하는 타입을 받아 그 객체의 부분 집합을 만족하는 타입으로 변환해주는 문법이다. 예를 들면 만약 아래와 같은 인터페이스가 있다고 할 때

```ts
interface Person {
  age: number;
  name: string;
}
```
위 Subset 타입을 적용하면 아래와 같은 객체를 모두 정의할 수 있다.

```ts
const ageOnly: Subset<Person> = { age: 23 };
const nameOnly: Subset<Person> = { name: 'Tony' };
const ironman: Subset<Person> = { age: 23, name: 'Tony' };
const empty: Subset<Person> = {};
```

## 실용 예제 2
아래와 같이 사용자 프로필을 조회하는 API 함수가 있다고 했을 때 
```ts
interface UserProfileUpdate {
  username?: string;
  email?: string;
  profilePhotoUrl?: string;
}

function updateUserProfile(params: UserProfileUpdate) {
  // ...
}
```

아래와 같이 동일한 타입에 대해서 반복해서 선언하는 것을 피해야 한다.

```ts
interface UserProfile {
  username: string;
  email: string;
  profilePhotoUrl: string;
}

interface UserProfileUpdate {
  username?: string;
  email?: string;
  profilePhotoUrl?: string;
}
```
위의 인터페이스에서 반복되는 구조를 다음과 같이 줄일 수 있다.
```ts

type UserProfileUpdate = {
  username?: UserProfile['username'];
  email?: UserProfile['email'];
  profilePhotoUrl?: UserProfile['profilePhotoUrl'];
}

type UserProfileUpdate = {
  [p in 'username' | 'email' | 'profilePhotoUrl']?: UserProfile[p]
}

type UserProfileUpdate = {
  [p in keyof UserProfile]?: UserProfile[p]
}
```












