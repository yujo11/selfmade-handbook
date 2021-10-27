# husky를 통한 Git hooks 활용



#### Git hooks를 적용한 이유

1. 팀원들과 협업을 하면서 공통의 formater, linter의 룰을 설정했으나 종종 룰이 지켜지지 않은 채 PR을 생성하는 경우가 있음.
2. PR하기 전 직접 명령어를 입력해 전체 파일을 검사하는 방법도 있으나 귀찮은건? -> 기계에게 맡기자

#### huksy를 적용한 이유

1. 협업하는 팀원들이 모두 통일 된 git hooks를 적용하고 싶었다.
2. 각자의 local에서 세팅하는 것 보다는 간단한 명령어를 통해 팀원들 각각의 개발환경에서 동일한 git hooks를 세팅 가능하기 때문에 선택

#### husky의 License 이슈

1. husky v5에서 라이센스가 `Parity License`로 변경되었다.
2. 그러나 v6부터는 다시 `MIT License`로 변경되었고, 현재 버전인 v7 역시  `MIT License`로 사용에 제약이 없다.

#### husky를 적용하면서 어려웠던 점

**1. root directory가 아닌 점**

하나의 저장소에서 backend/frontend로 하위 디렉토리를 나눠서 개발하다 보니 frontend폴더에 husky를 적용하기 위해서는 `.git`을 찾아가야 하는 문제가 있었다.

다행히 husky 공식 홈페이지에 Custom directory에 설정하는 방법이 적혀 있어서 문제를 간단히 해결할 수 있었다.

* [https://typicode.github.io/husky/#/?id=custom-directory](https://typicode.github.io/husky/#/?id=custom-directory)
