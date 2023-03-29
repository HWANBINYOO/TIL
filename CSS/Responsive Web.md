# 반응형웹(Responsive Web)

디바이스의 종류에 따라 웹페이지의 크기가 자동적으로 재조명 되는 것을 말한다

## 미디어 쿼리(Media Query)
단말기 종류에 따라 각각 다른 스타일을 적용시키게해준다

### 미디어 쿼리 문법

![image](https://user-images.githubusercontent.com/82823150/202606932-9d8fb90f-2b17-409f-8f68-40f275a06947.png)

#### only | not
only 키워드는 뒤에있는 조건만 , not 키워드는 뒤에 조건을 제외한 조건을 뜻한다

#### 미디어타입

all : 모든 미디어 타입

print : 인쇄용도

screen : 컴퓨터 스크린

#### 속성

width , height : 웹페이지 가로,세로 길이

min-width , min-height : 웹페이지 최소 가로,세로 길이

max-width , max-height : 웹페이지 최대 가로,세로 길이

ex)
```css
span {
  font-size: 18px;
  @media (max-width: 1920px) {
    font-size: 16px;
  }
  @media (max-width: 1400px) {
    font-size: 13px;
  }
  @media (max-width: 700px) {
    font-size: 5px;
  }
}
```

## 유동형 그리드(Fluid Grid)

그리드의 폭을 고정값(px) 이 아닌 em 또는 %값으로 설정해 웹의 가로길이에 따라 div의 width값이 바뀌는기법이다

하지만 가로 폭에 반응을하는데 레이아웃에는 변화가없어 폭이 많이 좁은 모바일에는 큰 효과를 볼 수 없다

![image](https://user-images.githubusercontent.com/82823150/202608288-55ca9d4f-e0c4-4748-98d8-a2b41067d88b.png)

## 유동형 레이아웃(Liquid Layouts)

레이아웃 크기를 상대적 단위로 지정해 웹의 크기에 유동적으로 변화를 주고 , 미디어 쿼리를 사용해 일정크기가 되면 레이아웃구조를 바꿔주는 방법이다

![image](https://user-images.githubusercontent.com/82823150/202610121-5bb77c22-e21f-495a-9d28-06f9b2b90997.png)

### Mostly Fluid

가장 작은 화면에서만 수직으로 컬럼을 세우는 구조를 가지는 패턴이다

<img width="532" alt="image" src="https://user-images.githubusercontent.com/82823150/228539911-8d2ef192-9483-4e33-859e-0b8e306e7525.png">

### Column Drop

화면이 작아짐에 따라 컬럼폭의 변화 대신 컬럼을 아래로 떨어뜨리는 방법을 쓰는 패턴이다

![image](https://user-images.githubusercontent.com/82823150/202620050-67fcf0c5-9816-4863-8604-f912b497bb05.png)

### Laout Shifter 

화면이 작아짐에 따라 각기다른 레이아웃을 보여주는 패턴여서 많은 작업이 필요하지만 혁신적인 디자인을 담을 수 있다

![image](https://user-images.githubusercontent.com/82823150/202624286-6dad9792-1bb5-4996-ba9b-1a70db306d28.png)

### Tiny Tweaks 

하나의 컬럼을 사용하는 패턴으로 주로 글 내용을 중시하는 웹에서 많이쓰인다

![image](https://user-images.githubusercontent.com/82823150/202621700-66162ec6-e42e-48b4-9049-d405847cd243.png)


### off Canvas

큰 화면에서는 모든 컬럼들을 보여주고 작은화면은 다른 부가적인 컬럼들을 화면 밖에 숨겨놓은 패턴이다

숨겨져 있는 다른컬럼은 필요할 때만 접근 하도록 한다

![image](https://user-images.githubusercontent.com/82823150/202622880-a061d8bc-5c37-43eb-8ab8-aa03d1884f05.png)





