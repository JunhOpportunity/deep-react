# useEffect와 Sync (23.11.17)

> Effect는 일반적으로 React 코드에서 벗어나 일부 외부 시스템과 동기화하는 데 사용된다.
> 
- Effect를 사용하면 특정 이벤트가 아닌 렌더링 자체로 인해 발생하는 부작용을 지정할 수 있다.
- ⭐ useEffect는 모든 렌더링 이후에 실행된다.
즉, 해당 렌더링이 화면에 반영될 때까지 useEffect 내부의 코드를 기다린다.
- React 에서 렌더링 도중에 DOM 수정과 같은 사이드 이펙트를 포함해서는 안된다.
ex) useRef를 사용해 직접 영상을 실행시키거나 정지시키는 것
- 💡 Effect 에서 데이터를 가져오는 것은 좋지 않다. 캐시를 사용하거나 React Query, useSWR 같은 것을 사용하자.

## useEffect를 사용하는 방법

> useEffect 내부의 코드는 마운트 되었을 때 실행되고, useEffect 내부의 return은 마운트가 해제될 때 실행된다.
> 

### 기본 사용법

- 모든 렌더링 이후에 실행하는 경우

```jsx
import { useEffect } from 'react';

function MyComponent() {
  useEffect(() => {});
  return <div />;
}
```

### 특정 경우에만 동작하도록 하는 방법

<aside>
💡 개발 환경에서 React는 초기 마운트 직후에 모든 컴포넌트를 한 번 더 마운트하므로 useEffect 내부에서 실행한 코드의 결과가 두 번 출력된다면 정상적인 것이다.
컴포넌트를 다시 마운트 함으로써 React는 다른 페이지로 이동했다가 다시 돌아오는 경우 코드 손상 여부를 확인한다. 이것이 Strict Mode 이다.

</aside>

1. 마운트(화면에 처음 나타날 때) 되었을 때 실행하는 경우 (return 사용하자.)

```jsx
function MyComponent() {
  useEffect(() => {
		console.log("마운트 되었음!")
		return console.log("마운트 제거!")
	}, []);
}

// 출력 예시
// 1. 마운트 되었음!
// 2. 마운트 제거!
// 3. 마운트 되었음!
```

1. 특정 값이 변경되었을 때 실행하는 경우 (종속성 배열 추가)

```jsx
function MyComponent() {
  useEffect(() => {

	}, [isLogin]);
}

```

## useEffect가 무한 루프를 생성하는 이유

```jsx
const [count, setCount] = useState(0);
useEffect(() => {
  setCount(count + 1);
});
```

이 코드를 사용했다가 무한 루프가 걸리는 경우를 경험해본 사람이 많을 것이다.

이때 무한 루프가 생성되는 이유는

1. 렌더링 이후 useEffect 실행
2. setCount()로 상태 변경시 렌더링 트리거
3. 렌더링 이후 useEffect 실행
4. setCount()로 상태 변경시 렌더링 트리거
5. …

## useEffect를 사용하지 않고 한 번만 실행하는 방법

> 컴포넌트 밖에 로직을 배치하면 된다.
> 

```jsx
// React 공식 문서의 코드를 그대로 가져왔습니다.
if (typeof window !== 'undefined') { 
  checkAuthToken(); // Auth 토큰 확인으로 로그인 확인
  loadDataFromLocalStorage(); // 로컬 스토리지에 있는 데이터 확인
}

function App() {
}
```

## useEffect 사용 시 주의 사항

- useEffect 내부에 결제 요청 관련 코드가 들어있는 경우라면 다른 페이지에 갔다가 다시 돌아왔을 때 또 다시 결제 요청이 보내진다. 따라서 렌더링으로 인해 결제가 발생하도록 하고 싶지 않다면 useEffect 밖으로 결제 로직을 빼자.

작동 방식을 이해하기 위한 좋은 예시가 있으니 useEffect의 작동 방식을 까먹었다면 다시 들어가보자. 

https://react.dev/learn/synchronizing-with-effects#putting-it-all-together