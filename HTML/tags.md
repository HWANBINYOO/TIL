# tags

## Img 속성
- src 특성은 필수이며, 포함하고자 하는 이미지로의 경로를 지정한다
- alt 속성을 필수는 아니지만 img 태그가 이미지를 로드하지 못하였을 시 보여지는 대체 택스트를 의미하는 속성이다
```html
<img src="주소"  alt="못불러왔네" />
```
  
## Input 속성
- placeholder="" : 아무 값이 없을때 보여주는 text
- maxlength="" : input창에 작성할 수 있는 `문자수를 제한`하기 위한 속성
- minlength="" " input창에 작성할 수 있는 `문자의 최솟값을 제한`하기 위한 속성
- min="" : 입력할 수 있는 수의 `최소값`(숫자|날짜)
- max="" : 입력할 수 있는 수의 `최대값`(숫자|날짜)
- disable : input창을 사용하지 못하게 막아둠
= required : 필수로 입력을 하지 않으면 동작하지 않게 하는 속성
- value : placeholder와 비슷한 속성이지만, value는 그 값을 복사할수 있다
```html
<input type="text" placeholder="input 속성" maxlength="12" minlength="3" required />
```
