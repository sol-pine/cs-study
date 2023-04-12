# SSR
![image](https://user-images.githubusercontent.com/105091138/231431374-aaf760bc-b2c0-4c71-aceb-6de7ff9510f3.png)

## SSR?
- 서버에서 사용자에게 보여줄 페이지를 모두 구성(렌더링)하는 방식
- 렌더링? 
  - 기존의 렌더링은 브라우저가 서버로부터 HTML, CSS, JS 파일을 받아와 파싱한 결과물을 브라우저 화면에 그리는 것
  - SSR에서의 렌더링은 HTML 파일에 렌더링 될 내용이 이미 있는 것, 따라서 브라우저가 렌더링하는 시점에 결과물을 볼 수 있음(CSR의 경우, index.html의 root div는 비어 있지만 SSR의 index.html의 root div는 렌더링할 내용으로 채워져 있음)
  - CSR은 브라우저가 JS 파일을 다운받은 후 (리액트의 경우)`ReactDOM.render(<App />, document.getElementById('root));`가 실행되고 나서야 렌더링
- SSR을 사용하면 모든 데이터가 매핑된 서비스 페이지를 브라우저에서 바로 보여줄 수 있음
- CSR 보다 페이지 구성 속도는 늦어지지만 콘텐츠 구성의 완료 시점은 빨라짐
- SEO 최적화 용이해짐

## SSR과 SEO
- 검색엔진 봇이 내용을 확인할 수 있어야하는데 CSR은 브라우저가 JS를 실행하기 전엔 내용이 없음
- SSR은 검색엔진 봇에게 내용을 제공할 수 있어 검색엔진 최적화 가능
