### 컴포넌트를 순수하게 유지 (23.10.23)

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