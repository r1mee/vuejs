v-model = "자식 컴포넌트와 동기화시킬 데이터 이름"
부모 컴포넌트에서 데이터 prop을 통해 자식 컴포넌트로 데이터를 전달하고
그 데이터를 전달받은 자식 컴포넌트는 이벤트 전달을 통해 다시 부모로 보내주는 구조


localStorage.setItem(key, value)  로컬 스토리지에 저장
localStorage.getItem(key) 데이터 조회
localStorage.removeItem(key) 키에 해당되는 데이터 삭제
localStorage.clear() 저장소 데이터 전체 삭제
