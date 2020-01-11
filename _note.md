# git
- 버전관리
- 협업

# 설치
- https://git-scm.com :: git 프로그램 설치
- https://git-fork.com :: git client fork. 파일의 흐름을 비쥬얼로 보여줌 

# 명령어 12가지
>> git init   :: Initialized Git repository in this folder

>> git status :: 현재 상태
- 보안 파일 수동 설정 (관리제외 파일) --> .gitIgnore 관리 제외 내용 작성

>> git add code1.txt
>> git status   :: 변동사항확인
>> git rm --cached code1.txt  :: to unstage (git add 시킨 파일 되돌리기)
    -r :: folder의 경우 -r 옵션 추가
    -f :: force option
>> git status   :: 변경된 내용 확인

>> git add .    :: 모든 파일 적용 (관리파일)
- .gitIgnore 파일 생성해서 관리제외 파일이나 폴더명 기록

>> git commit -m "Initial commit"  
   :: 현재 상태 기록 및 메시지 기록
   :: 관리 대상 제외 파일은 commit 하기 전에 .gitIgnore 파일에 작성해줘야 한다.
>> git log        :: commit 정보
>> git shortlog   :: 짧게 보여줌

>> git config --global user.email "자기 이메일"   :: 관리자 이메일 등록
>> git config --global user.name "myname"   :: 관리자 이름 등록

- code1.txt 파일 내용 수정
>> git status   :: 변경 사항 확인
>> git checkout -- code1.txt    :: 수정된 내용 되돌리기
>> git status   :: 결과 확인

>> git commit -a -m "Message..."  :: git add & git commit 동시에 처리

>> git diff

- git remote add <name> <URL>
>> git remote add origin https://github.com/utober/free-git :: 원격주소
>> git push origin master   :: 원격지 저장소에 업로드

- 작업전 서버에서 commit 된 내용 내려받아서 작업(팀작업시 다른 사람이 파일 수정)
- git pull <remote> <branch>
>> git pull origin master

- 명령줄 한글 깨짐
>> set LC_ALL=ko_KR.UTF-8

- git status 결과내용 한글깨짐
>> git config --global --edit
    + [core] quotepath = false  내용 추가 후 [esc] :wq 순으로 저장 후 빠져나옴
>> git config --global core.quotepath=false :: 라인에 직접 입력하는 방법

## 실수로 커밋한 것 되돌리기

* Untracked --> Unmodified --> Modified(빨강) --> Stage(초록)
  |------------------- add the file ------------------------>
                      |---Edit the file-->
                                         |---Stage the file-->
  <--Remove the file--|
                      <-----------------commit---------------|

________________________________________________________________

[기존커밋] ---> 빨강이  --> 초록이  --> [새커밋]
                              |<------------|    (soft)
                  |<------------------------|    (Mixed) :: 
    |<--------------------------------------|    (hard)

>> git commit -m "실수로커밋"
>> git reset HEAD~1     :: 하나 뒤로 되돌아감 :: 커밋 자체를 제거

>> git reset HEAD~1 --soft  :: file은 untracked 파일로 돌아감
>> git reset --hard     :: 새커밋을 하지 않은 상태에서 초록/빨강에서 기존커밋으로 돌아감
>> git reset <커밋고유번호>  ::  커밋 선택삭제

>> git revert HEAD      :: 실수 커밋을 삭제하지 않고 수정해서 새로운 커밋 날려줌(실수커밋리셋)
   :: 실수로 github에 올렸을 경우 실수 커밋도 기록에 남겨지므로 revert로 해서 올려줌

- git reflog    ::??

## branch
>> git branch       :: * master
>> git branch development   :: 신규 branch 생성
>> git branch       :: development / * master   
>> git checkout development     :: branch development로 변경
>> git branch       :: * development / master

## 첫 시작 습관적으로
>> git branch   :: 확인
>> git pull origin master   :: 서버측 변경사항 받아오기(다른 작업자 작업)

## master에서 development 작업 내용 가져오기
>> git checkout master
>> git merge development    :: CONFLICT -- 충돌 부분 알려줌
-  내용수정
>> git merge --abort    :: merge 과정 포기
>> git add <file>       :: 고친거 반영 or >> git commit -am "합체"

** 합치기 다른 방식
>> git reset HEAD~1 --hard (되돌리기)
>> git rebase development