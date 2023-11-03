## 객체 상태 업데이트 (23.11.01)

> 객체 상태를 직접 변경해서는 안된다. 반드시 새 객체를 생성하거나 복사해서 변경해야 한다. 리엑트가 상태 변화를 감지하지 못하기 때문이다.
> 

### **※ 객체 상태에 접근할 때 주의해야 할 부분**

쉽게 생각해보면 편하다.
아래 코드에서 index는 0 → 1 로 변경되었지만, 0 자체가 1로 변경된걸까? 그건 아니다.

```jsx
const [index, setIndex] = useState(0);
setIndex(1);
```

그렇다면 0과 1을 각각 객체로 바꿔서 생각해보면 이해가 될 것이다.

```jsx
const [user, setUser] = useState({name: 'junho', age: 23});
```

여기서 `user.age = 24` 로 변경하는 것이 가능하기는 하지만 이를 돌연변이라고 한다.
왜 하필 돌연변이냐? 이렇게 쓰지 말라고 돌연변이라고 부르는 것이다.

그냥 객체 상태를 절대 직접 변경해서는 안되는 중요 데이터라고 생각하자.
그래서 혹시라도 변경을 하고 싶다면 원본을 직접 건드는 것이 아니라 복사본을 수정하는 식으로 말이다.

```jsx
// ❗ 이런 방식은 괜찮습니다! (=로컬 뮤테이션)
const user = {};
user.name = "junho";
user.age = 23;
setUser(user);
```

### **spread 구문을 사용해 객체 복사&변경**

일일이 복사하는 것보다는 변경이 필요한 데이터만 작성하고 나머지는 그대로 가져오는 방법이다.

+) spread 구문은 JS 기본 문법으로, 코딩테스트에 자주 사용되는 문법이기도 하고 프로젝트를 구현할 때 정말 자주 사용되는 것 중 하나이다.

```jsx
// ❌ 일일이 변경하기
setUser({
	name: user.name,
	age: e.target.value
	job: user.job
})

// ⭕ 변경이 필요한 데이터만 작성하고 spread 구문 사용하기
setUser({
	...user,
	age: e.target.value
})
```

여기서 중요한 점은 spread 구문은 1차원에 대해서만 복사를 하기 때문에 중첩된 객체의 구조같은 경우에는 조금 추가된 방식으로 코드를 작성해야 한다.

```jsx
const [user, setUser] = useState({
	name: 'junho',
	article: {
		title: 'wooteco',
		image: 'https://'
	}
})

setUser({
	...user,
	article: {
		...user.article,
		title: 'woowaconf'
	}
})
```

여기서도 반복적인 코드 수행을 줄면서 복사하기 위해 immer을 사용할 수 있다.