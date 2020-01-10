# git
- 버전관리
- 협업

# 설치
- https://git-scm.com :: git 프로그램 설치
- https://git-fork.com :: git client fork. 파일의 흐름을 비쥬얼로 보여줌 

# 명령어 12가지
>> git init   :: Initialized Git repository in this folder
>> git status :: 현재 상태
- 보안 파일 수동 설정 (관리제외 파일)
>> git add code1.txt
  >> git rm --cached code1.txt :: to unstage (git add 파일 되돌리기)
  + git status 로 확인
>> git add .    :: 모든 파일 적용