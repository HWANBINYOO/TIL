# 선택자
CSS 작성할때 HTML의 어떤 요소를 선택할 것 인지 정하는것

## 종류
<table border=1`>
     <tr>
      <td> 이름 </td>
      <td> 예시 </td>
      <td> 설명 </td>
    </tr>
    <tr>
      <td> 전체선택자 </td>
      <td> * {color:blue} </td>
      <td> 모든요소선택 </td>
    </tr>
      <tr>
      <td> id 선택자 </td>
      <td> #hi {color:blue} </td>
      <td> id가 hi인 요소 선택(유일해야 함) </td>
    </tr>
    <tr>
      <td> class 선택자 </td>
      <td> .hi {color:blue} </td>
      <td> class가 hi인 요소모두선택 </td>
    </tr>
    <tr>
      <td> 요소 선택자 </td>
      <td> p {color:blue} </td>
      <td> 태그이름이 p인 모든요소선택 </td>
    </tr>
    <tr>
      <td> 자손 선택자 </td>
      <td> div p {color:blue} </td>
      <td> div 안에 span 태그가 있는 모든요소선택 </td>
    </tr>
    <tr>
      <td> 자식선택자 </td>
      <td> div > p {color:blue} </td>
      <td> 부모가 div 인 태그 안에 span 태그가 있는 모든요소선택 </td>
    </tr>
     <tr>
      <td> 인접선택자 </td>
      <td> div + p {color:blue} </td>
      <td> div 요소바로뒤에 P 태그가 있는 모든요소선택 </td>
    </tr>
     <tr>
      <td> 속성선택자 </td>
      <td> a[href] {color:blue} </td>
      <td> a 태그에 href 속성이 있는 모든 요소 선택 </td>
    </tr>
   <tr>
    <td> 가상선택자 </td>
      <td> a:active {color:blue} </td>
      <td> a 태그 클릭하는 순간 선택 </td>
    </tr>
  </table>
  
  ### 속성 선택자 종류
  <table>
  <tr>
    <td>이름</td>
    <td>설명</td>
  </tr>
  <tr>
    <td>[attribute]</td>
    <td> [href] 경우,  href 속성이 있는 모든 요소 선택</td>
  </tr>
    <tr>
    <td>[attribute=value]</td>
    <td>  [target = _blank]  :  target = "_ blank"인 모든 요소 선택</td>
  </tr>
    <tr>
    <td>[attribute^=value]</td>
    <td> a [href^="https"] 경우,  href 속성값이 "https"로 시작하는 모든 <a> 요소를 선택</td>
  </tr>
  </table>
  
  ### 가상선택자 종류
  <table>
  <tr>
    <td>이름</td>
    <td>설명</td>
  </tr>
  <tr>
    <td> :active </td>
    <td> a:active 경우, <a> 요소 클릭하는 순간 선택 </td>
  </tr>
    <tr>
    <td> ::after </td>
    <td> p::after 경우 , 모든 p 요소의 뒤 부분 선택 </td>
  </tr>
    <tr>
    <td> :checked </td>
    <td> input:checked 경우, checked 속성 갖는 input 요소 선택 </td>
  </tr>
  </tr>
    <tr>
    <td> :first-child </td>
    <td> p:fist-child경우 , 부모의 첫번쨰 자식인 모든 p 요소 선택 </td>
  </tr>
  
  </table>

## 선택자 우선순위
1. !important 
1. 인라인 스타일(style=) 
1. ID선택자(#id) 
1. CLASS 선택자(.class) 
1. 속정 기반 선택자(a[href]) 
1. 가상클래스(a:hover) 
1. 가상요소(span::after) 
1. 태.크 선택자(a) 
1. 전체 선택자(*)




 
