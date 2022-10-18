# position

position에 은 `HTML 문서 상에서 요소가 배치되는 방식을 결정`한다

## static
position 속성을 별도로 지정해주지 않으면 기본값인 static이 적용된다
top, left, bottom, right 속성값은 무시된다

## relative
요소를 원래 위치를 기준으로 `상대적(relative)`으로 배치해준다

## absolute
부모 요소가 relative 인 요소를 기준으로 배치된다
부모 요소에 relative 요소가 없다면 body태그를(브라우저 상단, 왼쪽 0, 0 값)기준으로 위치 값이 변경된다

## fixed
요소를 항상 `고정된(fixed)` 위치에 배치해준다

## sticky
relative처럼 작동하다가, 스크롤 시 설정된 top, left 값 위치 도달시 거기에 고정합니다.right, bottom 속성값은 적용이안된다
