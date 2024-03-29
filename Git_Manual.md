// Reference Book: [Pro Git](https://git-scm.com/book/ko/v2)

// Written by WoohyunSHIN. I reconstitute the reference book as my style for studying. If you have question or I commit an infrigement of copyright, send me a mail <swh159@gmail.com> please thank you.

# 1. Git 이란 ?

***

​	VCS (Version Control System) 의 일종으로 소스코드를 효과적으로 관리하기 위해 개발된 '분산형 버전 관리 시스템이다.'

**IMPORTANT** : 아래의 내용을 다 모르더라도 나는 Github를 간단하게 사용하겠다고 한다면 아래의 내용은 알고 넘어가자. 여러명과의 공동작업이라고 하기보단 개인 공부용 포트폴리오 용으로 사용할 수 있다.

#### Tip : 아래는 CLI 를 이용하여 local 에서 Github 에 파일을 업로드 하는 명령어 이다. 

```
1. git init : 현재(pwd) 존재하는 위치의 디렉토리를 git 저장소로 사용할 것이다! 라고 명명 하는 작업이다.

2. git add [파일명] : 디렉토리 안에 [파일]을 git이 관리하는 local 저장소로 commit 영역에 넣을 것이다. 대기실이라고 생각하면 편하다. 팁은 현위치를 나타내는 "." 을 이용하여 모든 파일을 대기실로 넣을 수 있다.

3. git commit -m "first commit" : 현재 대기실에 있는 파일들에게 first commit 이라는 이름표를 붙여라

4. git remote add origin https://github.com/WoohyunSHIN/ETC.git : Github에 있는 디렉토리와 local의 선을 이어주는 작업으로 한번만 작업하면 된다.

5. git push -u origin master : 이름표를 단 파일들을 원격저장소로 밀어보낸다! 라는 명령어이다. 다음부터는 git push 라고만 입력해도 원격저장소로 이어진다.
```



## 1.1. Github 란 ?

***

​	git을 공유할 수 있는 플랫폼중 하나이다. 다양한 플랫폼이 존재하나 가장 인기가 있으며 많은 개발자들이 프로잭트를 공유하거나, 포트폴리오를 위하여 사용된다.



## 1.2. git repository 란 ?

***

​	저장소란 말그대로 파일이나 폴더를 저장해 두는 곳이다. git 저장소가 제공하는 좋은 점 중 하나는 파일이 변경 이력 별로 구분되어 저장이된다는 점이다. 비슷한 파일이라도 실제 내용 일부 문구가 서로 다르면 다른 파일로 인식을 한다.

* 원격 저장소 & 로컬 저장소
  1. Remote Repository : 파일이 원격 저장소 전용 서버에서 관리되며 여러 사람이 함께 공유하기 위한 저장소이다.
  2. Local Repository : 나의 PC에 파일이 저장되는 개인 전용 저장소이다. 로컬 저장소를 만드는 방법은 2가지가 있다. 첫번째, 아예 저장소를 새로 만들거나, 두번째, 이미 만들어져 있는 원격 저장소를 로컬 저장소로 복사해온다.

## 1.3. commit 이란 ?

***

​	변경을 기록하는 역활을한다. 파일 및 폴더의 추가/변경 사항을 저장소에 기록하려면 **commit**이란 버튼을 눌러줘야 한다. 커밋 버튼을 누르면 이전 커밋 상태부터 현재 상태까지의 변경 이력이 기록된 커밋이 만들어진다. 각 커밋에는 영문/숫자로 이루어진 40자리 고유 이름이 붙는다. 저장소에선 이 40자리 이름을 보고 각 커밋을 구분하고 선택한다.

## 1.4. git 의 3가지 상태

***

​	처음 배우면서 정리를 해가는 입장에서 가장 헷갈렸던 부분이다. 아래의 3가지 상태는 git 프로젝터의 3가지 단계와 연결돼 있다. 

> Git은 파일을 Committed, Modified, Staged 3가지 상태로 관리를 한다.
>
> * Committed 란 데이터가 로컬 테이터베이스에 안전하게 저장돼었다는 것을 의미한다.
> * Modified 는 수정한 파일을 아직 로컬 데이터베이스에 커밋하지 않은 것을 말한다.
> * Staged 란 현재 수정한 파일을 곧 커밋할 것이라고 표시한 상태를 의미한다.

![1](https://git-scm.com/book/en/v2/images/areas.png)

### 1.4.1. Working Directory

***

​	쉽게 얘기하여 우리가 흔히 말하는 폴더를 작업디렉토리라고 하거나 Working Tree 라고한다.  위의 그림과 같이 프로젝트의 특정 버전을 Checkout한 것이다. **.git directory** 는 지금 작업하는 디스크에 있고 그 디렉토리 안에 압축된 데이터베이스에서 파일을 가져와 작업디렉토리를 만든다.

```
Checkout 이란 ?
> 중앙 저장소 또는 로컬 저장소에서 워킹 디렉토리로 복사 하는 행위.

```



### 1.4.2. Staging Area 

***

​	**commit** 명령어를 실행하기 전의 **.git direcotry** 와 **Working Directory** 사이에 존재하는 공간을 **Index** 또는 **Staging Area** 라고한다. git의 ‘커밋’ 작업은 ‘작업 트리’에 있는 변경 내용을 저장소에 바로 기록하는 것이 아니라 그 사이 공간인 ‘인덱스’에 파일 상태를 기록 (staged) 하게 되어 있다. 따라서 저장소에 변경 사항을 기록하기 위해서는, 기록하고자 하는 모든 변경 사항들이 ‘인덱스’에 존재해야 한다.

```
git add [파일명] 
```

은 ~에 해당 파일을 **tracked** 시키는 것이며 **스냅샷**을 만든 것이다.

### 1.4.3. Repository

***

​	git 디렉토리는 git이 프로젝트의 메타데이터와 객체 데이터베이스를 저장하는 곳을 말한다. 이 git 디렉토리가 git의 핵심이다. git directory를 만드는 2가지 방법 :

1. 첫번째 : 직접 빈 디렉토리를 만든다.

   git directory가 만들어지기 원하는 디렉토리로 **cmd**(윈도우) or **terminal**(맥) 를 사용하여 이동 후 디렉토리 안에서 **git init** 명령어를 집어넣으면 **.git** 이라는 보이지 않는 디렉토리가 생성된다. 혹시 CLI 에서 확인하고 싶을 경우 맥북 기준 **ls -al** 명령어로 확인 가능하다.   

```
git init 
```

2. 두번째 : 이미 진행중인 프로젝트를 받아온다

   첫번째와 동일하게 원하는 디렉토리로 이동후 **git clone [주소값]** 을 이용하여 원하는 원격 저장소를 받아온다

```
git clone https://github.com/WoohyunSHIN/ETC
```



### 1.4.4. 예시

***

 	github를 처음 접하고 원하는 파일을 원거리 저장소에 push 하는 작업을 할 떄, 기입했던 명령어들에 대한 **해석** :

1. 워킹 트리에서 파일을 수정한다. 예를들어 파일의 이름을 변경한다.

```
mv Readme.md README.md
```

2. Staging Area 에 파일을 stage해서 커밋할 스냅샷을 만든다. 모든 파일을 추가 할 수도 있고 선택 하여 추가할 수도 있다.

```
git add README.md
```

3. Staging Area에 있는 파일들을 커밋해서 Git 디렉토리에 영구적인 스냅샷으로 저장한다. 변경된 이름의 md 파일에 second commit 이라는 딱지를 붙일꺼다.

```
git commit -m "second commit"
```



## 1.5. 파일의 라이프 사이클

***

* Working directory

  * Tracked file or Untracked file
    * if file == Tracked
      * Unmodified
      * Modified
      * Staged

  

  ​	처음 저장소를 Clone 하면 모든 파일은 Tracked 이면서 Unmodified 상태이다. 왜냐하면 파일을 Checkout 하고 나서 아무것도 수정하지 않았기 때문이다. 마지막 커밋 이후 아직 아무것도 수정하지 않은 상태에서 어떤 파일을 수정하면 Git은 그 파일을 Modified 상태로 인식한다. 실제로 커밋을 하기위해서는 파일을 Staged 상태로 만들고, Staged 상태의 파일을 커밋한다.

![2](https://git-scm.com/book/en/v2/images/lifecycle.png)



​	**git add** 명령어는 Untracked 를 Tracked(Staged) 으로 바꿀 때도 사용하며, 수정한 파일이 Modified 상태에서 Staged 상태로 바꿀때도 사용한다.

> Unmodified, Modified, and Staged 상태 모두 기본적으로 Tracked 되고 있다는 것을 가정한다.

 	**git commit** 명령어를 사용할 때 -a 옵션을 사용할 경우 이미 **git add** 를 한번 하여 Tracked 중인 상태의 파일을 자동으로 Staging Area에 넣는다. 따라서 파일을 수정후 **git add** 명령어를 실행하는 수고를 덜 수 있다.

```
git commit -a -m "added new lines for test"
```



### 1.5.1. 파일 삭제

***

​	Git 에서 파일을 제거하려면 **git rm [파일명]** 명령으로 Tracked 상태의 파일을 삭제후에 commit 해야한다. 이명령은 워킹 디렉토리에 있는 파일도 삭제하기 때문에 실제 파일도 지워진다. 커밋하면 파일은 삭제되고 Git은 이 파일을 더는 추적하지 않는다. 

​	이미 파일을 수정했거나 Staging Area에 추가했다면 **-f** 옵션을 주어 **강제 삭제**해야한다. 

```
$ git rm PROJECTS.md
rm 'PROJECTS.md'
$ git status
On branch master
Your branch is up-to-date with 'origin/master'
Changes to be committed:
	(use "git reset HEAD <file>..." to unstage)

		deleted: PROJECTS.md
```



### 1.5.2. 파일 이름 변경하기

***

​	리눅스처럼 mv 를 사용하는 것은 똑같으나 단순 mv 만을 사용하지 않고 **git mv** 라는 명령어를 사용하여 mv 후 원래 파일을 git rm 하는 번거러움을 없앤다.

```
$ git mv README.md README
$ git status
On branch master
Your branch is up-to-date with 'origin/master'
Changes to be committed:
	(use "git reset HEAD <file>..." to unstage)

		renamed: README.md -> README
```

***



## 1.6. Git의 기초



### 1.6.1. 커밋 히스토리 조회하기

***

​	저장소의 히스토리를 보고 싶을 때 사용하는 명령어로 **git log** 가 있다. 특별한 아규먼트 없이 git log 명령을 실행하면 저장소의 커밋 히스토리를 시간순으로 보여준다. 가장 유용한 옵션 2가지만 예로 들자면 :

> **-p** : 각 커밋의 diff 결과를 보여준다. 추가 : **-2** 옵션을 사용하여 최근 2개만 본다.
>
> ```
> git log -p -2
> ```

> **-S** : 코드에서 추가되거나 제거된 내용 중에 특정 텍스트가 포함되어 있는지를 검색한다. 
>
> ```
> git log -S [찾는내용]
> ```

***

### 1.6.2. 파일 상태를 Unstage로 변경하기

​	여러 파일을 Staged 한후 commit 을 하기전 한 파일을 수정을 하고싶다. 이러한 경우 수정이 필요한 파일을 Unstage 후 다시 **git add** 를 사용하여 staged를 해야한다. 그럴때 사용하는 명령어는 **git reset HEAD [파일명]** 이다.

```
$ git add *
$ git reset HEAD CONTRIBUTING.md
Unstaged changes after reset:
M			CONTRIBUTING.md
```

***

### 1.6.3. Remote Repository 

​	인터넷이나 네트워크 어딘가에 있는 저장소를 뜻한다. 저장소에 대한 다양한 권한(RWX)을 부여 할 수 있다. 리모트 저장소를 관리한다는 것은 저장소를 추가, 삭제하는 것 뿐만 아니라 브랜치를 관리하고 추적할지 말지 등을 관리하는 것을 말한다.

> 먼저, **git remote** 라는 명령어를 입력하게 되면 현재 프로젝트에 등록된 여러 리모트 저장소를 확인할수 있다. 

> git clone 명령어를 사용하게 되면 default 값으로 origin 으로 이름이 잡히게 된다. 기존 워킹 디렉토리에 새 리모트 저장소를 추가할 수 있는데 **git remote add [단축이름] [url]** 를 사용한다.

***

