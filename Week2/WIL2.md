## Branch를 사용하는 이유
다수의 개발자들이 하나의 목표를 가지고 코드를 짤 떄, 
이들은 여러 기능들을 구현해야 하고 또한 계속 디버그 작업도 해주어야 한다.

결국 각각의 인원들이 분담하여 맡는 역할이 있을탠데 하나의 소스코드를 가지고 작업을 하게 되면
개개인의 스타일에 따라 잦은 충돌들이 발생하게 된다

이를 막기 위해 Branch를 만들어 다른 공간에서 각자 작업하여 서로에게 영향을 주지 않고, 마지막에 Merge로 코드들을 합치는 과정을 거친다.

또한 이러한 방식은 각각의 Branch마다 목적이 분명하기에 문제가 발생시 그에 따른 조치를 취하기가 용이하다.

## 용어 설명
Fork : 나의 코드를 다른 사람들과 공유를 하고 싶거나, 피드백 혹은 제안과 같은 것을 받고 싶을 때 사용- 다른 사람들은 fork를 눌러 내 코드를 가져올 수 있음

Star : 북마크와 동일한 기능

Issue: 코드를 작성 중에 문제가 발생하거나, 특정한 기능들을 만들고 싶을 때 생성

Branch : 위와 동일

Pull request : 병합을 하기 전 단계, 코드리뷰

Merge : main branch (사용하던 소스코드)로 합병, 합치는 과정 <br/>
종류 - 1. merge commit - 순서대로 commit하고 이를 참조하는 main을 형성,  이는 모든     기록들을 포함한다. <br/>
   2. squash merge - commit들을 하나로 합친 후 main에 추가, 필요성이 적은        commit들은  제거한다 - 비교적 코드가 깔끔해진다 <br/>
   3. rebase merge - commit들을 합치지 않고 그냥 바로 main에 추가한다 - 이는 commit     hash 발생 가능성이 있어 보통 사용을 지양한다.

## 실습
1. issue 만들기 - git hub의 repositories에서 만든다 <br/>
      제목과 내용을 적기
2. branch 만들기 - git branch "이름" : branch 형성 <br/>
        git branch -b "이름" : branch 형성 및 이동 <br/>
        git branch -D "이름" : branch 삭제 <br/>
        git branch -a : 현재 존재하는 모든 branch 표시 <br/>
        git checkout "이름" : 해당 branch로 이동 <br/>
       - 현재 머물러 있는 branch는 vscode 좌측 하단에 표시 됨
3. 파일 만들기 - 해당 파일 만든 후 commit하고 push해주기 (이때 branch 명으로 push를        해주기)
4. pull request 만들기 - git hub에서 pull requset를 생성 후, 병합 대상과 목적지를 설정하                     며 제목과 설명을 작성 - 만약 이슈를 닫고 싶다면 '-close #issue             number' 을 description에 기입 (이번 실습에서는 열어둔다)
5. merge - 3개의 옵션 중 하나를 골라 (이번 실습에서는 squash merge) merge하기
6. 나의 repositories에서 확인한다

## 과제 링크
https://github.com/HaJeongHun01/2024-1-Beginner-Study/pull/4