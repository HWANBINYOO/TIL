# 인터페이스

인터페이스는 상호 간에 정의한 약속 혹은 규칙을 의미한다

## 옵션 속성
인터페이스를 사용할 때 인터페이스에 정의되어 있는 속성을 모두 다 꼭 사용하지 않아도 되는것을 옵션 속성이라고 한다
```js
interface 인터페이스_이름 {
  속성?: 타입;
}
```

## 읽기 전용 속성
인터페이스로 객체를 처음 생성할 때만 값을 할당하고 그 이후에는 변경할 수 없는 속성을 의미한다
```js
interface CraftBeer {
  readonly brand: string;
}
//배열을 선언할 때 ReadonlyArray<T> 타입을 사용하면 읽기 전용 배열을 생성할 수 있다
let arr: ReadonlyArray<number> = [1,2,3];
arr.push(4); // error
arr[0] = 100; // error
```

## 함수 타입
```js
interface FactorialInterface {
  (n: number): number;  
}
// 인터페이스를 함수 타입에 설정했기에 별도의 매개변수, 리턴 값 설정을 생략해도 된다
const facto: FactorialInterface = (n) => {
  return n;
};
```
