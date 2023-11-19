# useEffect가 필요하지 않을 수 있다 (23.11.19)

> 특정 동작을 실행시키고 싶은데, 원치 않는 다른 동작도 함께 실행된다면 useEffect에서 제거 시키거나 useEffect를 사용하지 말아야 한다.
> 
- 굳이 useEffect를 사용하지 않아도 되는 경우에는 함수로 추출해서 호출하는 방식을 사용하자.
예를 들면, 사용자의 입력으로 이벤트가 발생했을 때 동작하는 코드를 useEffect에 넣어두고 input에 대한 값을 state로 받아서 변경할 때마다 useEffect가 발생한다면 그냥 이 코드를 함수로 빼서 이벤트 핸들러 함수로 만들면 된다.
- 하위 컴포넌트에서 상위 컴포넌트의 데이터를 업데이트 하는 경우 useEffect 내부에서 업데이트 한다면 추적하기 어렵기 때문에 이를 지양해야 한다.

useEffect는 Strict Mode 때문에 두 번 실행된다는 것을 앞에서 이야기 했었다.
그렇다면 딱 한번만 실행되어야하는 코드가 useEffect에 있다면 어떻게 할까?
답은, 전역 변수를 하나 생성한 뒤에 첫 번째 실행에서 이 전역 변수를 true로 바꾸고, 중요 코드를 if문 내부에 넣으면 된다.

```jsx
// React 공식 문서의 코드를 그대로 가져왔습니다.
let didInit = false;

function App() {
  useEffect(() => {
    if (!didInit) {
      didInit = true;
      // ✅ Only runs once per app load
      loadDataFromLocalStorage();
      checkAuthToken();
    }
  }, []);
  // ...
}
```