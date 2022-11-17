# 호이스팅

변수,함수 안에 있는 선언들을 모두 끌어올려서 해당 함수 유효 범위의 최상단에 선언하는 것을 말한다

호이스팅은 크게 함수 호이스팅과 변수 호이스팅으로 나뉜다


###  호이스팅 규칙 
선언된 함수는 상단에서 참조, 호출이 가능하다

선언된 `var` 는 상단에서 참조, 할당이 가능하다

선언된 `let` , `const` 는 상단에서 참조, 할당이 불가능하다


## Function Hoisting(함수 호이스팅)
함수 호이스팅은 다른 무엇보다 가장 먼저 이루어지고 선언문에만 해당한다

함수의 선언문은 식별자가 변수 객체에 수집될 때 부가적으로 해당 함수 참조에 대한 초기화까지 자동으로 이루어져서 선언된 함수는 상단에서 참조, 호출이 가능하다

## Variable Hoisting(변수 호이스팅)
변수는 프로그램 내에서 3단계를 거친다

1. 선언 : 파싱 과정에서 변수 객체가 변수에 대한 식별자들을 수집한다
3. 초기화 : 식별자에 메모리를 할당하고 `undefined` 상태를 부여한다
3. 할당 : 변수 안에 직접 값을 넘겨 준다

- `var` 는 호이스팅이 발생하면, 선언과 초기화가 거의 동시에 이루어진다 
 실행 시점의 스코프 최상단에서 해당 변수에 대한 메모리가 살아있기 때문에 선언부 위치에 상관 없이 참조, 할당이 가능하다
 
- `let` , `const` 는 호이스팅이 발생하면, 선언만 이루어지고 실행 시점에서 실질적인 선언부를 만날 때까지 초기화는 이루어지지 않는다
 이 간극만큼 해당 변수에 대한 메모리는 존재하지 않기 때문에 선언부 상단에서 참조, 할당이 불가능하다.

### TDZ(Temporal Dead Zone)
let, const 가 동작하는 과정에서 스코프의 진입지점과 해당 식별자의 실질적 선언부 사이를 일시적 사각지대, TDZ(Temporal Dead Zone) 이라고 한다





