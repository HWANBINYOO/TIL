# 적응형 웹(Adaptive Web)

특정 뷰포트의 크기에 맞게끔 설계된 웹 페이지를 만든다

서버나 클라이언트에서 웹에 접근한 기기를 체크해 그 기기에 맞는 템플릿을 제공하는 개념이다(HTTP GET 요청의 user-agent 헤더 정보)

ex. 스마트폰으로 네이버에 접속할 경우 m.naver.com로 리디렉션 시킨다


## vs 반응형

반응형에 반해 사용자의 기기에 맞는 템플릿 및 CSS만 다운로드 하므로 데이터 낭비가 적고 로딩 속도가 빠르다

하지만 , 각 기기별로 별로의 템플릿을 작성해야 하므로 개발이 복잡해진다

![image](https://user-images.githubusercontent.com/82823150/202624682-bec59cd2-0484-4365-926d-69b527377811.png)

![image](https://user-images.githubusercontent.com/82823150/202625106-08d35ad8-566e-4ffd-8e20-09160a5faee5.png)
