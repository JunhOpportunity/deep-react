## 스냅샷 (23.11.01)

1. 상태 업데이트
2. 스냅샷 계산
3. DOM 트리 업데이트

```jsx
<button onClick={() => {
  setNumber(number + 1); // 다음 렌더링에서 숫자를 1로 변경할 준비를 한다. (아직 렌더링 전)
  setNumber(number + 1); // 다음 렌더링에서 숫자를 1로 변경할 준비를 한다. (아직 렌더링 전)
  setNumber(number + 1); // 다음 렌더링에서 숫자를 1로 변경할 준비를 한다. (아직 렌더링 전)
}}>+3</button>
```

첫 번째 렌더링에서 number는 0이었고, 해당 렌더링이 setNumber(number + 1)가 호출된 후에도 number 값은 여전히 0이다. **상태 변경은 다음 렌더링에 적용된다는 것이다!**

```jsx
<button onClick={() => {
  setNumber(0 + 1);
  setNumber(0 + 1);
  setNumber(0 + 1);
}}>+3</button>
```

비동기적으로 실행되더라도 상태 변경 요청 이전의 원래 값대로 출력되는 것을 기억하자.

```jsx
<button onClick={() => {
 setNumber(number + 5);
 setTimeout(() => {
   alert(number); // 3초 뒤에 alert가 출력되어도 이전 값이 출력된다.
 }, 3000);
}}>+5</button>

// ❗ 직관적으로 확인하기
<button onClick={() => {
 setNumber(0 + 5);
 setTimeout(() => {
   alert(0);
 }, 3000);
}}>+5</button>
```

이것이 필요한 이유는, 이메일을 보내는 기능이 있다고 가정해보면 편하다.
이메일 발송 버튼을 누른 뒤 용량이 커서 5초가 지나야 발송되는 이메일이 있다고 했을때 5초 이내에 수신자를 변경해버리면 이미 발송을 눌렀는데도 새로운 수신자로 발송되는 것이다.
따라서 이러한 이벤트 핸들러 실수를 줄일 수 있도록 도움이 될 수 있다.