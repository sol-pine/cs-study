# docuemnt load event와 DOMContentLoaded event

## onload
- 스타일시트, 스크립트, iframe 및 이미지와 같은 모든 종속 리소스를 포함하여 전체 페이지가 로드되면 이벤트가 시작된다.
- 이벤트 취소할 수 없다.
- 버블링되지 않는다.

```
window.addEventListener("load", (event) => {
  console.log("page is fully loaded");
});


window.onload = (event) => {
  console.log("page is fully loaded");
};
```

## DOMContentLoaded
- 초기 HTML 문서를 완전히 불러오고 분석했을 때 발생
- 스타일 시트, 이미지, 하위 프레임의 로딩은 기다리지 않는다.
- <script>...</script>나 <script src="..."></script>를 사용해 삽입한 스크립트는 DOMContentLoaded가 실행되는 것을 막는다. 브라우저는 이 스크립트가 실행되길 기다린다.

```
window.addEventListener('DOMContentLoaded', (event) => {
    console.log('DOM fully loaded and parsed');
});
```

⚡ **일반적으로, 스크립트를 문서의 마지막(</body>) 이전에 삽입하면 굳이 이벤트를 이용하여 프로그래밍을 처리할 필요가 없다. 다만, 문서의 <head> 영역에 스크립트가 삽입되거나 외부의 파일에 정의되어 있다면 이벤트를 연결하여 문서의 로드시점에 맞게 처리해야 한다.**
  
## 참고
https://developer.mozilla.org/en-US/docs/Web/API/Window/load_event

https://developer.mozilla.org/ko/docs/Web/API/Window/DOMContentLoaded_event

https://ko.javascript.info/onload-ondomcontentloaded
