# useState (23.11.01)

> React 에서는 시간이 지남에 따라 변하는 데이터를 `**상태**`라고 칭한다.
> 

> React 에서는 컴포넌트별 메모리를 `**상태**`라고 칭한다.
> 

> React 렌더링은 지역 변수에 대한 변경 사항을 고려하지 않는다.
> 

### **새 데이터로 컴포넌트를 업데이트하기 위한 조건**

1. 렌더링 간 데이터 유지
2. React를 트리거하여 컴포넌트 재렌더링

이것을 만족하는 것이 useState Hook 이다.

1. 렌더링 간 데이터를 유지하는 상태 변수
2. 변수를 업데이트 한 뒤 React를 트리거하여 컴포넌트를 재렌더링

+) React에서 “use” 로 시작하는 함수를 Hook 이라고 한다.
Hook은 React가 렌더링하는 동안에만 사용할 수 있는 특수 함수이다.

※ Hook은 컴포넌트의 최상위 레벨 또는 자체 Hook에서만 호출할 수 있다. 조건, 루프 또는 기타 중첩된 함수 내부에서는 Hook을 호출할 수 없다.

+) 컴포넌트는 독립적이다. 같은 컴포넌트를 두 번 호출해도 각각 다른 상태를 갖게 된다.

객체나 배열 형태의 상태를 업데이트 할 때는 직접 업데이트 해서는 안되고 새 배열을 만들고 복사본을 사용하도록 해야한다.(이런 방식이 싫다면 Immer 사용 https://github.com/immerjs/use-immer)

```jsx
const [list, setList] = useState(
	{ id: 0, title: 'Big Bellies', seen: false },
  { id: 1, title: 'Lunar Landscape', seen: false },
  { id: 2, title: 'Terracotta Army', seen: true },
);
setList(list.map(artwork => {
    if (artwork.id === artworkId) {
      return { ...artwork, seen: nextSeen };
    } else {
      return artwork;
    }
}));
```