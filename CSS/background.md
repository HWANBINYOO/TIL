# background


## background-color
- 배경 색을 정해준다

## background-image	
- 배경 이미지경로를 설정한다
- 이미지 크기는 늘어나거나 줄어들지 않고 그대로 표시되며,
이미지 보다 컨테이너가 더 크다면 이미지는 반복되어 표시되게 된다

```css
  background-image: url("/images/attach/earth.jpg");
```

## background-repeat
- 배경 이미지의 반복 여부와 반복 방향을 정한다
  - repeat : 가로 방향, 세로 방향으로 반복한다
  > ![image](https://user-images.githubusercontent.com/82823150/196030132-b8e55855-01bc-47c8-95bd-fd29cbd5222a.png)

  - repeat-x : 가로 방향으로 반복한다
  > ![image](https://user-images.githubusercontent.com/82823150/196030230-79f213d6-b0cd-4f74-b0c9-fe145e9899d1.png)
  
  - repeat-y : 세로 방향으로 반복한다
  >![image](https://user-images.githubusercontent.com/82823150/196030242-d4f639f1-d46c-4fdc-a9b9-02d63e7b72f2.png)

  - no-repeat : 반복하지 않는다
  > ![image](https://user-images.githubusercontent.com/82823150/196030249-fe73c69a-c343-4819-8783-c93e085f15b1.png)

  - initial : 기본값으로 설정한다
  - inherit : 부모 요소의 속성값을 상속받는다


## background-position	
- 배경 이미지 위치를 정해준다 
![image](https://user-images.githubusercontent.com/82823150/196030630-ee440b69-4adf-4670-802c-505469b6ad12.png)
- x-position y-position : 가로 위치와 세로 위치를 정한다( left, center, right, 백분율(%), 길이)
- initial, inherit

