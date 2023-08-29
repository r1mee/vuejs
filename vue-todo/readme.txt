
{
  "todos": [
    {
      "id": 1,
      "text": "할 일 항목 1",
      "updatedAt": "2023-08-30T10:00:00.000Z"   // 수정일 (업데이트되지 않았을 때는 작성일과 동일)
    },
    {
      "id": 2,
      "text": "할 일 항목 2",
      "createdAt": "2023-08-30T11:30:00.000Z",
      "updatedAt": "2023-08-30T11:30:00.000Z"
    },
    // 기타 할 일 항목들
  ]
}















v-model = "자식 컴포넌트와 동기화시킬 데이터 이름"
부모 컴포넌트에서 데이터 prop을 통해 자식 컴포넌트로 데이터를 전달하고
그 데이터를 전달받은 자식 컴포넌트는 이벤트 전달을 통해 다시 부모로 보내주는 구조


localStorage.setItem(key, value)  로컬 스토리지에 저장
localStorage.getItem(key) 데이터 조회
localStorage.removeItem(key) 키에 해당되는 데이터 삭제
localStorage.clear() 저장소 데이터 전체 삭제
