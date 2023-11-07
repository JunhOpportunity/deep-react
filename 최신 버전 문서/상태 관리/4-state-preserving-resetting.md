# 상태 보존과 재설정

> 컴포넌트가 살아있다면 상태는 유지되고, 죽었다가 다시 살아난다면 상태가 재설정 된다
> 

### 컴포넌트가 죽었다 살아나는 경우

React가 컴포넌트를 제거하면 해당 상태도 파괴된다.
컴포넌트를 다시 살리면 처음으로 초기화된다.
⇒ 컴포넌트가 죽었다 살아나는 과정은 부활이 아니라 환생인 것이다.

```jsx
export default function App() {
  const [showB, setShowB] = useState(true);
  return (
    <div>
      <Counter />
      {showB && <Counter />} 
    </div>
  );
}
```

1. 처음 렌더링 되었을 때는 Counter 컴포넌트가 둘 다 살아있다.
2. showB가 false로 변경되면 두 번째 Counter 컴포넌트는 사라진다.
3. showB가 true로 변경되면 두 번째 Counter 컴포넌트는 살아나지만 해당 컴포넌트 내의 상태는 모두 초기 상태로 돌아간다.

### 동일한 위치에 같은 컴포넌트가 변경되는 경우

이때는 상태가 보존된다.

```jsx
export default function App() {
  const [isFancy, setIsFancy] = useState(false);
  return (
    <div>
      {isFancy ? (
				<Counter isFancy={true}/>
			) : (
				<Counter isFancy={false}/>
			)}
    </div>
  );
}
```

### 동일한 위치에 같은 컴포넌트가 변경되었지만 컴포넌트의 상위 태그가 바뀐 경우

상위 태그가 변경된다면 이것은 기존 컴포넌트가 삭제되고 새로운 컴포넌트가 생성되었다고 인지되고 상태가 재설정 된다.

즉, 변경된 부분부터 그 트리 자체가 재설정 되는 것이다.

```jsx
// <div></div> -> <section></section>
export default function App() {
  const [isFancy, setIsFancy] = useState(false);
  return (
    <div>
      {isFancy ? (
				<div>
					<Counter isFancy={true}/>
				</div>
			) : (
				<section>
					<Counter isFancy={true}/>
				</section>
			)}
    </div>
  );
}
```

※ 따라서 컴포넌트 함수의 중첩을 피해야 한다.

### 동일한 위치에 같은 컴포넌트가 변경되었을 때 상태를 초기화하는 방법

한 번에 하나의 사용자 카드만 보여주고 싶은데, 다른 사용자 카드로 변경되었을 때 이전 사용자에 대한 상태를 유지하지 않는 방법

1. 교체하는 것이 아니라 따로따로 없애고 생성하는 방법
    
    ```jsx
    {isPlayerA &&
       <Counter person="Taylor" />
    }
    {!isPlayerA &&
       <Counter person="Sarah" />
    }
    ```

    
2. 키를 사용하는 방법
    
    ```jsx
    {isPlayerA ? (
       <Counter key="Taylor" person="Taylor" />
    ) : (
       <Counter key="Sarah" person="Sarah" />
    )}
    ```
    
    key를 사용하면 React가 모든 컴포넌트를 구별하도록 할 수 있다.
    평소에는 위치를 기준으로 컴포넌트를 판별하지만 key를 추가한다면 key를 기준으로 컴포넌트를 판별하게 된다.
    

여기서 CSS를 사용해 컴포넌트를 보이지 않게 한다면 상태는 보존된다. 하지만 숨겨진 트리가 크거나 많다면 속도가 매우 느려질 수 있다.