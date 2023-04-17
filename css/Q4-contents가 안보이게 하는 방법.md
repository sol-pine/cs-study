# contents가 안보이게 하는 방법
웹페이지에서 캡쳐 방지를 100% 방지할 수 없지만(브라우저 개발자 도구 또는 캡처 도구를 사용하여 콘텐츠를 캡처할 수 있기 때문), javaScript나 css를 활용하여 사용자가 캡쳐하는것을 어렵게 만들수 있다.  
이미지 또는 동영상의 캡처물이 덜 유용하도록 만들수도 있다.

## 1. css로 스크린샷 방지하기
```
body {
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
```
위 CSS 코드는 웹 페이지에서 선택 가능한 텍스트, 이미지, 요소 등을 사용자가 선택하지 못하도록 하는 방법이다.   
이를 통해 사용자가 특정 콘텐츠를 복사, 붙여넣기, 드래그 등의 작업을 할 수 없도록 할 수 있다.  
다만 사용자가 캡처도구를 이용하거나 브라우저 개발자 도구를 사용할 시 캡쳐할 수 있다.  

## 2. JavaScript로 스크린샷 방지하기
```
window.addEventListener('blur', function() {
  setTimeout(function() {
    window.focus();
  }, 100);
});

window.addEventListener('focus', function() {
  clearInterval(interval);
});

var interval = setInterval(function() {
  if (document.hidden) {
    window.dispatchEvent(new Event('blur'));
  }
}, 100);
```
위 코드는 사용자가 현재 창을 포커스하지 않거나, 다른 애플리케이션으로 이동했을 때, 해당 창이 계속해서 활성 상태로 유지되도록 하는 코드이다.  
이를 통해 사용자가 스크린샷을 찍거나, 페이지를 캡처하는 동안 창이 비활성화되는 것을 방지할 수 있다.  

## 3. 이미지 워터마크 추가하기
캡처물을 찍더라도 워터마크가 존재하면 원본과의 차이를 만들어 줄 수 있다.

## 4. DRM (Digital Rights Management) 기술 사용하기 
DRM은 웹 페이지에서 콘텐츠를 보호하는 기술로, 사용자가 캡처를 시도해도 보호 기술로 인해 캡처물이 유용하지 않게 만들 수 있다.

### Widevine
Google에서 개발한 DRM 솔루션으로, Chrome 브라우저에서 지원된다.   
Widevine을 이용하여 보호된 콘텐츠를 재생하면, 해당 콘텐츠는 브라우저 내에서만 보여지고 스크린 캡쳐나 화면 녹화 등의 방법으로 캡쳐하는 것이 막힌다.

### Encrypted Media Extensions (EME)
EME는 HTML5에서 지원하는 API로, 브라우저에서 DRM을 구현하는 데 사용된다.  
EME를 이용하여 보호된 콘텐츠를 재생하면, 브라우저에서 보호된 콘텐츠에 대한 암호화 및 복호화를 수행한다. 이 때, 복호화된 콘텐츠는 메모리에만 저장되고, 실제로 저장 장치에 저장되지 않기 때문에 캡쳐를 방지할 수 있다.
