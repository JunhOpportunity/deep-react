# 상태의 구조 선정 (23.11.06)

> 어떤 상황에서 어떤 구조의 상태가 가장 효율적일까
> 

### 상태 구조화 원칙

1. 항상 두 개 이상의 상태 변수를 동시에 업데이트 한다면 그룹화해서 병합하자.
2. 깊게 중첩된 상태는 피하자.
3. 중복 사용되는 상태는 피하자.

### 그룹화 - 객체 사용

```jsx
const [position, setPosition] = useState({
    x: 0,
    y: 0
});

// ...
		<div
      onPointerMove={e => {
        setPosition({
          x: e.clientX,
          y: e.clientY
        });
      }}
		</div>
```

※ 여기서 주의할 점은 x 또는 y 하나만 변경하는 것은 불가능 하다는 점이다.
만약 y만 변경하고 싶다면 x는 그대로 둔 채 y를 변경하는 방법을 사용해야 한다.
`setPosition({…position, y: 100})`

### 중복 상태 피하기

```jsx
// ❌
const [firstName, setFirstName] = useState('');
const [lastName, setLastName] = useState('');
const [fullName, setFullName] = useState('');

function handleFirstNameChange(e) {
  setFirstName(e.target.value);
  setFullName(e.target.value + ' ' + lastName);
}

function handleLastNameChange(e) {
  setLastName(e.target.value);
  setFullName(firstName + ' ' + e.target.value);
}

// ⭕
const [firstName, setFirstName] = useState('');
const [lastName, setLastName] = useState('');

const fullName = firstName + ' ' + lastName; 

function handleFirstNameChange(e) {
  setFirstName(e.target.value);
}

function handleLastNameChange(e) {
  setLastName(e.target.value);
}

```

fullName은 렌더링 중에 계산되기 때문에 firstName과 lastName을 붙이기 위해 새로운 상태를 만들 필요가 없다. 두 상태 중 하나의 상태를 변경시키면 재렌더링이 트리거되고, fullName에 새로운 데이터가 할당된다.