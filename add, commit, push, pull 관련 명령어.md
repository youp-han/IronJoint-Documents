

​git add .
git commit -m "message"
git push


현재 상태 확인하기

git status

지금까지 모든 커밋에 대한 내용 조회하기

git log // 지금까지 모든 커밋에 대한 내용 그래프로 나타내기 git log --graph

local git 저장소 생성하기 (.git 폴더 생성하기)

git init

git init 취소하기 (.git 폴더가 삭제, 로컬저장소 지정 해제)

rm -rf .git

git pull 되돌리기

git reset --hard ORIG_HEAD

git add 취소하기

git reset HEAD [파일명] git reset

git commit 취소하기

git reset --hard @^

Working Directory → Staging Area로 올리기

git add [디렉토리] git add .

Staging Area -> repository(.git)로 올리기

git commit -m "commit message" // add와 commit을 한번에 하고 싶다면 아래 명령어 사용 git commit -am "commit message"

**​**

**연결 관련 명령어**

**​**

원격저장소와 연결하기

git remote add origin [원격저장소 주소]

현재 연결된 원격 저장소 확인하기

git remote -v

git remote 취소하기 (원격저장소 연결 해제gkrl)

git remote rm origin

현재 연결된 원격 저장소 삭제하기

git remote remove [origin]

연결하고 있던 원격저장소의 ‘이름’이 변경되었을 때, 재설정하기

git remote set-url origin [원격저장소 주소]

**​**

**Branch 관련 명령어**

모든 브랜치 확인하기

git branch -v(-a)

브랜치 명 바꾸기

git branch -M [브랜치 이름(main)] git branch -m [현재 브랜치 이름] [바꾸고싶은 브랜치 이름]

HEAD가 가리키는 브랜치 바꾸기

git checkout [branch name]

​

가장 자주 사용되는 Git 명령어들을 간결하게 정리해두었어요. 이제 복잡하고 어려웠던 Git 명령어들을 쉽게 찾아보고, 기억하여 Git을 쉽고 빠르게 이용해보세요!

**[출처]** [매번 헷갈리는 ‘자주 쓰는 Git 명령어’ 정리집](https://blog.naver.com/codeitofficial/223419594858)|**작성자** [코드잇](https://blog.naver.com/codeitofficial)