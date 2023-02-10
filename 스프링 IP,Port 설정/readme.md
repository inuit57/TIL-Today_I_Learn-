# 개요
- 스프링 서버의 IP,Port 를 임의로 설정하는 방법에 대해서 기술한다.
- 기존설정은 IP는 localhost , port 는 8080을 사용하게 되어있다. 


## 설정 방법
- application.properties 파일을 수정해준다.
```
server.address=0.0.0.0 // 또는 자신의 IPv4 주소
server.port=8080
```

## 랜덤포트로 변경
```
server.port=0
```


# 자료참고
- [[Spring Boot] 스프링 부트 외부 접속 안되는 문제](https://bestinu.tistory.com/m/51)
- [랜덤 포트 변경](https://hoit1302.tistory.com/81)
