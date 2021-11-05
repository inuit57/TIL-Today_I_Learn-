# 개요
- virtual box에 CentOs 7 버전을 설치하다가 발생한 네트워크 관련 이슈에 대한 기록 
- [자료출처](https://m.blog.naver.com/theswice/221375000780) 


## IP 관련 설정
- ONBOOT 를 Yes로 둘다 설정해줘야 한다. 
- 
```
$ vi /etc/sysconfig/network-scripts/ifcfg-enp0s3
onboot=yes

$ vi /etc/sysconfig/network-scripts/ifcfg-enp0s8
TYPE=Ethernet
PROXY_METHOD=none
BROWSER_ONLY=no
BOOTPROTO=none
DEFROUTE=yes
IPV4_FAILURE_FATAL=no
IPV6INIT=yes
IPV6_AUTOCONF=yes
IPV6_DEFROUTE=yes
IPV6_FAILURE_FATAL=no
IPV6_ADDR_GEN_MODE=stable-privacy
NAME=enp0s8
UUID=a4d7c7a8-54ee-4ce0-8994-9932e2b6a8fc
DEVICE=enp0s8
ONBOOT=yes
IPADDR=192.168.56.105
PREFIX=24
GATEWAY=192.168.56.1
IPV6_PRIVACY=no
```

## 도메인 관련 설정
```
$ vi /etc/resolv.conf
nameserver 111.118.0.1
nameserver 111.118..0.11
```
- HCN 의 DNS 서버 주소이다. 
- 다른 통신사의 주소를 쓰고 싶다면 [여기](https://jjangfree.tistory.com/2223)를 참고


## 네트워크 재시작
```
$ systemctl restart network
```

## 테스트
```
$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=115 time=41.7 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=115 time=40.6 ms
```
