## week1

#vscode-git hub연동법

1. 파일 생성 및 불러오기
2. git init으로 .git파일을 만들어 git에서 관리하도록 설정
3. gid add . , git commit -m "first commit"으로 대상 등록 및 옮기기
4. github에서 새로운 Repository를 생성하기
5. 그 후 위 말고 아래 3줄을 복사해서 실행
6. 새로고침 후 생성을 확인
7. 그 다음 vscode에서 원하는 코드 작성 
8. 다시 git add . 과 git commit -m "원하는 commit" 작성
9. 그 다음 git push origin main 으로 github로 보내주기


*추가적으로 실험해본 결과
1. 위의 순서 중 Repository 먼저 만들면 코드가 안뜸
2. 위의 순서 중 하나라도 틀리면 코드가 안뜸
3. 만약 내용을 추가한다면 8~9번 반복 (commit을 계속 불러와야 하는 듯) + 꼭 ctrl s로 저장해주기 (저장 안하면 적용 안됨)

## 추가
add - commit 전 단계 add .은 전체파일, add 파일명은 개별파일
commit - git에 그 상태를 저장하는 것, 즉 나중에 파일이 손상되거나 변경되더라도 다시 돌아갈 수 있음

과제 링크 : https://github.com/HaJeongHun01/HaJeongHun01