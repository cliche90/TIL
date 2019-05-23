# How to save (github) Credential?

> IDE 의 기능이 아니라 command line 을 통해 git을 사용하게되면 github 에 내용을 push 할 때마다 계정 정보를 요구하기 때문에, 여간 귀찮은 것이 아니다. 공용으로 사용하는 환경이 아니라 개인이 사용하는 환경이라면 저장해 두어도 무방할 것이다. 

- Github 계정정보 (ID / Password) 저장 방법

  ```bash
  git config credential.helper store
  ```

  - 위 커맨드는 해당 명령을 수행한 git repository (local) 에서만 적용되므로 전체에 적용하려면 `--global` 플래그를 추가하면 된다.
  - 수행 전/후로 1회 이상 로그인했다면 이후로는 계정정보 입력 없이 사용이 가능하다.