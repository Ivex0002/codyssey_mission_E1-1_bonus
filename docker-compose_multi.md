# 도커 docker-compose 멀티 컨테이너
- 이전 보너스과제에서 사용한 코드를 재활용했습니다.
### 사용한 yml 파일
```
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
    depends_on:
      - cache

  cache:
    image: redis:latest
    ports:
      - "6379:6379"
```
- cache 작업 의존을 추가했습니다. cache 에선 간단한 테스트 작업을 위해 redis를 사용했습니다.

### 실행 로그
```
User@4F-48 UCRT64 ~/Downloads/codessey-beginners_course-main/codessey-beginners_course-main/mission1_miniproject_port
$ docker compose up
[+] up 13/13
 ✔ Image redis:latest                                          Pulled   5.1s
 ✔ Network mission1_miniproject_port_default                   Created  0.0s
 ✔ Container mission1_miniproject_port-cache-1                 Created  0.2s
 ✔ Container mission1_miniproject_port-my-web-app-e1-1-bonus-1 Created  0.1s
Attaching to cache-1, my-web-app-e1-1-bonus-1
cache-1  | Starting Redis Server
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * Redis version=8.10.3, bits=64, commit=00000000, modified=1, pid=1, just started
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * Configuration loaded
cache-1  | 1:M 03 Nov 2026 06:20:04.896 * monotonic clock: POSIX clock_gettime
cache-1  | 1:M 03 Nov 2026 06:20:04.899 * Running mode=standalone, port=6379.
```
```
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose ps
NAME                                                IMAGE          COMMAND                  SERVICE                 CREATED         STATUS         PORTS
mission1_miniproject_port-cache-1                   redis:latest   "docker-entrypoint.s…"   cache                   7 minutes ago   Up 7 minutes   0.0.0.0:6379->6379/tcp, [::]:6379->6379/tcp
mission1_miniproject_port-my-web-app-e1-1-bonus-1   my-web         "python3 -m http.ser…"   my-web-app-e1-1-bonus   7 minutes ago   Up 7 minutes   0.0.0.0:8080->8000/tcp, [::]:8080->8000/tcp
```
- 빌딩을 확인 후 외부 터미널에서 compose 목록을 확인한 결과 정상적으로 잡힘을 알수있습니다.

```
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose logs cache
cache-1  | Starting Redis Server
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * oO0OoO0OoO0Oo Redis is starting oO0OoO0OoO0Oo
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * Redis version=8.10.3, bits=64, commit=00000000, modified=1, pid=1, just started
cache-1  | 1:C 03 Nov 2026 06:20:04.896 * Configuration loaded
cache-1  | 1:M 03 Nov 2026 06:20:04.896 * monotonic clock: POSIX clock_gettime
cache-1  | 1:M 03 Nov 2026 06:20:04.899 * Running mode=standalone, port=6379.
cache-1  | 1:M 03 Nov 2026 06:20:04.900 * <bf> RedisBloom version 8.10.1 (Git=unknown)
cache-1  | 1:M 03 Nov 2026 06:20:04.900 * <bf> Registering configuration options: [
cache-1  | 1:M 03 Nov 2026 06:20:04.900 * <bf>  { bf-error-rate       :      0.01 }
cache-1  | 1:M 03 Nov 2026 06:20:04.900 * <bf>  { bf-initial-size     :       100 }
```
```
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose exec cache redis-cli ping
PONG
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose exec cache redis-cli
127.0.0.1:6379> set hello world
OK
127.0.0.1:6379> get hello
"world"
```
- 실제 컨테이너 내부로 돌아가 테스트해본 결과 정상적으로 동작함을 확인했습니다
