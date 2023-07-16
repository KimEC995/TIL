# Git
> 00에서 Git이 무엇이고, Gitbash를 설치했다.
>
> 이제 이 Git의 왕기초를 배워보자. 
>
> >  2023.07.13(목요일) 수업 수강
> >
> >  ​								  작성



- 시작 하기 전

> 1. Gitbash를 설치한다.
>
> > [링크][https://git-scm.com/]



### Git의 정의

> 개발자들에게 유용한 도구. 
>
> 크게
>
> - **관리**
> - **협업**
> - **배포**
>
> > 배포의 경우 **분산 관리** 시스템으로도 사용한다.
>
> 위 3가지 용도로 사용한다.



#### 줄임말 - SCM & VCS
- SCM(Source Code Managment): 코드 관리 도구
- VCS(Version Control System): 버전 관리 도구
- DVCS(Distributed Version Control System) : 분산 버전 관리 도구



### Git 명령어

`git(명령어)`



- **git init**

Git 으로 코드 관리를 시작

- 코드 관리 단위(기준): 폴더

- `(master)`: 현재 브랜치명
- `.git`  폴더 생성: Git의 관리와 관련된 파일



- **git status**

현재 상태를 출력(Git에게 현재 상태를 물어봄)

> `git init` 직후,

```
On branch master
-> master라는 브랜치 위에 있어요.
No commits yet
-> 아직 commit이 없어요.
nothing to commit (create/copy files and use "git add" to track)
-> commit할 것이 없어요.
```

> `text.txt` 파일 생성 후

```
Untracked files:
(use "git add <file>..." to include in what will be committed)
test.txt
-> 추적되지 않은 파일이 있어요.
(파일명)
nothing added to commit but untracked files present (use "git add
-> commit 하기 위해 add된 것이 없어요. 그러나 추적되지 않은 파일이 존재합니다.
```

> `git add text.txt` 입력

```
Changes to be committed:
(use "git rm --cached <file>..." to unstage)
new file: test.txt
-> commit할 변경들이 있어요.
(파일명)
```

> `git commit "TEXT" ` 이후

```
nothing to commit, working tree clean
-> commit 할 게 없어요. 작업 폴더는 깔끔해요.
```

> 파일 수정 후 (txt 생성처럼됨)

``` 
 On branch master
  Changes not staged for commit:
  -> commit하기 위해 stage 되지 않은 변경 사항이 있어요.
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
  modified: test.txt
  no changes added to commit (use "git add" and/or "git commit -a")
```



- **`git add [파일/폴더]` **

commit을 위한 stage

- `git add . `: 현재 폴더의 모든 변경 사항 stage

  > stage: commit 하기 전 준비단계.



- **`git commit -m "!!!(메세지)"`-**

commit == 버전을 생성 == 현재 상태의 스냅샷 촬영


> 처음으로 commit을 할 경우,

```
Author identity unknown
-> 누군지 몰라요
*** Please tell me who you are.
-> 당신이 누군지 알려주세요
Run
-> 아래의 명령어를 실행주세요
git config --global user.email "you@example.com"
git config --global user.name "Your Name"
```



> `git config` 설정 후 (`vim` 에디터 창)

```
# Please enter the commit message for your changes.
-> 변경사항에 대한 commit message(변경사항의 특징)를 입력해주세요.
# Lines starting with '#' will be ignored, and an empty message aborts the
commit.
-> #로 시작하는 라인은 무시됩니다. 아무것도 없는 메시지는 종료됩니다.
# On branch master
#
# Initial commit
#
# Changes to be committed:
# new file: test.txt
```



- ** `git config` **

Git에 관련된 설정

- `git config --global user.email "이메일"` : global(전역으로) user의 email 설정
- `git config --global user.email` : 설정값 확인



- ** `git log`

현재까지의 commit을 출력

>- `git log` 출력 예시

```
commit 1a7d9384d2f9a064e2ddb4719306defeb51ac3cf (HEAD -> master)
Author: John Kang <hphk.john@gmail.com>
-> 작성자
Date: Tue Mar 16 15:55:10 2021 +0900
-> 날짜
first commit
-> 커밋 메시지
```
>- `git log --oneline` 한 줄 출력

```
7c7abf0 (HEAD -> master) Add title
1a7d938 first commit
```
> 앞부분의 [7c7abf0] 는 파일 주소같은 개념. 모두 같지 않음



- ** git remote-**

- `git remote add [저장소 이름] [저장소 주소]` :  git remote add origin https://github.com/hkeryfonttlxisdrlw/basic_git
  - git에게 원격저장소(remote) 추가(add)를 명령
- 저장소 이름: `origin`
- 저장소 주소 :  https://github.com/hkeryfonttlxisdrlw/basic_git
