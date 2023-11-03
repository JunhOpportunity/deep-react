## 배열 상태 업데이트 (23.11.01)

|  | ❌❌❌ | ⭕⭕⭕ |
| --- | --- | --- |
| 추가 | push, unshift | concat, [...arr] |
| 제거 | pop, shift, splice | filter, slice |
| 변경 | splice, arr[i] = ... assignment | map |
| 정렬 | reverse, sort |  |

splice는 배열 자체를 변경하는 것이고, slice는 배열이나 일부를 복사하는 것이다.

### 배열 추가

> spread 구문 사용
> 

```jsx
setUsers(
	[
	...users,
	{userId: 1234567, name: "junho"}
	]
)

// ❗ spread 구문을 나중에 사용해도 같은 결과를 보여준다.

setUsers(
	[
	{userId: 1234567, name: "junho"},
	...users
	]
)
```

### 배열 제거

> filter 사용
> 

예시 : 휴면 계정인 유저는 제외하고 새 유저 배열로 만들기

```jsx
setUsers(
	users.filter(u =>
		u.userId !== dormantUserId; 
	)
)
```

### 배열 변경

> map 사용
> 

예시 : 일정 방문 수 이상인 유저만 등급 한 단계 올리기

```jsx
const [users, setUsers] = useState([
	{name: "J", lank: "B", visitNumber: 5},
	{name: "K", lank: "B", visitNumber: 3}
])

const lankUp = users.map(user => {
	if(user.visitNumber >= A_LANK_VISIT_NUMBER) {
		return {
			...user,
			lank: 'A'
		}
	}
})

setUsers(lankUp);
```

### 배열 삽입

> slice 사용
> 

**Array의 프로토타입 중 하나인 slice() 에 대한 간단한 설명**

- slice(a) : index a 부터 끝까지 잘라내기
- slice(a, b) : index a 부터 index b-1 까지 잘라내기
- slice() : 통째로 복사

```jsx
// 코드가 잘 되어있어서 React 공식 문서의 코드를 가져왔습니다.
function handleClick() {
    const insertAt = 1; // 삽입할 위치 정하기
    const nextArtists = [
      // 처음 ~ index (1-1 = 0) 까지를 그대로 복사
      ...artists.slice(0, insertAt),
      // 새로운 내용 삽입
      { id: nextId++, name: name },
      // index 1 부터 끝까지 그대로 복사
      ...artists.slice(insertAt)
    ];
    setArtists(nextArtists);
  }
```

### 배열 정렬

> 배열 정렬을 위해 reverse, sort를 원본에 직접 사용하지말고 복사된 데이터에 사용하자.
> 

```jsx
const [users, setUsers] = useState([
	{name: "J", lank: "B", visitNumber: 5},
	{name: "K", lank: "B", visitNumber: 3}
])

const reverseUsers = [...users]; // 원본 복사
reverseUsers.reverse();
setUsers(reverseUsers);
```