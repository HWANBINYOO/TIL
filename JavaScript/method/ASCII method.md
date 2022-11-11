# ASCII Code 메서드


## 아스키 코드 일부
```js
숫자 : (0)48 ~ (9)57 (10개)
대문자 : (A)65 ~ (Z)90까지 (26개)
소문자 : (a)97 ~ (z)122 (26개)
```

## charCodeAt
문자열의 해당 인덱스 요소를 아스키코드 번호로 변환한 값을 반환한다

```js
console.log('happy'.charCodeAt(2)); // p = 112

// index를 적지 않으면 맨 앞의 문자의 아스키코드를 리턴한다
```

## fromCharCode
아스키코드번호를 받아 문자열로 변환한 값을 반환한다

```js
String.fromCharCode(아스키코드 번호)
console.log(String.fromCharCode(112)); //p
console.log(String.fromCharCode(65, 83, 67, 73, 73)); //ASCII
```
