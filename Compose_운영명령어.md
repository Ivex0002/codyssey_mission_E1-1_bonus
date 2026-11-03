# Compose_운영명령어

## 명령어 정리
### 실행 / 종료
```
docker compose up        # 실행
docker compose up -d     # 백그라운드 실행
docker compose down      # 종료 + 컨테이너/네트워크 삭제
docker compose stop      # 삭제x 멈추기만
docker compose start     # stop한 걸 다시 시작
```

### 상태확인
```
docker compose ps        # 컨테이너 목록/상태
docker compose logs      # 전체 로그
docker compose logs cache    # 특정 서비스 로그
docker compose logs -f cache # 실시간으로 계속 보기(follow)
```

### 컨테이너 안으로 들어가기
```
docker compose exec cache redis-cli ping   # 명령 하나 실행
docker compose exec cache sh               # 셸로 접속
exit                                       # 나가기
```

### 변경 반영
```
docker compose up -d --build   # 코드/Dockerfile 바꾼 뒤 재빌드 후 실행
docker compose restart         # 재시작
```

이전 보너스 과제 1, 2 에서 docker compose up, ps, logs, exec 를 해보았으므로 stop, start, restart 를 실행해보겠습니다

## 실행 로그 : stop, start, restart
```
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose stop
[+] stop 2/2
 ✔ Container mission1_miniproject_port-my-web-app-e1-1-bonus-1 Stopped                                              3.3s
 ✔ Container mission1_miniproject_port-cache-1                 Stopped                                              0.4s
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose start
[+] start 2/2
 ✔ Container mission1_miniproject_port-cache-1                 Started                                              0.2s
 ✔ Container mission1_miniproject_port-my-web-app-e1-1-bonus-1 Started                                              0.2s
PS C:\Users\User\Downloads\codessey-beginners_course-main\codessey-beginners_course-main\mission1_miniproject_port> docker compose restart
[+] restart 0/2
 - Container mission1_miniproject_port-my-web-app-e1-1-bonus-1 Restarting                                           3.4s
 - Container mission1_miniproject_port-cache-1                 Restarting                                           3.4s
```
