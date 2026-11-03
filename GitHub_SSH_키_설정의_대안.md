# GitHub SSH 키 설정
- 본 교육과정에선 개인 데스크탑 대신 공용 기기를 사용하므로 **GitHub SSH 키를 절대 사용하지 않을 예정입니다.**
- 때문에 대안으로써 http상에서의 인증 과정만 적고자 합니다

### 로컬 프로젝트에서 깃허브로 업로드
```
User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port
$ git init
Initialized empty Git repository in C:/Users/User/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port/.git/

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git add .
warning: in the working copy of 'docker-compose.yml', LF will be replaced by CRLF the next time Git touches it

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ 

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git commit -m "test project start"
Author identity unknown

*** Please tell me who you are.

Run

  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"

to set your account's default identity.
Omit --global to set the identity only in this repository.

fatal: unable to auto-detect email address (got 'User@4F-48.(none)')

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git config --local user.email "garam199803@gmail.com"

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git config --local user.name "garam"

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git commit -m "test project start"
[master (root-commit) 4df3ff4] test project start
 3 files changed, 43 insertions(+)
 create mode 100644 Dockerfile
 create mode 100644 docker-compose.yml
 create mode 100644 index.html

User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port (master)
$ git branch -M main
git remote add origin https://github.com/Ivex0002/docker_compose_practice_miniproject.git
git push -u origin main
info: please complete authentication in your browser...
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 12 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (5/5), 865 bytes | 865.00 KiB/s, done.
Total 5 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
To https://github.com/Ivex0002/docker_compose_practice_miniproject.git
 * [new branch]      main -> main
branch 'main' set up to track 'origin/main'.
```
- 공용 pc이기 때문에 이름이나 이메일이 섞이는 사고를 막고자 global 대신 local로 설정했습니다

<img width="400" alt="스크린샷 2026-11-03 161249" src="https://github.com/user-attachments/assets/8ff47c12-3042-4ea5-b485-617a5894e834" />

<img width="400" alt="스크린샷 2026-11-03 161308" src="https://github.com/user-attachments/assets/fd6d88db-c9fc-4850-9218-262af63d1fdd" />


- 인증 과정 중 `info: please complete authentication in your browser...` 에 대한 스크린샷입니다

- 웹에서의 로그인 과정은 보안을 위해 외부 인증 앱 otp를 사용중입니다.

<img width="400" alt="스크린샷 2026-11-03 161359" src="https://github.com/user-attachments/assets/ec4c4181-9c0d-44d4-8bfa-f06aff402375" />

- 정상적으로 저장소에 코드가 업로드 된 것을 확인했습니다.
