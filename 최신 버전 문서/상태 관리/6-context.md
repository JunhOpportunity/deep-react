# 💡 Context (23.11.08)

> Props 전달 말고 컴포넌트의 데이터를 “텔레포트” 하는 방법. 전역적으로 데이터를 사용
> 
- 트리 전체에 걸쳐 깊게 Props 전달을 하는 경우 상태를 다시 끌어올릴 때 “prop drilling” 이 발생해 문제가 생길 수 있다.
- 가장 가까운 컨텍스트가 사용된다.
- 컨텍스트가 필요한 곳
    - 테마
    - 현재 로그인 계정 확인
    - 라우팅(이전 경로 확인)
    - 상태 관리

※ 컨텍스트를 사용하면 컴포넌트를 재사용하기 어려워질 수 있다.

### 기본 문법

```jsx
import { createContext, useContext } from 'react';

const themeContext = createContext({});

export default function App () {
	const theme = useContext(themeContext);
	return (
		<div>
			<h1>메인</h1>
			<Profile />
		</div>
	)
}

function Profile() {
	const theme = useContext(themeContext);
	return (
		<div style=(theme)>
			<h1>프로필</h1>
		</div>
	)
}
```

### Provider 사용해서 확실하게

```jsx
import { createContext, useContext } from 'react';

const themeContext = createContext({});

export default function App () {
	const theme = useContext(themeContext);
	return (
		<div>
			<themeContext.Provider value={{}}>
				<h1>메인</h1>
				<Profile />
			</themeContext.Provider>
		</div>
	)
}

function Profile() {
	const theme = useContext(themeContext);
	return (
		<div style=(theme)>
			<h1>프로필</h1>
		</div>
	)
}
```

### 컴포넌트 children 활용

> createContext를 사용해 컨텍스트를 만들고, 필요한 곳에서 import 해서 사용.
> 

```jsx
import { LevelContext } from './LevelContext.js';

export default function Section({ level, children }) {
  return (
    <section className="section">
      <LevelContext.Provider value={level}>
        {children}
      </LevelContext.Provider>
    </section>
  );
}
```