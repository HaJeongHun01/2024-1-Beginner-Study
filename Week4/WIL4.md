## Branch 전략의 필요성
본질적으론, 협업과 같은 활동 중, 팀원들 간의 서로에게 영향을 주지 않으며 공통의 이해를 달성하고 git branch를 효율적으로 관리할 수 있다. <br>
이를 위해 팀원들은 각 브랜치들의 분류와 정확한 명칭으로 구분을 해줘야하며 특히 main브랜치는 최종 목적지이기에 더욱 주의깊은 관리가 필요하다. <br>
대표적인 장점들로는 아래와 같은 것들이 있다.<br>
1. 코드 관리의 효율성 >> 코드 충돌 최소화<br>
2. 작업의 독립성 >> 개발 속도 향상<br>
3. 안정성 유지 >> 안정적인 프로덕션 환경<br>
4. 코드 리뷰 및 품질 관리 >> 코드 품질 향상상 <br>
5. 배포 및 롤백의 용이성 <br>

또한 생성한 브랜치들을 안전하게 관리하기 위해 아래와 같은 규칙들이 존재한다. <br><br>
**Branch Protection Rules** <br>
1. Branch name pattern - 특정 branch에 대해 규칙이 적용될 수 있게 한다. <br>
2. Require a pull request before merging - 해당 branch에 커밋을 추가하기 위힌 로컬에서의 Direct push가 불가능하고 별도의 branch를 만들어 pull request를 해야한다. (Direct push 방지용) <br>
3. Require status checks to pass before merging - 테스트 결과 이상이 없을 때만 merge가 가능하게 한다 <br>
4. Require conversation resolution before merging - pull request 시 conversation이 모두 solved 되었을 때만 merge가 가능하게 한다. <br>
5. Require signed commits - commit들이 sign 되어 있어야한다. <br>
6. Require linear history - 해당 branch에서 분기를 불가능하게 한다.<br>
7. Include administators - 관리자에게 5가지 규칙 중 선택한 규칙이 적용되게 한다<br>
8. Allow force pushes - 강제 push를 허용할 것인 지 여부를 결정 (권장하지 않음) <br>
9. push access를 가진 유저들이 branch를 지울 수 있게 한다. (권장하지 않음) <br>

이와 같은 규칙들은 repository의 setting에서 설정이 가능하다
<br>
## Branch 전략
위에 작성한 바와 같이, 완성되지 않은 소스코드인 main의 상태에서 branch를 사용하지 않는다면 여러 문제와 직면할 수 있다. 특히 협업과 같은 상황에선 더욱 더 혼잡을 야기할 수 있다. 따라서 대다수의 개발자들은 branch를 사용하여 코드를 정리하고 효율적으로 관리하려고 한다. 하지만 이러한 branch들도 규칙을 정하지 않고 마음대로 생성하고 병합을 한다면, 이 역시 혼란과 문제를 야기할 수 있다.<br>
그러면 어떤 규칙을 따라서 branch를 생성하는 것이 효율적일까? <br>
이 질문에 해답은 본인이 직접 규칙을 만들어도 되지만 더욱 좋은 방법은 Git-Work flow에서 찾을 수 있으며, 이는 효과적인 branch 전략을 보여주고 있다. 그리고 이 워크플로우의 종류에는 크게 Git flow와 Github flow 그리고 Gitlab flow가 있다. (Gitlab flow는 여기서 다루지 않는다.)

## Git Flow
먼저 Git Flow는 2010년에 Vincent Driessen가 한 블로그에 올린 A succesful Git branching이라는 글에 담긴 branch를 효율적으로 관리하기 위해 만든 전략이다. 그는 branch의 종류를 Master Branch에 해당하는 main과 devlop, 그리고 Supporting Branch에 해당하는 feature과 release 그리고 hotfix가 있다.<br><br>
**Master Branch**
1. main : 프로젝트 생성 시 기본으로 생성되는 branch <br>
출시 가능한 프로덕션 코드를 모아두는 branch로 생성과 동시에 개발 전반에 걸쳐 여러 병합을 통해 계속 새로운 버전을 만들어낸다. 이는 main 대신 master이라는 이름을 쓰기도 한다. <br>
2. develop : 다음 버전 개발을 위한 코드를 모아두는 branch <br>
main과 동일하게 개발 전반에 걸쳐 존재하며, feature branch의 기반이자 이곳에서의 진행중인 개발이 완료가 되면 main branch로 merge가 일어난다.<br>
<br>

**Supporting Branch**
1. feature : 하나의 기능을 개발하기 위한 branch <br>
개발 단계에서 어떠한 기능을 만들고 싶다면 , develop branch에서 생성 후(분기 후) 기능을 완성한 다음 다시 develop branch로 merge를 한다. <br>이때 사용하는 branch의 이름은 특정 명칭들을 제외하곤 모두 가능하지만, convention을 위해 feature/branch-name과 같은 형식을 만들어 팀원간의 협업이 잘 이루어 지게 하는 것이 좋다. <br>
이때 주의점은 Merge Commit을 생성해 merge를 해주어야 기능 단위로 묶이게 된다. <br>
2. release : software 배포를 준비하기 위한 branch <br>
develop branch에서 생성하며(분기) 배포전에 사소하고 자잘한 데이터들이나 버그들을 수정한다. 배포용 branch를 따로 만들어, 팀원들이 구애받지 않게 해준다. 배포 준비가 완료 되었다면 main과 develop branch에 모두 merge한다. 이때 tag를 통해 버전을 표시해주면 좋다 (release/v1.1). <br>
3.  hotfix : 배포 후에 버그와 같은 수정해야할 문제를 해결하는 branch <br>
main branch에서 생성하며(분기) 문제가 해결된다면 main과 develop branch에 모두 merge 해준다. 이는 release와 동일하게 개별 branch로 팀원들이 구애받지 않고 개발이 가능하다. <br> <br>

**Git Flow의 문제점** -- 웹 어플리케이션에 적합하지 않다. <br>
실제 Git Flow의 창시자인 Vincent Driessen도 2020년에 하나의 글을 올렸다. <br><br>
"Git-Flow는 등장하고 10년 넘게 표준처럼 자리잡고, 더 나아가 마치 만병통치약처럼 사용되었다. 현재는 Git으로 관리되는 인기있는 유형의 소프트웨어가 웹 어플리케이션으로 이동하고 있다. 웹 어플리케이션은 일반적으로 롤백되지 않고, 지속적으로 제공(Continuous Delivery)되므로 여러 버전의 소프트웨어를 지원할 필요가 없다.


웹 어플리케이션은 내가(Vincent Driessen) 10년전 블로그 글을 쓸때에는 염두해둔 소프트웨어 유형이 아니다. 팀이 소프트웨어를 지속적으로 제공한다면, Git Flow 대신 Github Flow와 같은 더 단순한 워크플로우를 채택할 것을 제안한다.


그러나 명시적으로 버전을 관리해야하는 소프트웨어를 개발한다면, 여전히 Git Flow가 적합할 수 있다." <br> <br>
간단히 요약하자면, Git Flow는 버전 관리가 필요한 프로젝트 (스마트폰 어플, 오픈소스 라이브러리, 프레임워크 등)에 적합하다. 하지만 항상 최신의 단일 버전을 사용하는 웹 어플리케이션은 이에 적합하지 않다는 것이다. <br>
Vincent Driessen은 여기서 Github Flow를 언급하는데, 실제로 그도 이를 사용할 것을 권장하고 있다.

## Github Flow
앞서 Git Flow는 수시로 배포를 하는 구조로, 대부분의 케이스에서 복잡한 형태를 띄고 있는 것과 달리, Github Flow는 main과 topic(feature) branch만을 사용해 굉장히 간단한 구조를 만들며 자동화를 적극 활용한다. <br>
1. main (master) : 기존의 main과 비슷한 branch <br>
하지만 여기서 main은 항상 안정성을 띄고 있어야 한다. 즉 모든 commit 언제든 문제 없이 배포가 가능해야하고, 언제든 새로운 branch를 문제 없이 만드는데 이때 main의 모든 branch들의 commit은 빌드가 되고 테스트를 통과해야 한다.<br>
2. topic (feature) : 새로운 기능을 개발하는 branch <br>
Git Flow에서의 feature branch와 동일한 기능을 한다.<br>
다른 점으론 먼저, hotfix에서 다루던 버그 수정도 모두 여기서 하게 된다. <br>
또한 commit이 기능적으로 완성되지 않더라도 push를 자주해주어 끊임 없는 커뮤니케이션을 유지한다. <br>
다른 종류의 branch를 만들지 않기에 topic branch의 이름은 기능을 설명할 수 있는 목적이 담긴 명확하게 지어야한다. <br>
Pull Request를 적극 활용하는데, 이때 코드 리뷰로 코드 품질을 향상시킨다. 이는 매우 중요한 역할을 한다. <br>
코드 리뷰가 끝나면 다른 사람들의 Approve를 얻은 다음 main branch에 merge한다. 이때 자동화 된 CI 빌드를 통과해야 한다.


## 어떤 전략이 더 유용한가
**Git Flow** - 복잡한 프로젝트나 대규모의 팀에서 유용 <br>
더 많은 제어와 복잡성을 가지고 있어 특정 기능이나 수정을 빠르게 배포해야 할 경우 등에서 유연성이 다소 떨어진다. 
그러나 그만큼 배포 안정성과 버전 관리 및 롤백 등 체계적인 운영이 가능하다. <br>
**Github Flow** - 잦은 수정 및 단순하며 빠른 개발과 배포에서 유용 <br>
테스트와 검증 절차를 거치지 않고 바로 main 브랜치로 merge 되므로 위험성을 가지고 있다. 
하지만 그만큼 단순하고 빠르게 기능을 테스트하고 Agile 하게 배포할 수 있기 때문에, 주로 각 환경의 구분이 명확하지 않고 작은 규모의 프로젝트에 적합한 전략이다. <br>

## Developer's Attitude
**Convention** <br>
협업간 원활한 커뮤니케이션을 위해 좋은 commit message를 사용해야 한다. 그래야지 나중에 문제가 생기거나, 긴 시간이 흐르더라도 빠르게 파악 및 해결이 가능하다. <br>
이때 보통 type, subject, body, (footer)를 담는다. <br><br>
**Googling** <br>
구글에 자료는 매우 거대하다. 실제로 개발자들은 구글에서 라이브러리를 가져가 90%를 작성한다는 말이 있을 정도다. 그러므로 우리도 막히거나 모르는 것이 생기면 구글에서 찾아보는 습관을 만들자. <br>
실제로 내가 직접 구글링을 통해 학습하고 사용하게 되면, 기억에도 오래가고 실력 향상에도 도움이 된다. <br> <br>
**Code** <br>
코드를 간결하고 효율적으로 작성하자. <br>
내가 작성한 코드는 사람들에게 보여주는 나의 모습이며 특히 Public Repository에서는 더욱 더 공개되므로, 그냥 코드를 막 실행만을 목적으로 작성한다기 보다는 내가 설계자, 즉 Architecture라는 생각으로 코드를 작성하자.
<br><br>

**Question** <br>
질문을 해야한다면, 좋은 질문을 할 수 있게 노력하자.




