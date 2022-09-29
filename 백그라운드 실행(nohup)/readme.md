# 개요 
- Linux 환경 상에서 백그라운드에서 프로세스가 동작하도록 만드는 몇 가지 방법에 대해서 서술한다. 
- SIGHUP (1) : 터미널 연결이 끊겼을 때 발생하는 시그널, 일반적으로 해당 터미널에서 실행되던 프로세스들은 모두 종료된다. 


## & 사용
```sh 
$> ./test_action.sh & 
```
- 가장 간단한 방법. 
- 실행하는 명령어 뒤에 & 만 붙여주면 된다. 

- 단, 리눅스 환경에 따라서 터미널 연결이 끊길 경우 작업이 중단될 수 있다. 


## nohup 명령어 사용 
```sh 
$> nohup ./test_action.sh & 
```
- 앞에 nohup 명령어를 넣어줄 경우, 터미널 연결이 끊기더라도 작업이 계속된다. 
- 명령어 그대로 HUP 시그널(SIGHUP)을 무시하겠다는 의미다. 


## disown -h 명령어 사용
```sh 
$> ./test_action.sh 
$> [ctrl + Z] 로 작업 중단 
$> jobs  명령어로 현재 작업 중인 항목들 확인 
$> bg %{id} 로 백그라운드에서 작업 재실행 ( id 값에는 jobs 에서 확인된 프로세스 번호 값) 
$> disown -h  
```
- 마지막에 disown -h 옵션을 넣어주면 nohup 명령어처럼 터미널이나 ssh 연결이 끊어져도 작업이 계속되게 된다. 
- (-h) 옵션을 통해서 SIGHUP 시그널을 무시하게 해준다. 

# 참고 자료 
- [SSH 접속 끊어져도 프로세스 돌아가게 하기](https://umbum.dev/558) 
- [리눅스 백그라운드 작업(ssh 연결 끊겨도) ](https://tyson.tistory.com/88)
- [원격 접속해서 시간 오래 걸리는 작업, 접속 끊어도 계속 진행되게 하기 nohup, disown, screen](https://mytory.net/archives/2340)
- [Linut, 백그라운드와 포그라운드](https://m.blog.naver.com/PostView.naver?isHttpsRedirect=true&blogId=dudwo567890&logNo=130156852012)
