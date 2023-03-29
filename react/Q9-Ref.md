# Ref
함수형 컴포넌트에서 useRef 훅을 쓰면 ref 오브젝트를 반환
```javascript
const ref = useRef(value)
// { current: value }
ref.current = "hello" //ref 오브젝트는 수정이 가능
```
- 컴포넌트가 unmount되기 전까지 라이프사이클 동안 value를 유지

### useRef는 언제 사용? Ref의 유용성
1. Ref는 state와 유사하게 값을 저장하는 저장공간이다.
- state가 바뀌면 리렌더링이 이루어지고 컴포넌트 내부의 모든 변수들은 값이 초기화된다.
- state가 바껴서 리렌더링이 일어나도 ref의 값은 유지된다.
- ref가 바뀌면 리렌더링이 일어나지 않고 변수들의 값이 유지된다.
- 불필요한 렌더링을 방지할 수 있다.

2. ref를 이용해 DOM 요소에 접근할 수 있다.`=== Document.querySelector()`
- 예를 들어 ref를 이용해 input에 focus를 줄 수 있다. 

### Ref와 State의 차이
```javascript
const [count, setCount] = useState(0);
const countRef = useRef(0);

const increaseCountState = () => setCount(count + 1);
const increaseCountRef = () => countRef.current = countRef.current + 1;

return(
  <div>
    <p>State: {count}</p>
    <p>Ref: {countRef.current}</p>
    <button onClick={increaseCountState}> State + </button>
    <button onClick={increaseCountRef}> Ref + </button>
  </div>
)
```

### Ref와 변수의 차이
```javascript
const [renderer, setRenderer] = useState(0);
const countRef = useRef(0);
let countVar = 0;

const render = () => setRenderer(renderer + 1);
const increaseRef = () => countRef.current = countRef.current + 1;
const increaseVar = () => countVar = countVar + 1;

return(
  <div>
    <p>Ref: {countRef.current}</p>
    <p>var: {countVar}</p>
    <button onClick={increaseRef}> Ref + </button>
    <button onClick={increaseVar}> Var + </button>
    <button onClick={render}> render! </button>
  </div>
)
```
