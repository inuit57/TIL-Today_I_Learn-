# 개요
- Window 환경 및 linux 환경에서 특정 IP , 특정 PORT로 접속 가능여부를 확인하는 방법에 대해 기술한다. 

## Windows 
- cmd 창에서 명령어를 통해서 작업을 진행한다. 
### 내 IP 확인
```
> ipconfig 
```
`
### IP check
```
> ping (IP address)
```

### Port check
```
> telnet (IP address) (Port)
```
- 연결이 성공적으로 진행된다면 해당 IP의 해당 PORT는 열려있다고 볼 수 있다. 


## Linux
- 콘솔 창에서 명령어를 통해서 확인할 수 있다. 
### 내 IP 확인
```
$ ifconfig
```


# 자료참고
- [리눅스 IP 확인(CentOS)](https://suzxc2468.tistory.com/165) 

## 추가 정리 필요
- 리눅스 IP , port 관련 
- 
