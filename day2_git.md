# git&github 특강 2일차 정리

>2022년 08월 09일 화요일

## Commit&push
>로컬 저장소의 내용을 원격 저장소에 업로드하는 것을 학습한다.

### git commands

1. git init
   - git으로 관리 시작하려는 Dir에서 설정. 
   - Dir당 한번만 설정
2. git status
   - 파일의 상태 확인, modify 여부 확인할 때 주로 사용
3. git add 파일명
   - 파일을 git에 추가하는 명령어
   - Dir에 있는 모든 파일을 추가할 땐 git add .
4. git commit -m "커밋 사유"
   - 변경사항을 간단하게 기록
   - -m을 빼먹으면 vim에 갇히므로 빼먹지 않기
   - vim 빠져나오려면 q
5. config 설정
   - git에게 내가 누군지 알려주는 과정(한번만)
    ```bash
    $ git config --global user.email "some@gmail.com"
    $ git config --global user.name "Git ID"
    $ git config --global --list
    ```
6. git log
   - 커밋 내역 확인
   - git log는 너무 길어서 가독성이 떨어짐
   - 그러므로 git log --oneline 사용 권장
7. 커밋들을 비교하기
   - git diff 해쉬값 해쉬값
8. github와 연결
   - git remote add origin URL(repository URL을 연결하는 명령어)
   - git remote -v(연결이 잘 되었나 확인)
   - git remote rm origin(remote 삭제)
9. github에 local commits 올리기
    - git push origin master
---
## Clone&pull
>원격 저장소의 내용을 로컬 저장소로 가져오는 것을 학습한다.

### git clone

- 원격 저장소의 커밋 내역을 모두 가져와서, 로컬 저장소를 생성하는 명령어
- clone은 "복제"라는 뜻으로, git clone 명령어를 사용하면 원격 저장소를 통째로 복제해서 내 컴퓨터에 옮길 수 있다.
- git clone <원격 저장소 주소>의 형태로 작성한다.

    ```bash
    $ git clone https://github.com/Kihoon-Kwon/TIL.git
    Cloning into 'TIL'...
    remote: Enumerating objects: 3, done.
    remote: Counting objects: 100% (3/3), done.
    remote: Total 3 (delta 0), reused 3 (delta 0), pack-reused 0
    Receiving objects: 100% (3/3), done.
    ```
- 위의 코드대로 실행하면, Github의 Kihoon-Kwon이라는 계정의 TIL 원격 저장소를 복제하여 내 컴퓨터에 TIL이라는 이름의 로컬 저장소를 생성하게 된다.
- git clone을 통해 생성된 로컬 저장소는 git init과 git remote add가 이미 수행되어 있다.

### git pull

- 원격 저장소의 변경 사항을 가져와서, 로컬 저장소를 업데이트하는 명령어
- 로컬 저장소와 원격 저장소의 내용이 완전 일치하면 git pull을 해도 변화가 일어나지 않는다.
- git pull <저장소 이름><브랜치 이름>의 형태로 작성

### .gitignore
