## Week3
## git log/status
git log : commit의 목록을 보고자 할 때 사용 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
명령어 입력 시, 그동안의 commit 기록들이 순차적으로 나오게 되는데 가장 위부터 최신 commit이 나오게 된다. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
이때 여러 옵션을 사용할 수 있는데, pretty graph p stat shortstat 등등 git log --'옵션'의 형태로 불러오면 된다. 예를 들어 기록을 간단하게 한 줄로 확인하고자 하면 git log --oneline으로 해주면 된다. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
git log 화면에서 나가고자 할 땐 q를 눌러 빠져나오면 된다.<br><br>
commit id: 암호학에서 사용되는 SHA-1 함수를 사용하며 중복 확률이 낮은 40자길이의 16진수이다. <br> <br>
HEAD: git log로 확인해보면 가장 최근 commit에 HEAD표시가 있는데, 이는 현재 작업 중인 위치, 즉 가장 최근에 commit한곳을 가리킨다. <br> <br>
git status: 현재 상태를 알려주는 명령어로 <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
현재 checkout되어 있는 branch표시
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
commit 유뮤
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
untracked, tracked 확인 (add(commit)가 한 번이라도 된 적이 있는 파일인 지)
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
unmodified, modified 확인 (staged 또는 commit이후 수정이 되었는 지)
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-이때 unmodified/tracked이라면 'nothing to commit, working tree clean'이라는 문구가 
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
-modified라면, 'Changes not staged for commit:' 문구가 나옴
<br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
주의점 - 파일 저장을 해야지 unmodified, modified확인 가능
<br>
요약 : git status라는 명령어는 add, commit등으로 파일의 상태를 working directory, staging area, local repo, (github로 push한다면 remote repo도 추가)와 같은 영역으로 구분되게 되는데, 현재 파일이 어떠한 상태인 지 위와 같은 표시들로 알려줌.
## Commit 수정
git commit --amend : 가장 최근의 commit 메세지 수정 (단, commit id도 변경 됨)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
insert를 눌러 수정을 한 뒤, esc :wq로 나와주면 된다.<br>
git commit --amend -m "수정할 메세지" : vim 진입 없이 바로 수정 <br>
git commit --amend --no-edit : 메세지 수정없이 commit <br> <br>
reset -> 범위 내 commit을 제거할 때 사용 - 특정 commit으로 돌아가기, soft mixed(default) hard 3가지가 있다.
reset --soft "commit id" : commit만 취소 후, 변경 사항 staging area로 이동<br>
reset --mixed "commit id" : commit을 취소 후, 변경 사항 woriking directory로 이동<br>
reset --hard "commit id" : commit + 변경 사항 모두 제거 > 이전 commit으로 돌아감<br>
*이때 가장 최근 commit말고도 가능하며, 최근->해당 commit까지 모두 동일하게 적용 (이때 hard라면 최근->해당 직전 commit들은 그냥 삭제) <br><br>
revert -> 특정 commit 시점으로 되돌리기
git revert "commit id" : 해당 commit 되돌리기 <br>
git revert --no-edit "commit id" : 편집기 진입 없이 바로 <br>
git revert --no-commit : 직접 commit 하지 않고, 내용을 바로 staging area로 올림 <br> <br>
reset : 이전 이력을 모두 삭제해서 되돌아감 <br>
revert : 특정 commit을 되돌리는 것으로 이전 이력은 남아있음 <br>
=> reset을 사용하면, 특히 협업과 같은 상황에서는 충돌이 일어날 가능성이 있으므로 평소에는 revert 사용을 권장함.
