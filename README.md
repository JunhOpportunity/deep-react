# deep-react
👀 React의 공식 문서를 뜯어보며 새롭게 깨달은 내용들을 정리해보자
🤔 11월 둘째주까지 공식 문서에 대한 1차 정리를 완료한 뒤에 복습을 진행하며 내용을 이해하기 쉽게 다듬는 과정을 거칠 예정입니다.

## 최신 버전 (목차와 요약)
### [기본 개념](https://github.com/JunhOpportunity/deep-react/tree/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EA%B8%B0%EB%B3%B8%20%EA%B0%9C%EB%85%90)
- [JSX](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EA%B8%B0%EB%B3%B8%20%EA%B0%9C%EB%85%90/1-jsx.md)
> HTML처럼 작성되었지만 실제로는 내부적으로는 JavaScript
- [Pure Component (순수한 컴포넌트)](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EA%B8%B0%EB%B3%B8%20%EA%B0%9C%EB%85%90/2-pure-component.md)
> Props를 활용하여 컴포넌트를 순수하게 만들자
- [Props](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EA%B8%B0%EB%B3%B8%20%EA%B0%9C%EB%85%90/3-props.md)
> {children} 을 적극 활용하자

### [UI에 관하여](https://github.com/JunhOpportunity/deep-react/tree/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI)
- [컴포넌트](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/1-component.md)
> 컴포넌트는 MarkUP을 뿌릴 수 있는 JS 함수이다
- [컴포넌트 import & export](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/2-component-import-export.md)
> 루트 컴포넌트에서 다른 컴포넌트들을 생성하지 말고, 새로운 파일을 생성해 따로 작성
- [JSX 마크업 규칙](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/3-jsx-markup-rules.md)
- [JSX 안에 JS](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/4-js-in-jsx.md)
> 중괄호를 사용
- [조건부 렌더링](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/5-conditional-rendering.md)
> null 반환은 혼란을 야기할 수 있다
- [렌더링](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/UI/6-rendering.md)

### [상호 작용](https://github.com/JunhOpportunity/deep-react/tree/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9)
- [useState](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/1-usestate.md)
> React 렌더링은 지역 변수에 대한 변경 사항을 고려하지 않는다.
- [이벤트 핸들러](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/2-event-handler.md)
> 이벤트 핸들러에 전달된 함수는 호출되지 않고 전달되어야 한다. (함수 이름만 전달)
- [렌더링](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/3-rendering.md)
> React가 컴포넌트를 호출하는 것
- [스냅샷](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/4-snapshot.md)
- [객체 형태의 상태 업데이트](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/5-object-state-update.md)
> 객체 상태를 직접 변경해서는 안된다. 반드시 새 객체를 생성하거나 복사해서 변경해야 한다. 리엑트가 상태 변화를 감지하지 못하기 때문이다.
- [배열 형태의 상태 업데이트](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%98%B8%20%EC%9E%91%EC%9A%A9/6-array-state-update.md)

### [상태 관리](https://github.com/JunhOpportunity/deep-react/tree/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC)
- [상태를 사용하여 UI 반응하기](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/1-state-write-process.md)
> React는 UI를 직접 조작하지 않는다. 대신, 보여주고 싶은 것을 선언하면 된다.
- [상태의 구조](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/2-state-structure.md)
> 어떤 상황에서 어떤 구조의 상태가 가장 효율적일까
- [컴포넌트 간 상태 공유](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/3-component-state-share.md)
> 공통 상위 컴포넌트에서 props로 상태를 전달 받는다
- [상태 보존과 재설정](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/4-state-preserving-resetting.md)
> 컴포넌트가 살아있다면 상태는 유지되고, 죽었다가 다시 살아난다면 상태가 재설정 된다
- [useReducer](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/5-reducer.md)
> useState와 비슷하지만, 상태에 대한 처리까지 한 번에 모아둘 수 있는 효율적인 훅이다.
- [useContext](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/6-context.md)
> Props 전달 말고 컴포넌트의 데이터를 “텔레포트” 하는 방법. 전역적으로 데이터를 사용
- [Reducer & Context 결합](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%EC%83%81%ED%83%9C%20%EA%B4%80%EB%A6%AC/7-reducer-context.md)

### [탈출용 해치](https://github.com/JunhOpportunity/deep-react/tree/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98)
- [useRef](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/1-useref.md)
- [useEffect](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/2-useEffect.md)
> useEffect 내부의 코드는 마운트 되었을 때 실행되고, useEffect 내부의 return은 마운트가 해제될 때 실행된다.
- [useEffect는 꼭 필요한 경우에만 사용하자](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/3-useEffect-may-not-be-necessary.md)
> 특정 동작을 실행시키고 싶은데, 원치 않는 다른 동작도 함께 실행된다면 useEffect에서 제거 시키거나 useEffect를 사용하지 말아야 한다.
- [Lifecycle](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/4-lifecycle.md)
> 모든 컴포넌트는 동일한 생명주기를 가진다.
- [이벤트 핸들러와 useEffect 분리](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/5-separate-event-effect.md)
> 특정 상호작용을 처리해야 할 경우 이벤트 핸들러를 사용한다
- [useEffect 종속성 제거하기](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/6-remove-dependency.md)
- [커스텀 훅](https://github.com/JunhOpportunity/deep-react/blob/main/%EC%B5%9C%EC%8B%A0%20%EB%B2%84%EC%A0%84%20%EB%AC%B8%EC%84%9C/%ED%83%88%EC%B6%9C%EC%9A%A9%20%ED%95%B4%EC%B9%98/7-customhooks.md)
