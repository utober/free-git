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




