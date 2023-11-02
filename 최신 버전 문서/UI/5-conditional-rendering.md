# 조건부 렌더링 (23.10.31)

조건부로 아무것도 반환하고 싶지 않은 경우에는 null 을 반환하면 된다.

```jsx
if (isLogined) {
	return null;
}
return <h1>로그인을 하셔야 합니다!</h1>
```

하지만 null을 반환하는 것은 개발자가 렌더링을 시도할 때 논란의 요소가 될 수 있으므로 사용하지 않는 것이 좋다. ⇒ 부모 컴포넌트에서 조건부로 컴포넌트를 렌더링하면 된다.

- 삼항 연산자
- 💡 논리 연산자 (모두 True 일 때 마지막 피연산자 값을 반환 | 첫 번째 거짓 연산자의 값 반환)
    
    ```jsx
    return (
    	<li className="item">
        {name} {isPacked && '✔'}
      </li>
    )
    ```
    
    +) React는 거짓을 null 이나 정의되지 않은 것과 마찬가지로 JSX 트리에서 “구멍” 으로 간주하기때문에 그 자리에 아무것도 렌더링하지 않는다.
    
    +) 논리 연산자를 사용해 조건부 렌더링을 할 때 절대로 왼쪽에 숫자를 넣지 마라. 왼쪽이 0이면 전체 표현식이 해당 값(0)을 가져오고, React는 0을 렌더링하게된다. 따라서 숫자를 사용해 Boolean을 표시할 때에는 Bool로 만들면 된다.
    
    ```jsx
    const count = 0;
    
    // ❌
    return <>{count && <p>New messages</p>.}</> // 0 반환
    
    // ⭕
    return <>{count > 0 && <p>New messages</p>.}</>
    ```
    
- 💡 변수 할당 렌더링 (유지보수 용이)
    
    ```jsx
    function Item({ name, isPacked }) {
      let itemContent = name;
      if (isPacked) {
        itemContent = (
          <del>
            {name + " ✔"}
          </del>
        );
      }
      return (
        <li className="item">
          {itemContent}
        </li>
      );
    }
    ```
    