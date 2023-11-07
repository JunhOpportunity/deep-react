# 컴포넌트 간 상태 공유 (23.11.07)

> 공통 상위 컴포넌트에서 props로 상태를 전달 받는다
> 

```jsx
function main() {
	const [openIndex, setOpenIndex] = useState(0);

	return (
		<>
			<Profile
				isOpen={openIndex == 0}
			/>
			<Profile
				isOpen={openIndex == 1}
			/>
		<>
	)
}
```