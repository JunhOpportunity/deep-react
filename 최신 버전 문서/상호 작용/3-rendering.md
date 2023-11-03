## 렌더링 (23.11.01)

> React가 컴포넌트를 호출하는 것
> 
1. 렌더링 트리거 
컴포넌트 초기 렌더링이 트리거된다. 컴포넌트의 상태가 업데이트된다.
    
    ```jsx
    const root = createRoot(document.getElementById('root'))
    root.render(<Image />);
    ```
    
2. 컴포넌트 렌더링
초기 렌더링 : React는 Root 컴포넌트를 호출
이후 렌더링 : 상태 업데이트를 통해 재렌더링
3. DOM에 커밋
컴포넌트를 렌더링한 뒤 React는 DOM을 수정
재렌더링의 경우에는 React가 최소한의 변경사항만 계산(렌더링 중 계산)한 뒤에 적용한다.
즉, 렌더링 간에 차이가 있는 경우에만 DOM 노드를 변경한다는 것이다.
