# 커스텀 훅

## 커스텀 훅 컨벤션

- 커스텀 훅의 이름은 항상 `use` 로 시작한다
- 커스텀 훅의 이름은 camelCase를 사용한다
- 명확한 이름을 선택해서 작성한다. 이에 어려움을 겪는다면 각종 로직들이 결합되어 있을 가능성이 크다 (코드를 자주 작성하지 않는 사람이 보아도 수행 작업, 필요 작업, 반환 값 등을 추측할 수 있을 만큼 명확해야 한다.)
- 마운트 시에만 실행되는 것이 아닌 마운트 해제 시에도 실행되도록 return을 사용한다.
- 

이로써 내부에 React State가 포함될 수 있다는 것을 알리는 것이다.

## 커스텀 훅에 함수 전달

- 커스텀 훅에 함수를 전달할 때는 함수의 이름을 전달한다.
- 주의해야 하는 것은 커스텀 훅에 useEffect 내부에서 사용되는 경우에 함수가 고정적으로 같은 일을 수행하는 함수일 경우에는 useEffectEvent를 사용해서 함수를 전달하는 것이 좋다.
매번 같은 일을 수행하는데 상태가 변화할 때마다 또 다시 선언되거나 사용될 필요가 없기 때문이다.

## 💡 커스텀 훅 예시

- 굉장히 유용하고 이해가 잘 가는 좋은 코드 예시를 가져왔다

```jsx
// React 공식 문서의 코드를 그대로 가져왔습니다.
// ❗ state를 저장하고 해당 state가 포함된 객체를 반환
import { useState } from 'react';

export function useFormInput(initialValue) {
  const [value, setValue] = useState(initialValue);

  function handleChange(e) {
    setValue(e.target.value);
  }

  const inputProps = {
    value: value,
    onChange: handleChange
  };

  return inputProps;
}

// spread 연산자를 사용해 바로 어트리뷰트로 적용
export default function Form() {
  const firstNameProps = useFormInput('Mary');
  const lastNameProps = useFormInput('Poppins');

  return (
    <>
      <label>
        First name:
        <input {...firstNameProps} />
      </label>
      <label>
        Last name:
        <input {...lastNameProps} />
      </label>
      <p><b>Good morning, {firstNameProps.value} {lastNameProps.value}.</b></p>
    </>
  );
}
```

[Reusing Logic with Custom Hooks – React](https://react.dev/learn/reusing-logic-with-custom-hooks#custom-hooks-let-you-share-stateful-logic-not-state-itself)

💡 반복적으로 사용되는 코드로 보이지만, 각각 사용하는 변수나 목적이 다른 경우 useEffect에 같이 넣으면 안된다. 이때 두 로직이 같은 경우 커스텀 훅을 생성해서 공통 로직 자체를 훅으로 추출해서 사용하면 코드가 단순해질 수 있고 커스텀 훅을 제대로 활용할 수 있다.