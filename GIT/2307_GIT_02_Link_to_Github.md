# Git 에서 Github로 업로드하기

> 01에서 Gitbash를 이용해 파일 관리의 왕기초를 배웠다. 이제 이 파일들을 Gitbash를 이용해 Github로 업로드 해보자.
<br>
> > 2023.07.14(금요일) 수업 수강
> >
> > ​								   작성 시작
>
<br>

## 시작 하기 전

> 1. Gitbash를 설치 후 사용한다.
> 2. Github 계정 필요
> 3. C/Users/***(사용자 이름) 아래 업로드를 원하는 디렉토리를 생성한다.
>
> // 여기까진 01에서 완료. 이후 내용은 이전에 한 것과 중복되는 것도 있지만 정리를 위해 한번 더 기입한다.

<br>


## Git commend - Github 업로드 과정

### - git init

현재 자신이 위치한 디렉토리를 (master)로 지정한다.
>
단, root를 (master)로 지정하는 실수를 하지말것.

root 가 (master) 가 된다면, 하위 디렉토리에 있는 .git 파일들과 충돌을 일으켜 작업이 불가해진다.

> 만약 지정해버렸다면 root에 있는 .git을 삭제할것.
>
> 삭제 방법은 아래와 같다.
> rm .git


### - git status

현재 git의 상태를 확인한다.

만약 commit 까지 완료 된 상태라면 안정적인 메세지가 나오지만, 변경 된 파일이 있다면 메세지가 나온다.



### - git add !!!(파일 이름) 혹은 git add `.`

하나의 파일만 변경 된다면 그 파일을 포인팅 하지만, 다수개라면 `.`로 변경 된 파일 전부를 status 로 add 한다.



### - git commit -m "!!!(메세지)"

status에 있는 파일들을 commit 한다. 

commit 함으로써 Github에 올릴 준비를 마친다.

뒤에 주석을 반드시 붙인다.



### - git remote[저장소 이름. 주로 origin 사용] [저장소 주소. Github의 repositories 의 html]

Github에 올릴 경로를 지정한다.

Github repositorie address를 찾는 경로는 다음과 같다.

1. 해당 repositorie 의 "Code" 페이지
2. 우측 상단의 초록상자 "<> Code" 클릭
3. URL Copy



### - git remote 

remote 지정을 확인한다.



### - git remote -v

remote 링크를 확인한다.

### - git log

git 의 commit 내역을 확인한다. 

단, 간단하게만 표시된다.

진입하면 VIM이 나오는데 당황하지 말고 `q` 로 escape 한다.


### - git log -v

git 의 commit 내역을 확인한다. 

자세한 내역이 표시된다.

진입하면 VIM이 나오는데 당황하지 말고 `q` 로 escape 한다.

### - git log --oneline

git 의 commit 내역을 확인한다. 

자세한 내역의 한 줄만 표시된다.


### - git push origin master

>  다운 받았는데 master가 아니라 main이면 대신 쓰면됨

git에 업로드 되어있는 파일들을 현재 디렉토리 주소로 불러온다.

만약 새로운 디렉토리에 생성을 원한다면 아래의 내용을 따른다.

### - git clone  !!!(주소)  !!!(새로 만들 이름 폴더)

> Github에서 새로운 디렉토리로 다운받길 원하는 경우 

상단의 git remote 에서 한 것 처럼 URL 가져와 (주소) 에 넣고 새로 생성 될 디렉토리 이름을 뒤에 넣는다.


### 참고) 싱글 브렌치

> Github의 repositorie에는 [main] 과 그 외 브렌치가 존재한다. [main] 하나만 있으면 싱글 브렌치, 2개 이상은 멀티 브렌치이다.
>
> 브렌치가 나뉘면 마치 분기점이 나누어 지는 것 처럼 작업에 효율적 활용이 가능하다.
>
> 개인프로젝트 등 규모가 작은 프로젝트면 싱글브렌치도 충분히 가능하다.


### - Github 에서 협업하기

1.  메인 사용자가 설정 권한 부여해야됨
2.  팀장)github setting -> colabo~ -> 주소찾고 초대보냄
3.  팀원) 업로드가능
4.  팀장) 깃헙에서 수정 된 파일 받아오기
5.  git pull origin master(브랜치명)
6.  작업
7.  저장
8.  add, commit, push 작업

<br>
<br>



## - VScode 를 활용해 Github 연결하기

  - git -> VScode

    > git 에서 code .

  - VS code 에서 MarkDown 터미널 열기

    >1. VScode 좌측 상단 '터미널'
    >2. 터미널 탭 우측 상단 `+` 누르기
    >3. Git bash
>
  - VS code에서 파일 디렉토리 열기
    > code !!!(파일이름.형식)

