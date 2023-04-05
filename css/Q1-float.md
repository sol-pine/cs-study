# float
![image](https://user-images.githubusercontent.com/80516736/230090258-ef60f667-4891-482c-a0f2-bb665db05035.png)


- 해당 요소를 다음 요소 위에 떠 있게 한다.
- 요소가 기본 레이아웃 흐름에서 벗어나 요소의 모서리가 페이지의 왼쪽이나 오른쪽이 이동한다.
- clear 속성이 있으면 페이지 흐름이 달라짐. none 이 아니라면 display 속성은 무시된다.

| 프로퍼티값  | Description | 
| :------------ | :----------- |
| right     | 오른쪽에 부유하는 블록 박스를 생성. 페이지 내용은 박스 왼쪽에 위치하며 위에서 아래로 흐름         | 
| left    |왼쪽에 부유하는 블록 박스를 생성. 페이지 내용은 박스 오른쪽에 위치하며 위에서 아래로 흐름.   | 
| none  | 요소를 부유시키지 않음|

## Float 취소
CSS의 clear 속성은 별도의 속성으로서, 주요 기능은 float 속성이 적용된 요소 다음에 위치하는 요소들이 float 속성이 적용된 요소와 겹치는 현상을 방지하기 위해 사용된다. 요소에 float 속성이 적용되면 그 이후에 등장하는 모든 요소들은 정확한 위치를 설정하기가 매우 힘들어 지게 되는데, 따라서 clear 속성을 사용하여, 이후의 요소들이 더는 float 속성에 영향을 받지 않도록 설정해주어 요소들이 float 속성이 적용된 요소 아래에 위치하도록 한다.

| 프로퍼티값  | Description | 
| :------------ | :----------- |
| none     | clear를 설정하지 않은 기본값. 요소가 어느 쪽으로든 부유할 수 있다.        | 
| right    |float: right 를 취소시킴. 요소가 왼쪽에 부유한 요소 다음에 위치하도록 한다.    | 
| left  | float :left 를 취소시킴. 요소가 오른쪽에 부유한 요소 다음에 위치하도록 한다.|
| both  | float:left , float:right 둘다 취소시킴. 요소가 왼쪽과 오른쪽에 부유한 요소 다음에 위치하도록 한다. |

## 참고
https://developer.mozilla.org/ko/docs/Web/CSS/float

https://inpa.tistory.com/entry/CSS-%F0%9F%93%9A-float

https://ofcourse.kr/css-course/float-%EC%86%8D%EC%84%B1
