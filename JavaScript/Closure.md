## 클로저란
클로저는 내부함수가 외부함수의 환경의 지역변수같은 맥락을 기억하고있어서 접근할 수 있는 것을 말한다.

## 클로저장점
1 상태유지: 현재 상태를 기억하고 변경된 최신 상태를 유지할 수 있다.
2 전역변수의 사용억제: 상태변경이나 가변 데이터를 피하고 오류를 피하는 안정성을 증가시킬 수 있다.
3 정보의 은닉: 클래스 기반 언어의 private 키워드를 흉내낼 수 있다.

## 활용예시
 
```js
const click = (() => {
  // 클릭한 횟수를 기억
  let count = 0;
  return () =>  ++count;
})();

console.log(click()); // 1
console.log(click()); // 2
console.log(click()); // 3

```
print 함수 안에 있는 click 함수는 이름이 없는 클로저를 반환하고 호출한다. 클로저는 click 함수의 count변수 값을 계속 기억하고 있으므로 버튼을 누른 횟수를 출력할 수 있다.


또한 전역 변수를 대체하여 클로저를 사용할 수 있어서 **전역 변수의 남용을 막을 수 있고 변수 값을 은닉하는 용도로도 사용할 수 있다.**


```js
let makeCounter = function() {
  let privateCounter = 0;
  function changeBy(val) {
    privateCounter += val;
  }
  return {
    increment: function() {
      changeBy(1);
    },
    decrement: function() {
      changeBy(-1);
    },
    value: function() {
      return privateCounter;
    }
  }
};

let cnt1 = makeCounter();
let cnt2 = makeCounter();
console.log(cnt1.value()); // 0 
cnt1.increment();
cnt1.increment();
console.log(cnt1.value()); // 2
cnt1.decrement();
console.log(cnt1.value()); // 1
console.log(cnt2.value()); // 0
```

각 클로저는 그들 고유의 클로저를 통한 privateCounter 변수의 다른 버전을 참조해서, 각 카운터가 호출될 때마다 하나의 클로저에서 변수 값을 변경해도 다른 클로저의 값에는 영향을 주지 않는다.

## React 에서의 클로저
```js
const [state, setState] = useState(initialValue);
```
useState 의 구조를 보면 **[상태, 상태를 변경하는 함수]** 인데
이전 상태와 현재 상태의 변경을 감지하기 위해서는 함수가 실행되었을 때 이전 상태를 가지고 있어야 한다. 이때 사용되는 것이 클로저이다.


