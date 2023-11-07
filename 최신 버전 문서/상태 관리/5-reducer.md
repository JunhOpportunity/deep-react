# 💡 Reducer

> useState와 비슷하지만, 상태에 대한 처리까지 한 번에 모아둘 수 있는 효율적인 훅이다.
> 

### 기본 문법

```jsx
// ❗ if-else 문을 사용했지만, 보통 리듀서 내부에서는 switch-case 문을 사용한다.
function stateReducer(oldCount, action) {
	if(action === "UP") {
		return oldCount + 1;
	} else if (action === "DOWN") {
		return oldCount - 1;
	}
}
const [state, stateDispatch] = useReducer(stateReducer, 0)

function up() {
	stateDispatch('UP');
}
function down() {
	stateDispatch('DOWN');
}
```

### 활용 문법

```jsx
function stateReducer(oldCount, action) {
	if(action.type === "UP") {
		return oldCount + action.number;
	} else if (action.type === "DOWN") {
		return oldCount - action.number;
	}
}
const [state, stateDispatch] = useReducer(stateReducer, 0)
const [number, setNumber] = useState(1);

function up() {
	stateDispatch({type: 'UP', number: number});
}
function down() {
	stateDispatch({type: 'DOWN', number: number});
}
```

※ reducer 함수는 순수 함수여야 한다. 외부의 영향을 받아서는 안된다.
따라서 직접 외부의 다른 State에 접근해서 State에 따라 반환하는 값이 달라져서는 안된다.

이렇게 보면, 더 깔끔한 코드를 작성하기 위해 Reducer를 다른 파일로 옮겨서 모아둘 수 있지 않을까? 하는 생각이 들 수 있다. 당연히 가능하다.

간단한 상태만을 활용하는 경우에는 useState를 사용하고, 반복되거나 복잡한 상태 변경 기능이 필요한 경우에는 useReducer를 사용하자.