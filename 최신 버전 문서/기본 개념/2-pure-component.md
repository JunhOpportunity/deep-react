# 컴포넌트를 순수하게 유지 (23.10.23)

동일한 입력은 동일한 출력을 해야한다.
⇒ Props를 전달하여 컴포넌트를 순수하게 만들 수 있다.

```jsx
**// 좋지 않은 컴포넌트 예시**
let guest = 0;

function Cup() {
  guest = guest + 1;
  return <h2>guset : #{guest}</h2>;
}

export default function TeaSet() {
  return (
    <>
      <Cup /> // guset : #2
      <Cup /> // guset : #4
    </>
  );
}
```

```jsx
**// 좋은 컴포넌트 예시** - Props 사용
function Cup({ guest }) {
  return <h2>guest : #{guest}</h2>;
}

export default function TeaSet() {
  return (
    <>
      <Cup guest={1} /> // guset : #1
      <Cup guest={2} /> // guset : #2
    </>
  );
}
```

# 순수한 컴포넌트를 지향하라

- 호출되기 전에 존재했던 객체나 변수는 변경되지 않는다.
- 동일한 입력에 대한 결과는 항상 동일하다. (ex. y=2x 라는 식에 x=2 대입하면 y 는 언제나 4)

### 왜?

의도하지 않은 결과가 생성될 수 있다. ⇒ 변수를 선언하지 말고 Props로 전달하라!
사용자 입력에 대한 응답으로 값을 변경하려면 변수 대신 state를 설정해야 한다.
(컴포넌트가 렌더링되는 동안에는 기존 변수나 객체를 변경해서는 안된다.)
(그래서 Strict 모드가 있는 것이다. 컴포넌트를 두 번 호출하면서 이런 규칙을 위반하는 컴포넌트를 찾는 데 도움을 준다.)
(React 핸들러는 순수할 필요가 없다. 왜냐하면 렌더링 중에는 실행되지 않기 때문이다.)