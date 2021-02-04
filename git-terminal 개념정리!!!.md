# git 기초

> 분산버전관리시스템 (DVCS)

## git 저장소(repository) 초기화

```bash
$ git initMarmd
Initialized empty Git repository in /Users/hyungwoo/Desktop/md/.git/
```

* `.git` 숨김 폴더가 생성되고, bash 환경에서는 (master)로 브랜치 정보가 나타난다.



## 작업흐름 

## (cd 해당폴더 -> add 파일 -> commit 파일 -> push )

### 1. `add`

```bash
$ git add .            # . 현재디렉토리에 있는 모든 파일, 변경사항을 add하겠다.
$ git add a.txt b.txt        # 특정 파일
$ git add myfolder/     # 특정 폴더
```



현재 작업 중인 파일의 변경사항을 `staging area`로 변경시킨다.

* staging area : 커밋(버전)으로 기록할 대상의 파일들의 목록을 관리하는 곳

add 전 상황 (`touch 123.txt` 하고 난 뒤!)

```bash

% git status
On branch master

No commits yet
# untracked files - 트래킹이 되고 있지 않는 파일
# 첫번째 통
Untracked files:
# git add를 사용해라가 밑에 쓰여있다.
# 커밋이 될 것에 포함시키기 위해서..
# 두번째 통으로 이동시키려면..
  (use "git add <file>..." to include in what will be committed)
	123.txt

nothing added to commit but untracked files present (use "git add" to track)
```



* add 후 상황

```bash
hyungwoo@HyungWoo md % git add .
hyungwoo@HyungWoo md % git status
On branch master

No commits yet
# 커밋이 될 변경사항들
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
	new file:   123.txt
```



# 2. commit

> 변경사항들을 버전으로 기록

```bash
hyungwoo@HyungWoo md % git commit -m 'First Commit'
[master (root-commit) 605a84d] First Commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 123.txt
```

* 특정시점을 스냅샷처럼 기록한다.
* commit시 메시지는 반드시 잘 작성해야한다.
  * 지금 기록한 코드의 이력을 나타낼 수 있도록



#  기타 명령어

###  `log`

> 지금까지 기록된 커밋들을 확인할 수 있음

3번 통인 commit 버전들에 대해서 확인하는 것! 

```bash
hyungwoo@HyungWoo md % git log
commit 605a84d6a637e6121ec2378eb9ffa6f06f0e2389 (HEAD -> master)
Author: HyungWoo <woo7232@gmail.com>
Date:   Thu Feb 4 14:10:40 2021 +0900

    First Commit

$ git log --oneline # 한줄로
605a84d (HEAD -> master) First Commit

$ git log -2 # 최근 2개
$ git log --oneline -1 #최근 1개를 한줄로
```



### `status`

git 저장소의 파일 변경 사항등을 확인할 수 있음

1번 통인 working director와 2번 통인 staging area에 대한 상황을 본다. 

```bash
hyungwoo@HyungWoo md % git status
On branch master
nothing to commit, working tree clean

```

![스크린샷 2021-02-04 오후 2.20.35](/Users/hyungwoo/Desktop/%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B3%E1%84%85%E1%85%B5%E1%86%AB%E1%84%89%E1%85%A3%E1%86%BA%202021-02-04%20%E1%84%8B%E1%85%A9%E1%84%92%E1%85%AE%202.20.35.png)

# github에 바로 올리기!

```bash
% git remote add origin https://github.com/HyungWoo7232/first.git
% git push origin master
Username for 'https://github.com': HyungWoo7232
Password for 'https://HyungWoo7232@github.com': 
Enumerating objects: 6, done.
Counting objects: 100% (6/6), done.
Delta compression using up to 12 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 697 bytes | 697.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0)
remote: Resolving deltas: 100% (1/1), done.
To https://github.com/HyungWoo7232/first.git
 * [new branch]      master -> master
```

다음 줄에 username : HyungWoo7232 입력하고

password에는 열쇠그림이라 안보이지만 입력하여 엔터!



```bash
error : src refspec master does not match any
error : failed to push some refs to
```

* commit이 없을 것

```bash
% git add .
% git commit -m '_'
% git push origin master
```

