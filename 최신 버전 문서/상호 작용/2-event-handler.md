# 이벤트 핸들러 (23.11.01)

> 이벤트 핸들러에 전달된 함수는 호출되지 않고 전달되어야 한다. (함수 이름만 전달)
> 

만약 함수 호출을 전달한다면 렌더링하는 동안 해당 함수를 실행하게 된다.
함수만을 전달한다면 이벤트가 수행될 때 함수가 실행되는 것이다.

만약 이벤트 핸들러 함수를 인라인으로 정의하려면 익명 함수로 래핑하라

```jsx
<button onClick={() => alert('You clicked me!')}>
```

- onClick
- onMouseEnter

## 💡 더 깔끔한 코드 작성하기 - 여러 가지 버튼

```jsx
function Button({message, children}) {
	return (
		<button onClick={() => alert(message)}>
			{children}
		</button>
	);
}

export deafult function App() {
	return (
		<div>
			<Button message="Login">
				Login
			</Button>
			<Button message="Logout">
				Logout
			</Button>
		</div>
	)
}
```

이벤트 핸들러는 컴포넌트에 존재하는 모든 하위 항목에서도 이벤트를 포착한다.(이벤트 버블링)

```jsx
// 버튼 클릭하면 <div>에 있는 alert도 실행
export default function Toolbar() {
  return (
    <div className="Toolbar" onClick={() => {
      alert('You clicked on the toolbar!');
    }}>
      <button onClick={() => alert('Playing!')}>
        Play Movie
      </button>
      <button onClick={() => alert('Uploading!')}>
        Upload Image
      </button>
    </div>
  );
}
```

그래서 `stopPropagation` 을 사용해 버블링을 중지시킬 수 있다.

```jsx
<button onClick={e => {
      e.stopPropagation();
      onClick();
    }}>
      {children}
</button>
```

브라우저 이벤트에는 기본동작중에 <form> 내부의 버튼을 클릭할 때 발생하는 제출 이벤트는 기본적으로 전체 페이지를 다시 로드한다.

따라서 이때 `preventDefault()`를 사용해 이것을 방지할 수 있다

```jsx
<form onSubmit={(e) => {
	e.preventDefault();
}}>
	<input />
	<button><button />
</form>
```

## us