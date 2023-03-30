# FLUX
## FLUX 패턴?
2014년 페이스북 F8 컨퍼런스에서 발표된 아키텍처로, Client-Side 웹 애플리케이션을 만들기 위해 사용하는 디자인 패턴
MVC와 다르게 단방향으로 데이터가 흐른다.
Action → Dispatcher (콜백으로 함수전달) → Store → View
 

## Flux  4가지 구성요소
![image](https://user-images.githubusercontent.com/80516736/228844557-74583e8c-2645-44f2-99d0-51750cb9ccd1.png)

### Action
Dispatcher에서 콜백 함수가 실행 되면 Store가 업데이트 되게 되는데, 이 콜백 함수를 실행할 때 데이터가 담겨 있는 객체가 인수로 전달되어야 한다. 이 객체를 Action이라고 하는데, 대체로 Action 생성자(Action Creator)에서 만들어진다. Action creator는 새로 발생한 Action의 타입(type)과 새로운 데이터(payload)를 묶어 Dispatcher에게 전달한다.

 

### Dispatcher
Dispatcher는 Flux의 모든 데이터 흐름을 관리하는 허브 역할을 한다. Action이 발생되면 Dispatcher로 전달되는데, Dispatcher는 전달된 Action을 보고 등록된 콜백 함수를 실행하여 Store에 데이터를 전달한다. Dispatcher는 전체 어플리케이션에서 한 개의 인스턴스만 사용된다.

### Store
어플리케이션의 모든 상태 변경은 Store에 의해 결정이 된다. Store가 변경되면 View에 변경되었다는 사실을 알려준다. Store 또한 Dispatcher 처럼 싱글톤이다.

### View
Flux의 View는 화면에 나타내는 것 뿐만 아니라, 자식 View로 데이터를 흘려 보내는 뷰 컨트롤러의 역할도 한다.

 

## 참고

https://haruair.github.io/flux/docs/overview.html

https://github.com/d-virusss/interview_frontend/blob/main/docs/Redux%20%EC%99%80%20Flux%20%ED%8C%A8%ED%84%B4.md

https://velog.io/@andy0011/Flux-%ED%8C%A8%ED%84%B4%EC%9D%B4%EB%9E%80
