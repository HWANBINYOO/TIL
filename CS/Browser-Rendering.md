# 브라우저 렌더링

## 동작과정

<img width="836" alt="image" src="https://user-images.githubusercontent.com/82823150/209508993-13047a12-4bc6-40a9-be66-108b04db1931.png">

1. HTML 파일과 CSS 파일을 파싱해서 각각 Tree를 만든다
2. 두 Tree를 결합하여 Rendering Tree를 만든다
3. Rendering Tree에서 각 노드의 위치와 크기를 계산한다
4. 계산된 값을 이용해 각 노드를 화면상의 실제 픽셀로 변환하고, 레이어를 만든다
5. 레이어를 합성하여 실제 화면에 나타낸다

### Reflow(Layout)

화면구조(Layout)가 변경되었을 다시 렌더 트리를 구성하는것

### Repaint(Redraw)
화면에 가시성이 변하지만 레이아웃에 영향을 미치지 않는 요소의 외관을 변경할 때 발생한다

## Reflow와 Repaint가 모두 일어나는 경우

- DOM 노드를 추가, 제거 업데이트하는 경우
- DOM 요소의 위치 변경, 크기 변경 (margin, padding, border, width, height, 등..)
- display : none으로 DOM 요소를 숨기는 경우
- DOM 노드를 이동하거나 애니메이션을 생성하는 경우
- 창 크기를 조정,글꼴 스타일 변경,스타일 시트를 추가하거나 제거하는 경우,DOM을 조작하는 스크립트를 수정하는 경우
- offset, scrollTop, scrollLeft와 같은 계산된 스타일 정보 요청
- 이미지  크기 변경

## Repaint만 일어나는 경우 
- background-color, visibillty, outline 등의 스타일 변경(레이아웃이나 위치 변경이 없음)


