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
요약 : git status라는 명령어는 add, commit등으로 파일의 상태를 working directory, staging area, local repo, (github push한다면 remote repo도 추가)와 같은 영역으로 구분되게 되는데, 현재 파일이 어떠한 상태인 지 위와 같은 표시들로 알려줌.
## Commit 수정
git commit --amend : 가장 최근의 commit 메세지 수정 (단, commit id도 변경 됨)<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
insert를 눌러 수정을 한 뒤, esc :wq로 나와주면 된다.<br>
git commit --amend -m "수정할 메세지" : vim 진입 없이 바로 수정 <br>
git commit --amend --no-edit : 메세지 수정없이 commit

fdfdf

