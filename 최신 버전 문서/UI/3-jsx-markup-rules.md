### JSX MarkUp 규칙 (23.10.31)

1. **단일 루트 요소 반환**
항상 최상위 요소를 만들자.
+) 여기서 빈 태그가 단일 요소를 충족시키기 위한 래핑인  `Fragment` 라고 한다. (https://react.dev/reference/react/Fragment)
    
    ```jsx
    return (
    <>
    	<div><div/>
    	<img />
    </>
    )
    ```
    
2. 모든 태그 닫기
3. 속성은 CamelCase
`JSX` → `JS`, `JSX로 작성된 속성` → `JS 객체의 key`

TIP) 기존 마크업을 JSX로 변환하기 위해 일일이 작성하지 말고 변환해주는 사이트를 사용하자.
https://transform.tools/html-to-jsx