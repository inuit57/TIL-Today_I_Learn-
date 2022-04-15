# 개요
- 도커 사용법에 대해서 정리해본다. 


## docker 컨테이너 구축
```sh
 docker run -d  -it --publish 39092-39094:39092-39094 --volume /data1/v7_docker/cjn:/app/Z --name v7_cjn ubuntu /bin/bash 
```
> docker run <br>
> -d   : detached mode, 백그라운드 실행  <br>
> -it  : input terminal, 터미널 입력 옵션 <br>
> --publish 39092-39094:39092-39094 : 포트 포워딩 설정 <br>
> --volume /data1/v7_docker/cjn:/app/Z  : 마운트할 디렉토리 설정 <br>
> --name [컨테이너명] : 이름 설정 <br>
> ubuntu   : OS 설정 <br>
> /bin/bash : 쉘 설정 <br>

## docker 컨테이너 실행
> docker exec -it [컨테이너명] /bin/bash

## docker 컨테이너 중지 및 삭제
> docker stop [컨테이너명] <br>
> docker rm [컨테이너명]
