

​git add .
git status
git commit -m "message"
git push origin develop

### git 개념 및 명령어 정리

개인 개발을 넘어, 공동 개발에서 효율적인 코드 형상 관리를 하기 위함.

**Git 영역**

**(1) Working Directory** (Local)

    : 개인 코드 작성

**(2) Staging 영역**

    **:**​ git add 를 통해서 수정된 코드를 올리는 영역

**(3) Repository**

    **:** ​ git commit 을 통해서 최종 수정본을 제출

---

## **Git 작업 플로우**

먼저 터미널에 git을 설치합니다.

linux (Ubuntu) 기준

```
Copy$ sudo apt install git-all
```

### **(1) 저장소(Repository) 생성**

원하는 폴더 들어간 후

```
Copy$ git init
```

또는 기존 github에 있는 저장소를 내 로컬로 복제할 수도 있습니다.

```
Copy  $ git clone (git 저장소의 URL)
```

### **(2) 코드 생성** **(in Working directory)**

이 예제에서는 README.md 라는 파일에 스트링 문자를 쓰는 코드를 만들겠습니다.

```
Copy  $ echo "Hello, Git!" > README.md
```

확인 >>

```
Copy$ cat README.md
Hello, Git!
```

### **(3) Staging 영역에 추가**

코드 수정이 완료되면 staging 영역에 추가합니다.

```
Copy$ git add .
```

현재 디렉토리에 있는 업데이트 된 파일을 전부 스테이징 영역으로 추가합니다.

또는,

```
Copy$ git add -A
```

수정된 파일 전부를 스테이징 영역에 추가합니다.

```
Copy$ git status
```

로 현재 add 내역을 확인할 수 있습니다.

### **(4) Repository에 commit**

```
Copy$ git commit -m "feat: README.md update"
```

-m 은 메세지의 약자이고, 뒤에 ""안에 공유할 메시지 내용을 적어주시면 됩니다.

### **(5) 원격 저장소에 push, 업데이트 된 내용은 pull**

내 local 디렉토리로 부터 **원격저장소(Remote repository)**로 보내기 위해서는 push 명령어를 사용합니다.

그 전에 원격 저장소와 내 로컬을 연결해야 합니다.

**원격 저장소 연결 (github)**

```
Copy$ git remote add origin (원격 저장소 github URL)
```

origin은 remote repository의 이름이며, 다른 이름으로 설정해도 무방합니다.

**push**

```
Copy$ git push origin master
```

origin이라는 원격저장소의 master 브랜치 (브랜치는 뒤에서 설명)에 푸쉬합니다.

최근에는 깃헙에서 메인 브랜치이름을 master가 아닌 기본으로 main 으로 해놓았습니다. (필자의 수정날짜는 2021-05-11)

따라서 브랜치를 바꾸고, 바꾼 브랜치로 push 해주시면 됩니다. (브랜치 관련 명령어는 밑에 더 나옵니다.)

```
Copy$ git branch -M main
$ git push origin main
```

**pull**

또한 다른 사람이 원격 저장소(Remote repository)에 업데이트한 파일이 있을 때, 원격저장소와 내 로컬저장소의 상태를 동일하게 만들기 위해 pull을 이용합니다.

```
Copy$ git pull
```

---

## **그 외 알아두면 좋은 git 명령어**

### **(6) 커밋 이력 확인**

```
Copy  $ git log
```

또는

한 줄로 요약해서 보고 싶은 경우

```
Copy$ git log --oneline
```

### **(7) 파일변경시 (Working drectory → Staging) 내역 확인** 및 취소

현재 디렉토리에 README.md 가 있다는 가정하에,

이 파일에 다른 내용을 적어 업데이트하고, 무엇이 바뀌었는지 확인해봅니다.

**파일 내용 변경**

```
Copy  $ echo "update test" >> README.md
```

**내용 변경 확인**

```
Copy$ cat README.md
Hello, Git!
update test
```

**변경 내용 확인**

```
Copy$ git diff
```

**staging 취소 (unstage)**

```
Copy$ git reset
```

또는

```
Copy$ git reset --hard
```

working directory 까지도 변경전 상태로 되돌림 즉, 변경한 내용이 소멸되므로 주의

### (8) commit 정리

**여러개의 commit을 하나의 commit으로 정리**

```
Copy$ git rebase -i
```

**직전과 금번 커밋을 하나로 정리**

```
Copygit commit --amend
```

---

## Git Branch

프로젝트 진행 시, 중간에 에러가 발생한다면 이를 고쳐야합니다. 하지만 그와 동시에 지금 진행하고 있는 프로젝트에서 새로운 모듈을 개발해야 할 경우 위 두 코드는 독립적으로 수행되어야 합니다.

따라서 master (기본 브랜치) 외에 다른 브랜치가 하나더 필요합니다.

### **(9) branch 확인**

```
Copy$ git branch
```

현재 설정된 브랜치 앞에 * 가 붙습니다.

### (10) branch 생성 및 변경

```
Copy$ git branch mybranch
```

새로운 브랜치 mybranch를 생성했습니다.

```
Copy$ git checkout mybranch
```

기존 브랜치(master)에서 새로운 브랜치(mybranch)로 전환합니다.

따라서 바뀐 브랜치에서 commit을 하면, 원래 브랜치에는 업데이트가 안되고, 새로운 브랜치에서만 업데이트가 됩니다.

push는 다음과 같이 진행하면 됩니다.

```
Copy$ git push origin mybranch
```

origin이라는 원격저장소의 mybranch로 push합니다.

---

## Pull Request와 Merge

commit을 한다고 최종 코드가 수정되는 것은 아닙니다.

개인이 commit을 했으면, 관리자가 이 코드를 리뷰하고 바꿀것이 있으면 수정해달라고 다시 요청해야하기 때문입니다. 그 과정을 알아봅니다.

### 1) Pull Request 발행 (Review 의뢰자)

github에 접속 후, 원격저장소에 들어가서 해당 commit의 pull request 버튼을 누르면 Reviewer에게 풀리퀘스트 메시지 전송

### 2) Review & Comment (Review 수행자)

리뷰 후 comment 할 것이 있으면 comment 버튼 클릭

### 3) Comment 대응 (Review 수행자)

local에서 코드 수정 후 원래와 같은 방식으로 commit 수행

```
Copy$ git add .
$ git commit -m "커밋 메시지"
$ git push
```

### 4) Review 및 병합 (Review 수행자)

리뷰 후 최종 결과 만족 시 병합(merge) → github에서 pull request merge 버튼 클릭