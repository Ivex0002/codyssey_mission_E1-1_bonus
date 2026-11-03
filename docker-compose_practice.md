# 도커 docker-compose.yml 작성 연습

- 사용한 파일은 이전 기본 미션의 작업 결과를 재활용했습니다. [링크](https://github.com/Ivex0002/codessey-beginners_course/tree/main/mission1_miniproject_port)

### 작성한 yml 파일
```yml
services:
  my-web-app-e1-1-bonus:
    build: .
    image: my-web
    ports:
      - "8080:8000"
    environment:
      - MODE=dev
    volumes:
      - .:/app
```
- 기본미션에서 사용한 명령어 `docker build -t my-web-app .` 에서 이전 이미지와 구분키 위해 이름을 `my-web-app-e1-1-bonus` 으로 변경하고, `docker run -d -p 8080:8000` 사용했던 명령어는 동일하게 맞춰줬습니다.

### 실제 실행 모습
```
User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port
$ docker compose up
[+] up 1/1
 ! Image my-web pull access denied for my-web, repository does not e... 5.6s
[+] Building 25.1s (12/12) FINISHED                                         
 => [internal] load local bake definitions                             0.0s
 => => reading from stdin 742B                                         0.0s
 => [internal] load build definition from Dockerfile                   0.1s
 => => transferring dockerfile: 268B                                   0.0s
 => [internal] load metadata for docker.io/library/ubuntu:latest       2.1s
 => [auth] library/ubuntu:pull token for registry-1.docker.io          0.0s
 => [internal] load .dockerignore                                      0.1s
 => => transferring context: 2B                                        0.0s
 => [1/4] FROM docker.io/library/ubuntu:latest@sha256:6a06111c3b0a860  3.2s
 => => resolve docker.io/library/ubuntu:latest@sha256:6a06111c3b0a860  0.0s
 => => sha256:f3f25b84a7d74315d94ee4108231f8f5e0cd2a44725 392B / 392B  0.2s
 => => sha256:edafa32f5d9e4d9629f0dbc6c01e63c79ff08 42.14MB / 42.14MB  2.0s
 => => extracting sha256:edafa32f5d9e4d9629f0dbc6c01e63c79ff08133c01c  1.0s
 => => extracting sha256:f3f25b84a7d74315d94ee4108231f8f5e0cd2a44725a  0.0s
 => [internal] load build context                                      0.1s
 => => transferring context: 303B                                      0.0s
 => [2/4] WORKDIR /app                                                 0.1s
 => [3/4] COPY index.html /app/index.html                              0.1s
 => [4/4] RUN apt-get update &&     apt-get install -y python3 &&     15.6s
 => exporting to image                                                 3.2s
 => => exporting layers                                                1.6s
 => => exporting manifest sha256:21de057e9f9bd116e6482543abe91f18deb9  0.0s 
 => => exporting config sha256:aaec6804a451499121322eb063c3b6b0f4895d  0.0s 
 => => exporting attestation manifest sha256:f4a25a483dd4d87a5e31d4b6  0.1s 
 => => exporting manifest list sha256:d35cd27d0d058f763eb360c9d421db2  0.0s 
 => => naming to docker.io/library/my-web:latest                       0.0s
 => => unpacking to docker.io/library/my-web:latest                    1.4s
 => resolving provenance for metadata file                             0.1s
[+] up 3/3
 ✔ Image my-web                                                Built   31.4s
 ✔ Network mission1_miniproject_port_default                   Created  0.0s
 ✔ Container mission1_miniproject_port-my-web-app-e1-1-bonus-1 Created  0.2s
Attaching to my-web-app-e1-1-bonus-1
my-web-app-e1-1-bonus-1  | 172.18.0.1 - - [03/Nov/2026 06:06:50] "GET / HTTP/1.1" 200 -
my-web-app-e1-1-bonus-1  | 172.18.0.1 - - [03/Nov/2026 06:06:50] code 404, message File not found
my-web-app-e1-1-bonus-1  | 172.18.0.1 - - [03/Nov/2026 06:06:50] "GET /favicon.ico HTTP/1.1" 404 -
```
<img width="695" height="417" alt="image" src="https://github.com/user-attachments/assets/5e503ef2-ce1e-4834-a0a4-cc952d739d0b" />

- 빌드 완료 후, http://localhost:8080/ 에서 정상적으로 잡히는걸 확인했습니다
