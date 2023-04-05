# use strict

## use strict?
- 암묵적인 sloppy mode(non-stric mode)를 해제하고 명시적인 Strict Mode를 사용하는 방법
- 이 문구는 ES5부터 적용되는 키워드로, 안전한 코딩을 위한 하나의 가이드라인

## Stric mode
- Strict Mode는 코드에 더 나은 오류 검사를 적용하는 방법이다.
- ES6에서는 디폴트가 Strict Mode이기 때문에 사용할 필요가 없다.
- 코드 맨 앞(해당 스코프의 시작)에 use strict 행을 쓰면 사용할 수 있다.
- 블록 스코프 내부에서 사용할 수 없다. (함수에는 사용가능)

```
// Whole-script strict mode syntax
"use strict";
const v = "Hi! I'm a strict mode script!";
```
```
function myStrictFunction() {
  // Function-level strict mode syntax
  "use strict";
  function nested() {
    return "And so am I!";
  }
  return `Hi! I'm a strict mode function! ${nested()}`;
}
function myNotStrictFunction() {
  return "I'm not strict.";
}

```
- 모듈은 자동으로 stric mode이기 때문에 use stric을 사용할 필요가 없다.
- 클래스 본문의 모든 부분은 클래스 선언과 클래스 표현식을 포함하여 stric mode이다.
- 실수로 전역변수 생성이 불가능하다. 기존엔 변수를 잘못입력하면 전역 객체에 새 속성이 생성되고 작동되나 stric 모드에서는 오류가 발생된다.
- 쓰기 불가능한 데이터 속성에 할당시 오류가 발생한다. ( NaN, undefined, Infinity...)
- getter 전용 접근자 속성에 할당시 오류가 발생한다.
- 확장 불가능한 개체의 새 속성에 할당시 오류가 발생한다.
- 삭제할수 없는 속성이나 이름을 삭제하려할때 오류가 발생한다.
- 함수 매개변수 이름에 중복을 허용하지 않는다.
- 접두사가 0인 8진수 escape sequence를 허용하지 않는다. 대신에 0o prefix를 사용한다.
- primitive value(객체가 아닌 메소드나 속성이 없는데이터, string/number/boolean...)에 속성 설정을 금지한다.
- 중복 속성이름을 허용하지 않는다.
- with를 금지한다.
- eval()호출된 범위에서 변수를 생성할 수 없다.
- stric mode함수에서 this를 지정하지 않는경우 undefined이다. globalthis로 대체되지 않는다.

## Stric mode를 사용하는 이유
- 이전에 허용된 '잘못된 구문'을 실제 오류로 변경한다
- JavaScript 엔진의 최적화 처리를 어렵게 만드는 오류를 수정하여 빠르게 실행 될 수 있도록 한다.
- 향후 버전용으로 예약된 키워드는 변수 이름으로 사용할 수 없다. (implements, let, yield, static....)
 

## 참고
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode

https://ithub.tistory.com/162

https://stackoverflow.com/questions/31685262/not-recommended-to-use-use-strict-in-es6

https://www.w3schools.com/js/js_strict.asp
