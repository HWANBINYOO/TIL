# 유틸리티 타입
유틸리티 타입은 이미 정의해 놓은 타입을 변환할 때 사용하기 좋은 타입 문법이다

인터페이스, 제네릭 등으로 타입을 변환할 수 있지만 유틸리티 타입을 쓰면 훨씬 더 간결한 문법으로 타입을 정의할 수 있다

## Partial\<T\>
특정 타입의 부분 집합을 만족하는 타입을 정의할 수 있다
```js
interface Address {
  email: string;
  address: string;
}

type MayHaveEmail = Partial<Address>;
const me: MayHaveEmail = {}; // 가능
const you: MayHaveEmail = { email: 'test@abc.com' }; // 가능
const all: MayHaveEmail = { email: 'capt@hero.com', address: 'Pangyo' }; // 가능
```

## Pick<T, K>
T 타입으로부터 K 프로퍼티만 추출한다
```js
interface Hero {
  name: string;
  skill: string;
}
const human: Pick<Hero, 'name'> = {
  name: '스킬이 없는 사람',
};
```
```js
type HasThen<T> = Pick<Promise<T>, 'then' | 'catch'>;
let hasThen: HasThen<number> = Promise.resolve(4);
hasThen.th // 위에서 'then'만 선택하면 'then'만 제공, 'catch' 선택하면 'catch만 제공'
```

## Omit<T, K>
T 타입으로부터 K 프로퍼티를 제거한 타입을 구성한다(Pick 타입과 반대)
```js
interface AddressBook {
  name: string;
  phone: number;
  address: string;
  company: string;
}
const phoneBook: Omit<AddressBook, 'address'> = {
  name: '재택근무',
  phone: 12342223333,
  company: '내 방'
}
const chingtao: Omit<AddressBook, 'address'|'company'> = {
  name: '중국집',
  phone: 44455557777
}
```

## Record<K, T>
두 개의 제네릭 타입을 받을 수 있다

K는 key 값의 타입으로, 두번째 제네릭 타입 T은 값의 타입으로 갖는 타입을 리턴한다.
```js
type IFieldValue = {
  name: string;
  value: number;
};

type IFormName = 'event' | 'point';

const x: Record<IFormName, IFieldValue> = {
  event: {
    name: 'foo',
    value: 0,
  },
  point: {
    name: 'foo',
    value: 30,
  }
}
```


## Readonly\<T\>
Type의 모든 속성을 읽기 전용(readonly)로 설정한 타입을 구성한다
```js
interface User {
    name: string;
}

const userA: Readonly<User> = {
    name: "Jongmin",
};
userA.name = "Minjong"; //error
```


