# 객체
키(key)과 값(value)으로 구성된 프로퍼티(Property)들의 집합이다

### 프로퍼티
프로퍼티는 프로퍼티 키(이름)와 프로퍼티 값으로 구성된다

프로퍼티는 프로퍼티 키로 유일하게 식별할 수 있다
![image](https://user-images.githubusercontent.com/82823150/199744419-548fdc6c-100d-4e07-878d-a34e9d2fef55.png)


 ## 객체 생성 방법
 
### 객체 리터럴
중괄호({})를 사용하여 객체를 생성하는한다

```js
var person = {
  name: 'Lee',
  gender: 'male',
  sayHello: function () {
    console.log('Hi! My name is ' + this.name);
  }
};
```
### 생성자 함수
생성자 함수를 사용하면 마치 객체를 생성하기 위한 템플릿(클래스)처럼 사용하여 프로퍼티가 동일한 객체 여러 개를 간편하게 생성할 수 있다

```js
// 생성자 함수
function Person(name, gender) {
  this.name = name;
  this.gender = gender;
}

// 인스턴스의 생성
var person1 = new Person('Lee', 'male');
var person2 = new Person('Kim', 'female');
```
### Object 생성자 함수

## 객체 프로퍼티 접근

### 프로퍼티 키

 프로퍼티 키는 문자열이므로 따옴표(‘’ 또는 ““)를 사용하지만  유효한 이름인경우  따옴표를 생략할 수 있다
 ```js
 var person = {
  'first-name': 'Ung-mo',
  gender: 'male',
};
```
### 프로퍼티 값 읽기
객체의 프로퍼티 값에 접근하는 방법은 마침표(.) 표기법과 대괄호([]) 표기법이 있다
```js
var person = {
  'first-name': 'Ung-mo',
  gender: 'male',
};
console.log(person['gender']); // 'male'
console.log(person.gender); // 'male'
console.log(person.age); // undefined
```
대괄호([]) 표기법을 사용하는 경우, 대괄호 내에 들어가는 프로퍼티 이름은 반드시 `문자열`이어야 한다
객체에 존재하지 않는 프로퍼티를 참조하면 undefined를 반환한다.


### 프로퍼티 값 갱신
객체가 소유하고 있는 프로퍼티에 새로운 값을 할당하면 프로퍼티 값은 갱신된다.
```js
var person = {
  'first-name': 'Ung-mo',
};

person['first-name'] = 'Kim';
console.log(person['first-name'] ); // 'Kim'
```
### 프로퍼티 동적 생성
객체가 소유하고 있지 않은 프로퍼티 키에 값을 할당하면 하면 주어진 키와 값으로 프로퍼티를 생성하여 객체에 추가한다.
```js
var person = {
  'first-name': 'Ung-mo',
};

person.age = 20;
console.log(person.age); // 20
```

### 프로퍼티 삭제
`delete` 연산자를 사용하면 객체의 프로퍼티를 삭제할 수 있다. 이때 피연산자는 `프로퍼티 키`이어야 한다.
```js
var person = {
  'first-name': 'Ung-mo',
};

delete person.first-name;
console.log(person.gender); // undefined
```




