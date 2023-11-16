# Refs (23.11.16)

> 컴포넌트가 정보를 기억하기를 원하지만 해당 정보가 새 렌더링을 트리거하는 것을 원하지 않는 경우 사용
> 

```jsx
import { useRef } from 'react';

const ref = useRef(0);

ref.current += 1;
```

```jsx
// useRef가 반환하는 객체
{ 
  current: 0
}
```

ref의 current 값은 증가하지만, 만약 화면에 current 값을 출력하도록 만들었다면 다시 렌더링 되지 않기 때문에 변경된 값을 볼 수 없다. 초기의 값만 계속해서 보이게 되는 것이다.

그렇다면 useRef를 도대체 언제 사용해야 할까?

- DOM 요소 저장 및 조작

# Refs를 사용하여 DOM 조작

> DOM 노드의 JSX 태그 내부의 속성에 ref를 전달
> 

```jsx
<div ref={ref}>
```

예를 들어, 위 div에 초점을 맞추고 싶다면 `ref.current.scrollIntoView()` 또는 `ref.current.focus()` 를 사용하면 된다.

여기서 주의할 점은, React는 컴포넌트가 다른 컴포넌트의 DOM 노드에 접근하는 것을 허용하지 않기 때문에 다른 컴포넌트에서 ref를 사용해 포커스 하는 경우에는 에러가 발생한다.
심지어 부모-자식 관계에서도 허용하지 않는다.

이때는 특정 방법을 사용해야 하는데, 아래 코드를 참고하자.
(아래 코드는 버튼을 누르면 input을 포커스 하는 기능을 구현한 것이다.)

```jsx
// ❌ - 에러 발생
function ChildComponent(props) { 
	return <input {...props} />; // 여기서 props에 ref를 그대로 전달
}

function ParentComponent() {
	const ref = useRef(null);
	
	function handleClick() {
		ref.current.focus();
	}

	return (
		<>
			<ChildComponent ref={ref}/>
			<button onClick={handleClick}> 포커스 </button>
		</>
	)
}
```

```jsx
// ⭕
function ChildComponent((props, ref)) { 
	return <input {...props} ref={ref}/>; 
}

function ParentComponent() {
	const ref = useRef(null);
	
	function handleClick() {
		ref.current.focus();
	}

	return (
		<>
			<ChildComponent ref={ref}/>
			<button onClick={handleClick}> 포커스 </button>
		</>
	)
}
```

다른 props는 그대로 전달하지만, ref만 따로 빼서 전달하는 것을 확인할 수 있다.