# Git Command

## git 사용법

    git init
    # 현재의 디렉토리에서 작업, 레포지토리 초기화. working tree라 지칭.

    git status
    # 레포지토리 상태 표시.

    git add
    # git 내의 파일 추가. (버전 관리 시스템). stage area 단계라고도 함.

    git config --global user.[name / email] value
    # 프로젝트에 본인의 이름이나 이메일 기록

    git log
    # 레포지토리 내의 커밋 히스토리 확인 가능

    git commit -am"message"
    # 한 번 이상 add 된 파일을 커밋할 때 한꺼번에 처리할 수 있는 명령어

    git remote add origin link
    # github 내의 원격 저장소를 추가할 수 있다.

    git push -u origin master
    # -u옵션 : 로컬 레포지토리에 있는 현재 브랜치 upstream이 origin 레포의 master 브랜치로 변경.

    git log -p
    # 커밋에서 변경된 내용 함께 확인 가능
