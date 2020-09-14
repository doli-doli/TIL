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
