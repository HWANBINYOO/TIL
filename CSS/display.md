# display
display 태그는 화면에 어떻게 드러나게 할지를 결정하는 속성이다

## block

- display 속성값이 블록(block)인 요소는 언제나 새로운 라인(line)에서 시작하며, `해당 라인의 모든 너비를 차지`한다
- - width와 height 속성을 지정할 수 있다
```html
<div>, <h1>, <p>, <ul>, <ol>, <form>
```
## inline

- 요소의 너비가 해당 라인 전체가 아닌 해당 HTML `요소의 내용(content)만큼만 차지`한다
```html
<span>, <a>, <img>
```

## inline-block
- inline과 block의 특성을 합쳐놓은 속성이다
- 기본적으로는 inline의 속성을 지니고 있지만(줄바꿈이 되지 않음), 해당 요소 내부에서는 블록(block) 요소처럼 동작한다(크기나 여백을 지정할 수 있음)

## none
- 화면에서 사라진다. 크기 자체도 차지하지 않는다

## flex
- 아이템들을 가로 방향 혹은 세로 방향으로(1차원 배치) 배치할 수 있는 방식이다([여기](https://velog.io/@sukong/WEB-Flexbox-Froggy-%ED%92%80%EC%9D%B4))

## grid
아이템들을 2차원으로 배치하는 방식으로 column과 row의 비율이나 크기를 지정한다

## table
레이아웃을 table로 표현할 수 있는 속성이다


