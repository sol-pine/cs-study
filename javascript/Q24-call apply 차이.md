# call apply 차이

# Function.prototype.call()
call() 메소드는 주어진 this 값 및 각각 전달된 인수와 함께 함수를 호출합니다.
```
func.call(thisArg[, arg1[, arg2[, ...]]])
```
- thisArg: func 호출에 제공되는 this의 값
- arg1, arg2, ...: func이 호출되어야 하는 인수

# Function.prototype.apply()
apply() 메서드는 주어진 this 값과 배열 (또는 유사 배열 객체) 로 제공되는 arguments 로 함수를 호출합니다.
```
fun.apply(thisArg, [argsArray])
```
- thisArg: func 호출에 제공되는 this의 값
- argsArray: func이 호출되어야 하는 인수를 지정하는 유사 배열 객체

### 참고
https://velog.io/@josworks27/%ED%95%A8%EC%88%98%ED%98%B8%EC%B6%9C-call-apply-bind-%EC%B0%A8%EC%9D%B4

https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/call https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Function/apply
