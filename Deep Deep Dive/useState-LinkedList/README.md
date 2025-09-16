## **useState와 Linked List**

useState 를 호출하면 Hook 객체를 생성하는 것이다.

여기서 queue 객체, udate 객체 등이 존재한다.

여기서 보면 next 가 존재하는데, 이것을 보고 Linked List 자료구조라는 것을 깨달을 수 있다.

이를 통해 hook 이라는 노드들이 Linked List 형태로 연결되어있다고 유추할 수 있다.

하나의 hook 객체 안에는 하나의 queue 객체를 갖고 있다.

```jsx
function mountWorkInProgressHook(): Hook {
	const hook: Hook = {
		memoizedState: null,
		
		baseState: null,
		queue: null.
		baseUpdate: null,
		
		next: null,
	}
	
	if (workInProgressHook === null) {
		// 아무것도 작업중인 훅이 없다면
		firstWorkInProgressHook = workInProgressHook = hook;
	} else {
		// Linked List로 구현되어있기 때문에 다음 훅을 연결할 때 현재훅.next 를 사용해 할당한다.
		workInProgressHook = workInProgressHook.next = hook;
	}
	return workInProgressHook;
}
```

큐 안에는 업데이트 객체가 들어있는데, 상태를 업데이트 하기 위해 갖고있는 자바스크립트 객체를 의미한다.

큐 객체 내부에 last는 마지막에 담겨있는 update 객체를 말한다.

dispatch 함수는 dispatchAction이 bind 되어있다.

왜냐하면 dispatch 는 외부로 노출되기 때문이다. (여기서 dispatch 함수가 결국 setState 함수인 것이다.)

```jsx
const queue = (hook.queue = {
	last: null,
	dispatch: null,
	// ...
})
```

## 🤚dispatchAction 함수가 하는 일

1. dispatchAction 함수는 update 객체를 생성한다
2. 이후에 update 객체는 queue에 저장된다
3. 불필요한 렌더링이 발생하지 않도록 최적화한다
4. update 를 적용하기 위해서는 Work 를 scheduler 에 예약해야 한다
⇒ 여기서 Work란? VDOM을 재조정하는 단계에서 배운 내용이다.
즉, WORK는 reconciler가 컴포넌트의 변경 내용을 DOM에 적용하기 위해 수행하는 일을 말한다.

idle 상태 : 어떠한 일도 하지 않는 기본 상태

### update 객체

```jsx
const udate: Update<S, A> = {
	expirationTime,
	action,
	next,
	eagerReducer, 
	eagerState,
}
```

- expirationTime : Work 상태에 따른 값을 저장하는 부분
- action : setState()의 인자로 들어가는 값
- next : update 객체는 Linked List 로 저장되기 때문에 다음 노드를 가리키고 있는 값
- eagerReducer, eagerState : 불필요한 렌더링이 발생하지 않도록 최적화 하는 단계와 관련 있음