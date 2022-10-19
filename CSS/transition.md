# transition
CSS 속성을 변경할 때 애니메이션 속도를 조절하는 속성이다

```css
transition: property timing-function duration delay | initial | inherit
```
- `property` : transition을 적용시킬 속성을 정한다

- `timing-function` :transition의 진행 속도를 조절한다
<img loading="lazy" class="aligncenter size-full wp-image-10943" src="https://www.codingfactory.net/wp-content/uploads/css-transition-timing-function-01.gif" alt="" width="728" height="590">
 
 ```css
 ease(기본값) : cubic-bezier( 0.25, 0.1, 0.25, 1 )
 linear : cubic-bezier( 0, 0, 1, 1 )
 ease-in : cubic-bezier( 0.42, 0, 1, 1 )
 ease-out : cubic-bezier( 0, 0, 0.58, 1 )
 ease-in-out : cubic-bezier( 0.42, 0, 0.58, 1 )
 step-start : steps( 1, start )
 step-end : steps( 1, end )
 ```
 
- `duration` :  transition이 끝날 때까지 걸리는 시간을 정한다

- `delay` : 시작하는 시간을 연기한다

- initial : 기본값이다

- inherit : 부모 요소의 속성값을 상속받는다
