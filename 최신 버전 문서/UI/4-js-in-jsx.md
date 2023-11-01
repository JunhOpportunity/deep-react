### JSX에서 JS 문법 사용 (23.10.31)

> 중괄호를 사용하라!
> 

⇒ 속성의 텍스트 또는 HTML TEXT를 동적으로 지정하려는 경우 : `{}` 중괄호 안에 작성

중괄호 사용 규칙

- JSX 태그 내부의 텍스트로는 작동하지만 그 외부에서는 작동하지 않는다.
    
    ```jsx
    // ⭕
    <h1>{name}'s Diary</h1>
    
    // ❌
    <{tag}>My Diary</{tag>
    ```
    
- 객체를 전달하는 경우에는 이중 중괄호를 사용한다. (특히 JSX의 인라인 CSS 스타일에서)
    
    ```jsx
    <h1 style={{backgroundColor: 'black', color: 'pink'}}>제목</h1>
    ```
    

+) 이런 식으로 style 리팩토링 가능

```jsx
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

<div style={person.theme}></div>
```

### Pr