# transform
 - 요소에 이동(translate), 회전(rotate), 확대축소(scale), 비틀기(skew) 효과를 부여하기 위한 함수를 제공하는 속성이다
 - 좌표공간을 변형함으로써, 다른 엘리먼트에 영향을 미치지 않고 특정 엘리먼트의 위치를 바꿀 수 있다
 
 ## 2D transform 
  <table>
  <thead>
    <tr>
      <th style="text-align: left">transform function</th>
      <th style="text-align: left">설명</th>
      <th style="text-align: center">단위</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: left">translate(x,y)</td>
      <td style="text-align: left">요소의 위치를 X축으로 x만큼, Y축으로 y만큼 이동시킨다.</td>
      <td style="text-align: center">px, %, em 등</td>
    </tr>
    <tr>
      <td style="text-align: left">translateX or Y(n)</td>
      <td style="text-align: left">요소의 위치를 (X,Y)축으로 n만큼 이동시킨다.</td>
      <td style="text-align: center">px, %, em 등</td>
    </tr>
    <tr>
      <td style="text-align: left">scale(x,y)</td>
      <td style="text-align: left">요소의 크기를 X축으로 x배, Y축으로 y배 확대 또는 축소 시킨다.</td>
      <td style="text-align: center">0과 양수</td>
    </tr>
    <tr>
      <td style="text-align: left">scaleX or Y(n)</td>
      <td style="text-align: left">요소의 크기를 X축으로 n배 확대 또는 축소 시킨다.</td>
      <td style="text-align: center">0과 양수</td>
    </tr>
    <tr>
      <td style="text-align: left">skew(x-angle,y-angle)</td>
      <td style="text-align: left">요소를 X축으로 x 각도만큼, Y축으로 y 각도만큼 기울인다.</td>
      <td style="text-align: center">+/- 각도(deg)</td>
    </tr>
    <tr>
      <td style="text-align: left">skewX or Y(x-angle)</td>
      <td style="text-align: left">요소를 (X ,Y)축으로 x 각도만큼 기울인다.</td>
      <td style="text-align: center">+/- 각도(deg)</td>
    </tr>
    <tr>
      <td style="text-align: left">rotate(angle)</td>
      <td style="text-align: left">요소를 angle만큼 회전시킨다.</td>
      <td style="text-align: center">+/- 각도(deg)</td>
    </tr>
  </tbody>
</table>

## 3D transform
  <table>
  <thead>
    <tr>
      <th style="text-align: left">transform function</th>
      <th style="text-align: left">설명</th>
      <th style="text-align: center">단위</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align: left">translate3d(x,y,z)</td>
      <td style="text-align: left">요소의 위치를 X축으로 x만큼, Y축으로 y만큼 Z축으로 z만큼 이동시킨다.</td>
      <td style="text-align: center">px, %, em 등</td>
    </tr>
    <tr>
      <td style="text-align: left">translateX or Y or Z(n)</td>
      <td style="text-align: left">요소의 위치를 (X ,Y ,Z)축으로 n만큼 이동시킨다.</td>
      <td style="text-align: center">px, %, em 등</td>
    </tr>
    <tr>
      <td style="text-align: left">scale3d(x,y)</td>
      <td style="text-align: left">요소의 크기를 X축으로 x배, Y축으로 y배, Z축으로 z배 확대 또는 축소 시킨다.</td>
      <td style="text-align: center">0과 양수</td>
    </tr>
    <tr>
      <td style="text-align: left">scaleX or Y or Z(n)</td>
      <td style="text-align: left">요소의 크기를 (X or Y or Z)축으로 n배 확대 또는 축소 시킨다.</td>
      <td style="text-align: center">0과 양수</td>
    </tr>
    <tr>
      <td style="text-align: left">rotate3d(x,y,z)</td>
      <td style="text-align: left">요소를 X축으로 x각도, Y축으로 y각도, Z축으로 z각도 회전시킨다.</td>
      <td style="text-align: center">+/- 각도(deg)</td>
    </tr>
    <tr>
      <td style="text-align: left">rotateX or Y or Z(n)</td>
      <td style="text-align: left">요소를 (X , Y , Z)축으로 n각도 회전시킨다.</td>
      <td style="text-align: center">+/- 각도(deg)</td>
    </tr>
  </tbody>
</table>






