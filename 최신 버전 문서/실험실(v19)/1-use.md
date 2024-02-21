# use Hook

promise 또는 conetext

우리는 보통 `useQuery` 라는 커스텀 훅을 정의해 사용하거나 tanstack Query를 사용해  fetch 요청을 보냅니다.

// 요즘은 많은 도구들이 나와서 직접 useQuery 훅을 작성하지는 않지만 확실한 개선을 보여드리기 위해 useQuery 코드도 예시로 첨부하였습니다.

```jsx
// useQuery
function useQuery({queryFn}) {
	const [data, setData] = useState(null);
	const [error, setError] = useState(null);
	const [loading, setLoading] = useState(true);

	useEffect(() => {
		fetch('/api/data')
			.then(setData)
			.catch(setError)
			.finally(() => setLoading(false));
	}, []);
	
	return {data, error, loading };
}

// tanstack Query
import { useQuery } from '@tanstack/reack-query'

const { data, error, loading } = useQuery({
	queryFn: () => fetch('/api/data'),
	suspense: true, // 이 설정을 추가하면 Data만 가져올 수 있게된다. (error, loading 처리 X)
})
```

그런데 왜 fetch 요청을 보낼 때 커스텀 훅을 생성해서 사용하거나 tanstack Query같은 도구를 사용하는 것일까요?

비동기로 데이터를 불러오기 위해서는 useEffect 내부에서 요청을 해야 하는데 매번 컴포넌트에 동일한 코드를 작성하지 않기 위해 useQuery 훅을 만들거나 도구를 통해 요청을 해 깔끔한 코드를 작성할 수 있기 때문입니다.

그리고 이러한 과정을 따로 거치지 않게 하기 위해 React에서는 `use` 를 제공하는 것입니다.


## `use`란

컴포넌트 내에서  Promise 또는 Context와 같은 리소스 값을 읽을 때 사용하는 React의 Hook입니다.

다른 React Hook들과는 달리 use는 조건문과 루프 내에서 호출할 수 있기 때문에 조금 더 자유로운 사용이 가능하다는 장점이 존재합니다.

use Hook이 반환하는 값을 확인해보면 한가지 특이한 점을 찾을 수 있습니다.

요청에 대한 결과 데이터만 반환하고 error와 loading에 대해서는 따로 반환하지 않는다는 점입니다.

이는 Suspense와 ErrorBoundary로 감싸주면 Promise가 해결될 때까지 Suspense의 fallback이 표시되고 에러가 발생한 경우 ErrorBoundary의 fallback이 표시됩니다.

## 사용 방법

사용 방법은 굉장히 간단합니다.

```jsx
import { use } from 'react';

const value = use(resource)
```

여기서 `resource`는 `Promise` 또는 `Context`가 될 수 있습니다.

```jsx
import { use } from 'react';

function MessageComponent({ messagePromise }) {
  const message = use(messagePromise);
  const theme = use(ThemeContext);
```

## 주의 사항

- `use` 역시 컴포넌트 또는 커스텀 훅 내부에서만 사용이 가능합니다.
- 여기서 정말 주의해야 할 것은 클로저 내부에서 호출하는 것도 불가능하기 때문에 `map`, `filter`와 같은 프로토타입 함수 내에서 사용이 불가능 하다는 것입니다.
- 리엑트 공식 문서에서는 서버 컴포넌트에서 데이터를 가져올 때 `async-await` 사용을 권장하고 있습니다. 즉, 클라이언트 컴포넌트에서만 `use`를 사용하라는 것으로 이해할 수 있습니다.
- `use` 훅은 `try-catch` 문 내에서 호출할 수 없기 때문에 `.catch` 메서드를 사용하거나 ErrorBoundary로 감싸주어야 합니다.

## 활용 방법

### Context API와 함께 사용하기

useContext는 컴포넌트의 최상위에서 호출해야 하는데 use로 전달해서 호출하게 된다면 조건부로 호출할 수 있어 더 유연하게 Context API를 사용할 수 있다.



## Reference
- https://www.youtube.com/watch?v=zdNF9FJWJ8o
- https://www.youtube.com/watch?v=Zrsf8_YWcH8
- https://www.youtube.com/watch?v=Hd1JeePasuw
- https://react.dev/reference/react/use#usage
