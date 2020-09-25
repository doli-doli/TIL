## 초기 USER 설정
  1. 유저네임 설정 `git config --global user.name "doli-doli"`
  2. 이메일 설정 `git config --global user.email "mail@gmail.com"`
  
## 파일이나 폴더 올리기
  1. 로컬 저장소로 이동
  2. git add (파일이나 폴더)
  3. git commit -m "메세지" - 커밋
  4. git push origin master - 푸쉬
  
## 폴더 삭제
  1. cmd나 깃배쉬 이용하여 로컬 저장소로 이동 ( cd C:\Users\jh\git\Prepare ) - 경로
  2. git rm -rf ( 삭제 하고싶은 파일이나 폴더 이름 ) - 삭제
  3. git commit -m "커밋메세지" - 커밋
  4. git push -u origin master - 푸쉬
  
## 블로그 ADMIN 설정
  1. Gem 파일안에 `gem 'jekyll-admin', group: :jekyll_plugins` 추가
  2. cmd 창에서 블로그 레파지토리 저장소 경로 잡기
  3. `# bundle install # jekyll serve ` 입력
  4. `http://localhost:4000/admin/`[링크](http://localhost:4000/admin/) 접속 후 이용

## error 처리
  1. error: unable to create file ...파일경로 (Filename too long) 에러. 윈도우 API의 파일 경로 길이가 260자 제한을 갖기 때문<br/> 
  -> 1. Git Bash 관리자 권한으로 실행<br/> 
  -> 2. `git config --system core.longpaths true`
  
  2. The file will have its original line endings in your working directory / warning: LF will be replaced by CRLF.  <br/>
  맥 또는 리눅스를 쓰는 개발자와 윈도우 쓰는 개발자가 Git으로 협업할 때 발생하는 Whitespace 에러. 유닉스 시스템에서는 한 줄의 끝이 LF(Line Feed)로 이루어지는 반면,<br/>
  윈도우에서는 줄 하나가 CR(Carriage Return)와 LF(Line Feed), 즉 CRLF로 이루어지기 때문이다. 따라서 어느 한 쪽을 선택할지 Git에게 혼란이 온 것<br/>
  -> 윈도우) `git config --global core.autocrlf true` <br/>
  -> 리눅스나 맥) `git config --global core.autocrlf true input` <br/>
  -> 물론 시스템 전체가 아닌 해당 프로젝트에만 적용하고 싶다면 —global 을 빼주면 된다.<br/>
  
  3. fatal: Unable to create '경로.git/index.lock': File exists. 잘못 커밋했을 경우 생기는 에러<br/>
  -> 에러경로로 이동해서 `rm -rf ./.git/index.lock`<br/>
  
## add,commit 취소
  - git add 취소하기(파일 상태를 Unstage로 변경하기)<br/>
    1.git reset HEAD [file] 명령어를 통해 git add를 취소할 수 있다. 뒤에 파일명이 없으면 add한 파일 전체를 취소한다.
  
  - git commit 취소하기
    1. 너무 일찍 commit 했거나 어떤 파일을 빼먹고 commit 했을 경우 <br/>
     `commit 목록 확인 / git log` <br/>
~~~
[방법 1] commit을 취소하고 해당 파일들은 staged 상태로 워킹 디렉터리에 보존
$ git reset --soft HEAD^
[방법 2] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에 보존
$ git reset --mixed HEAD^ // 기본 옵션
$ git reset HEAD^ // 위와 동일
$ git reset HEAD~2 // 마지막 2개의 commit을 취소
[방법 3] commit을 취소하고 해당 파일들은 unstaged 상태로 워킹 디렉터리에서 삭제
$ git reset --hard HEAD^
~~~

  2. commit message 변경하기<br/>
  commit message를 잘못 적은 경우, `git commit –amend` 명령어를 통해 git commit message를 변경할 수 있다.
