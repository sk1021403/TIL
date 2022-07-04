### git reset  
- soft: 헤더만 바뀜 -> 커밋 로그 바꿀 때 사용
- mixed: 인덱스, 헤더 날림(add 하기 전 상태로 돌아감) -> 작업 영역의 내용 변경 필요할 때 사용
- hard: 작업 영역, 인덱스, 헤더 다 날림 -> 이전의 상태로 돌아가길 원함

  ex) git reset --soft 3218  

<br/>

### git reflog
- 한 번 커밋했던 내역들이 다 남아있음  
  ex) git reflog, git reset --hard 8aaa (이런식으로 돌아가면 됨)

<br/>

### git amend
- 최종 로그 바꿀 때 사용 or 첫 로그 바꿀 때
git commit --amend -m "~" 사용하자

