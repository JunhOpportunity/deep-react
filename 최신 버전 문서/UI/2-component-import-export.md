### 💡 Component - Import & Export (23.10.30)

루트(App.js) 컴포넌트에서 다른 컴포넌트들을 생성하지 말고, 새로운 파일을 생성해 따로 작성하는 것이 좋다, 이를 통해 모듈화되고 재사용이 가능해지기 때문이다.

```jsx
// ⭕ App.js
import Gallery from './Gallery.js';

export default function App() {
  return (
    <Gallery />
  );
}

// ❌ App.js
function Profile() {
  return (<img/>);
}

export default function App() {
  return (
    <Profile />
  );
}
```

`**import Profile from ‘./Profile.js’` VS `import { Profile } from ‘./Profile.js’`**

- `import **Profile** from ‘./Profile.js’` : 한 파일에서 하나만의 컴포넌트를 반환하는 경우에 사용
    
    ```jsx
    export default function Profile () {}
    
    import Profile from './Profile.js';
    ```
    
- `**import { Profile } from ‘./Profile.js’`** : 한 파일에서 여러개의 컴포넌트를 반환하는 경우에 사용 (export default 쓰지 않았을 경우에!)
    
    ```jsx
    export function Profile () {}
    export function User () {}
    
    import { Profile, User } from './Profile.js';
    ```
    

⇒ 💡 딱 하나만 export 하니까 뭘 가져오든 그 컴포넌트만 가져올테고, 여러개를 export 하니까 어떤걸 가져와야하는지 명시해주어야 하는 것이다.

+) 이 두 방식이 혼동을 일으킬 수 있으므로 팀의 상황에 맞추어서 하나의 스타일만 사용할 수도 있다.