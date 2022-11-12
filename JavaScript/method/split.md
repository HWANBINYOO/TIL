# split

문자열을 배열로 분할하는 메서드이다


## 형식
```js
string.split( separator, limit )
```

## separator(분리기호) 활용

```js
let str = "aa/bb/cc/dd/ee";  
 
arr1 = str.split("");  // ["a", "a", "/", "b", "b", "/", "c", "c", "/", "d", "d", "/", "e", "e"]
 
arr2 = str.split("/"); // ["aa", "bb", "cc", "dd", "ee"]  
 
arr3 = str.split("/", 2);  //  ["aa", "bb"]
```
