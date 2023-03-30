# SPA와 MPA

## MPA(Multi Page Application)
![image](https://user-images.githubusercontent.com/80516736/228844801-6745d0e6-8e09-4e36-b870-93562c670529.png)
- 여러 개의 페이지로 구성된 애플리케이션
- 웹 페이지 화면마다, 정적 파일 html로 보여주는 애플리케이션
- 클라이언트가 서버에 페이지를 요청하면, 클라이언트에게 HTML만 넘겨줌
- Server Side Rendering

### 장점
페이지마다 키워드가 노출되어 있으므로, 검색이 쉽다
### 단점
프론트 엔드와 백엔드 간 개발 업무가 밀접하게 연관된다

## SPA(Single Page Application)
![image](https://user-images.githubusercontent.com/80516736/228844916-4129ccbd-6f1f-4567-b750-c290b93bb7a4.png)
- 한 개의 페이지로 구성된 애플리케이션
- 페이지를 변경하지 않고, 자바스크립트만을 이용하여 콘텐츠만 변경하여 웹페이지를 보여주는 애플리케이션
- AJAX(Asynchronous JavaScript and XML)와 REST API로 서버에 데이터를 요청하고, JSON으로 응답받은 후 데이터를 변경함
- Client Side Rendering
### 장점
- 서버가 해야 할 역할을 클라이언트 부담하므로, 서버 부담이 경감
- 모듈화 및 컴포넌트 개발에 용이
- 백엔드와 프론트 개발 영역을 명확하게 구분
### 단점
- 초기 구동 속도가 느림 (처음 접속 시, 사이트 구성과 관련 없는 모든 리소스를 한 번에 다 받음)
- 클라이언트에 중요 비즈니스 로직이 노출될 수 있음
- 검색 엔진 최적화(Search Engine Optimization)가 어려움 => 페이지가 로딩되어야 리소스가 보이므로, 검색에 노출이 안됨
  - 동적렌더링(Dynamic Rendering)이나 history api를 이용해 문제를 해결할 수 있음

## SPA는 모든 사이트에 필요한가?
### 사이트가 방대한 양의 콘텐츠를 담고자 한다면?
예를 들어, EC(E-Commerce) 사이트의 경우 방대한 양의 콘텐츠를 담아야하기 때문에 한번에 모든 요소를 요청하는 SPA 방식(Chunk로 묶어 일부만 로딩하는 방법도 있습니다만)보다는 MPA방식으로 구성하는 것이 SEO뿐만 아니라 페이지 속도 측면에서도 더 유리하다고 볼 수 있다. 이는 비단 EC 사이트가 아니더라도 블로그 형태의 사이트나 에버그린 콘텐츠를 담는 사이트 등 콘텐츠를 계속 빌드업하려는 사이트에 경우 모두 해당된다고 할 수 있다.

### 사이트의 규모가 작다면?
사이트의 콘텐츠가 적고 화려하면서 부드러운 이미지 구현이 필요한 사이트의 경우 SPA가 적합할 수 있다. 또한 모바일 환경에서 사용자 경험이 좋은 SPA방식은 SEO에 완전하지 않거나 불편한 보완책을 감수하고 SPA를 선택할 수 있다.

### SPA와 MPA를 섞은 하이브리드 방식
SPA와 MPA방식을 섞은 하이브리드 방식으로 사이트를 제작할 수도 있다. SPA로 페이지 구현이 효과적인 페이지만 일부 SPA로 제한하고 검색에 노출이 되어야하는 페이지는 MPA로 제작하는 방법으로 사이트를 구축하는 방법도 있다.

## 참고

https://www.ascentkorea.com/seo-for-spa/

https://it-techtree.tistory.com/entry/Web-Advantage-And-Disadvantage-SPA-MPA

https://learn.microsoft.com/en-us/archive/msdn-magazine/2013/november/asp-net-single-page-applications-build-modern-responsive-web-apps-with-asp-net
