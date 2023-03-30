# REST API

## REST란?
- REST는 Representational State Transfer의 약자이다. 

- a way of providing interoperability between computer systems on the Internet.

- interoperablility는 상호 운용성이라는 뜻으로, 컴퓨터 시스템와 인터넷 사이에 상호 운용성을 제공하는 방법이다.

 

## REST의 출현 계기
1991년 www가 팀 버너스 리에 의해 탄생했다. 이때 어떻게 인터넷에서 정보를 공유할 것인가에 대해 고민을 시작한다. 팀 버너스 리는 이에 대한 답으로 정보들을 하이퍼 텍스트로 연결하는 방법을 제시했다. 세부적인 방법으로는 표현 형식은 HTML이며, 식별자는 URI, 전송방법은 HTTP 방식을 제안했다. 그래서 HTTP 프로토콜을 여러 사람들이 설계를 하게 됐고, 그중 로이 필딩이라는 사람도 프로토콜 작업에 참여하게 됬다.  

그 와중에 고민이 생긴다. 로이는 http 1.0 작업에 참여했는데, http를 정립하고 명세에 기능을 더하고 기존의 기능을 고쳐야 하는 상황에 놓이게 된다. 그러나 무작정 http 프로토콜을 고치게 된다면, 기존 구축된 웹 하고 호환이 안 되는 가능성이 존재했다. 이에 로이는 '웹을 망가뜨리지 않고 어떻게 http 기능을 증가시킬 수 있을까?' 고민했다. 고민 끝에 HTTP Object Model(이후에 REST로 발표)이라는 것을 만들고, REST를 최초로 공개한다.

 

##  REST의 제약조건
### 1. Server-Client(서버-클라이언트 구조)

- 자원이 있는 쪽이 Server, 자원을 요청하는 쪽이 Client가 된다.
  - REST Server: API를 제공하고 비즈니스 로직 처리 및 저장을 책임진다.
  - Client: 사용자 인증이나 context(세션, 로그인 정보) 등을 직접 관리하고 책임진다.
- 서로 간 의존성이 줄어든다.
### 2. Stateless(무상태)

- HTTP 프로토콜은 Stateless Protocol이므로 REST 역시 무상태성을 갖는다.
- Client의 context를 Server에 저장하지 않는다.
  - 즉, 세션과 쿠키와 같은 context 정보를 신경쓰지 않아도 되므로 구현이 단순해진다.
- Server는 각각의 요청을 완전히 별개의 것으로 인식하고 처리한다.
  - 각 API 서버는 Client의 요청만을 단순 처리한다.
  - 즉, 이전 요청이 다음 요청의 처리에 연관되어서는 안된다.
  - 물론 이전 요청이 DB를 수정하여 DB에 의해 바뀌는 것은 허용한다.
  - Server의 처리 방식에 일관성을 부여하고 부담이 줄어들며, 서비스의 자유도가 높아진다.
### 3. Cacheable(캐시 처리 가능)

- 웹 표준 HTTP 프로토콜을 그대로 사용하므로 웹에서 사용하는 기존의 인프라를 그대로 활용할 수 있다.
  - 즉, HTTP가 가진 가장 강력한 특징 중 하나인 캐싱 기능을 적용할 수 있다.
  - HTTP 프로토콜 표준에서 사용하는 Last-Modified 태그나 E-Tag를 이용하면 캐싱 구현이 가능하다.
- 대량의 요청을 효율적으로 처리하기 위해 캐시가 요구된다.
- 캐시 사용을 통해 응답시간이 빨라지고 REST Server 트랜잭션이 발생하지 않기 때문에 전체 응답시간, 성능, 서버의 자원 이용률을 향상시킬 수 있다.
### 4. Layered System(계층화)

- Client는 REST API Server만 호출한다.
- REST Server는 다중 계층으로 구성될 수 있다.
  - API Server는 순수 비즈니스 로직을 수행하고 그 앞단에 보안, 로드밸런싱, 암호화, 사용자 인증 등을 추가하여 구조상의 유연성을 줄 수 있다.
  - 또한 로드밸런싱, 공유 캐시 등을 통해 확장성과 보안성을 향상시킬 수 있다.
- PROXY, 게이트웨이 같은 네트워크 기반의 중간 매체를 사용할 수 있다.
### 5. Code-On-Demand(optional)

- Server로부터 스크립트를 받아서 Client에서 실행한다.
- 반드시 충족할 필요는 없다.
### 6. Uniform Interface(인터페이스 일관성)

- URI로 지정한 Resource에 대한 조작을 통일되고 한정적인 인터페이스로 수행한다.
- HTTP 표준 프로토콜에 따르는 모든 플랫폼에서 사용이 가능하다.
  - 특정 언어나 기술에 종속되지 않는다.
 

## REST API
- REST 아키텍쳐 스타일을 따르는 API, 즉 REST의 제약조건을 모두 지켜야 한다.

- 대체로 API는 대부분의 제약조건을 만족시키지만 Uniform interface를 만족시키지 않은 경우가 많다.

 

### Uniform Interface의 제약 조건
#### 1. Identification of resources

- 자원이 url로 식별되면 된다.
#### 2. Manipulation of resources through representations

- Representations(PUT, GET, DELETE ...) 전송을 통해 자원을 조작해야 한다.
  - 즉 리소스를 만들거나 삭제, 수정할 때 http 메시지에 그 표현을 전송해야 된다
#### 3. Self-descriptive messages

- 메시지가 스스로 설명해야 한다. 즉, 메시지만 보고 무슨 뜻을 의미하는지 알아야 한다.
```
HTTP/1.1 200 OK
Content-Type: application/json

[ { "op": "remove", "path": "/a/b/c" } ]
```
위의 코드는 Self-descriptive하지 않다. Content-Type 헤더에서 명시한 application/json으로 대괄호, 중괄호, 따옴표의 의미가 뭔지 알게되어 파싱이 가능하여 문법을 해석 할 수 있으나, op와 path가 무엇을 의미하는지 알수 없다.
```
HTTP/1.1 200 OK
Content-Type: application/json-patch+json

[ { "op": "remove", "path": "/a/b/c" } ]
```
IANA에 op와 path가 무엇을 의미하는지 작성되어 있는 json-patch+json이라는 미디어 타입을 따로 정의하면 완전해진다.
#### 4. Hypermedia as the engine of application state(HATEOAS)

- 애플리케이션의 상태는 HyperLink를 이용해서 전이되어야 한다.
![image](https://user-images.githubusercontent.com/80516736/228841484-4f0d4738-86d7-4bb7-9d81-bb76a7867063.png)
위와 같이 상태를 전이하는 것을 애플리케이션 상태 전이라고 하고, 이 상태 전이마다 항상 해당 페이지에 있던 링크를 따라가면서 전이했기 때문에 HATEOAS라고 할 수 있다. 말 그대로, 하이퍼 링크를 통한 전이가 되는 것이다.

그래서 html 같은 경우를 보면 HATEOAS를 만족하게 되는데,
```
HTTP/1.1 200 OK
Content-Type: text/html

<html>
<head> </head>
<body> <a href="/test"> test </a> </body>
</html>
```
a 태그를 통해서 하이퍼링크가 나와 있고, 이 하이퍼 링크를 통해서 그 다음 상태로 전이가 가능하기 때문에 만족한다고 볼 수 있다.

Json으로 표현하면 어떻게 할 수 있을까?
```
HTTP/1.1 200 OK
Content-Type: application/json
Link: </articles/1>; rel="previous",
			</articles/3>; rel="next";

{
	"title": "The second article",
	"contents": "blah blah..."
}
```
Link라는 헤더가 있는데, 이것이 바로 이 리소스와 하이퍼링크로 연결되어 있는 다른 리소스를 가르킬 수 있는 기능을 제공해준다.
![image](https://user-images.githubusercontent.com/80516736/228841785-7bc5734a-3bc9-49c7-b453-04e6981d7948.png)

URL정보를 응답에 추가하여 구현할 수도 있다.

## 정리
- 오늘날 대부분 "REST API"는 사실 REST를 따르고 있지 않다.
- REST의 제약 조건 중 특히 self-descriptive와 HATEOAS를 잘 만족하지 못한다.
- REST 긴 시간에 걸쳐(수십년) 진화하는 웹 애플리케이션을 위한 것
- REST를 따를 것인지는 API 설계하는 이들이 스스로 판단하여 결정
- REST를 따르겠다면 Self-decriptive와 HATEOAS를 만족시켜야한다.
  - Self-decriptiv는 custom media type, profile link relation으로 만족 가능
  - HATEOAS는 HTTP 헤더나 본문에 링크를 담아 만족 가능
- REST를 따르지 않겠다면, "REST를 만족하지 않는 REST API"를 뭐라고 부를지 결정해야할 것이다.
  - HTTP API라고 부를 수도 있고
  - 그냥 이대로 REST API라고 부를 수도 → 로이가 싫어함
  
## 참고
https://gmlwjd9405.github.io/2018/09/21/rest-and-restful.html <br/>

https://velog.io/@kjh03160/%EA%B7%B8%EB%9F%B0-REST-API%EB%A1%9C-%EA%B4%9C%EC%B0%AE%EC%9D%80%EA%B0%80 <br/>

https://joomn11.tistory.com/26 <br/>

https://www.youtube.com/watch?v=RP_f5dMoHFc <br/>

