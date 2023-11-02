# Props (23.10.30)

## Props 전달하기

1. 컴포넌트에 Props 전달

```jsx
export default function Profile() {
  return (
    <Avatar
      user={{ name: 'Kim Junho', imageId: 'imga1' }}
      size={100}
    />
  );
}
```

2. 하위 컴포넌트에서 Props 읽기 (구조 분해 할당 사용)

```jsx
function Avatar({ user, size }) {}
```

## 💡 **전달 받은 Props를 그대로 하위 컴포넌트에 전달하기**

```jsx
function Profile(props) {
  return (
    <div>
      <Avatar {...props} />
    </div>
  );
}
```

## children
> JSX 태그 내에서 콘텐츠를 중첩하면 상위 컴포넌트 내에 Children 이라는 Props를 받는다.
> 

```jsx
function Card({ children }) {
  return (
    <div className="card">
      {children}
    </div>
  );
}

export default function Profile() {
  return (
    <Card>
      <Avatar/>
    </Card>
  );
}
```

💡 Props는 불변을 유지해야 하기 때문에 컴포넌트 내에서 Props를 변경해야 하는 경우에는 상위 컴포넌트에 다른 Props(새 객체)를 전달하도록 요청해야한다. 그 다음에 오래된 Props는 폐기되고 JS엔진은 해당 Props가 차지한 메모리를 회수한다.