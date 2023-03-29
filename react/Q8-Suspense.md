# [Suspense](https://react.dev/reference/react/Suspense)

### 자식 컴포넌트가 로딩이 끝날 때까지 `fallback`을 보여주는 것

```javascript
<Suspense fallback={<Loading />}>
  <SomeComponent />
</Suspense>
```
- Suspense를 사용하기 전엔 조건부 렌더링으로 핸들링 → Suspense를 사용하여 조회 상태에 대한 의존을 해결
```javascript
const [loading, setLoading] = useState(true);

if data !== null {
    setLoading(false); 
} 

<>
    { !loading && 
        <SomeComponent />
    }
    { loading && 
        <Loading />
    }
<>
```

### [여러 로딩 상태들을 하나로 묶기](https://react.dev/reference/react/Suspense#revealing-content-together-at-once)
```javascript
<Suspense fallback={<Loading />}>
  <Biography />
  <Panel>
    <Albums />
  </Panel>
</Suspense>
```
- 하나의 로딩 컴포넌트로 여러 컴포넌트 로딩 상태를 모두 표시

### [중첩된 내용 로딩 처리](https://react.dev/reference/react/Suspense#revealing-nested-content-as-it-loads)
```javascript
<Suspense fallback={<BigSpinner />}>
  <Biography />
  <Suspense fallback={<AlbumsGlimmer />}>
    <Panel>
      <Albums />
    </Panel>
  </Suspense>
</Suspense>
```
- 중첩된 `Suspense Boundary`를 사용하면 `<Biography />`는 `<Albums />`의 로드가 끝날 때까지 기다릴 필요가 없다.

### [Stale한 State 처리](https://react.dev/reference/react/Suspense#showing-stale-content-while-fresh-content-is-loading)
```javascript
const [query, setQuery] = useState(''); // state 변경을 감지해 fallback 표시
  return (
    <>
      <label>
        Search albums:
        <input value={query} onChange={e => setQuery(e.target.value)} />
      </label>
      <Suspense fallback={<h2>Loading...</h2>}>
        <SearchResults query={query} />
      </Suspense>
    </>
  );
```
### startTransition(): 시급하지 않은 상태 업데이트를 여유있게 처리하기
```javascript
const [pending, startTransition] = useTransition();
const [num, setNum] = useState(1);

const handleClick = () => startTransition(() => setNum((prev) => prev + 1))

return (
  <>
    <p>
      <button onClick={handleClick}> + </button>
      {pending && '업데이트 중...'}
    </p>
    <p>
      number: {num}
    </p>
  </>
)
```
- `pending`은 `startTransition()`으로 실행한 state의 업데이트가 진행 중이면 `true`, 아니면 `false`
- Suspense에 적용하면
```javascript
const [num, setNum] = useState(1);

const handleClick = () => startTransition(() => setNum((prev) => prev + 1))

return (
  <>
    <p>
      <button onClick={handleClick}> + </button>
    </p>
    <Suspense fallback={'업데이트 중...'}>
      <p>
        number: {num}
      </p>
    </Suspense>
  </>
)
```
Suspense는 React에서 비동기 데이터 로드를 처리하는 프로세스를 단순화하여 개발자가 보다 반응이 빠르고 효율적인 애플리케이션을 쉽게 만들 수 있도록 한다.
