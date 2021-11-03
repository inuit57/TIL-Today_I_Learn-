# 개요
- 리눅스 콘솔 상에서 명령어를 치는 등의 작업을 수행하다가 오타를 수정하고 싶은 상황에서 <br>
  백스페이스를 눌렀는데 글자가 지워지지 않고 이상한 문자(^H,^?)가 출력되는 경우의 해결책을 작성한다. 

- 보통 ^?는 delete 키, ^H는 backspace키 입니다. 
  
## 방법1 : Ctrl + Backspace
- 특별한 설정 없이 곧바로 문자를 지우려고 한다면 Ctrl키와 함께 backspace키를 누르면 지워집니다. 

## 방법2 : stty 명령어 사용
```
$ stty erase ^H(또는 ^?) 
```
- 이 방법을 사용할 경우, 현재 로그인되어있는 상태에서는 백스페이스를 누르더라도 이상한 문자가 출력되지 않고 정상적으로 지워집니다. 


## 방법 3 : 설정파일 수정
```
## 모든 사용자에게 설정내용 적용
## /etc/profile 에 stty erase ^H 를 등록하기

echo "stty erase ^H" >> /etc/profile

## 설정 후 재부팅할 경우 적용됩니다.
```
```
## 특정 사용자에게 설정내용 적용
## $HOME/.profile 에 stty erase ^H 를 등록하기 

#> echo "stty erase ^H >> $HOME/.profile 
#> source .bash_profile 

## source 명령어를 사용하면 재접속하지 않더라도 스크립트 파일에 변경된 내용을 곧바로 적용가능하다. 
```

# 추가 공부
- stty : 터미널 설정 명령어
- 문법) stty [설정명령] [설정할 키보드 key] 
- 예시) stty erase ^H


# 자료 참고
- [ctrl+backspace](https://syuda.tistory.com/151)
- [stty설정](https://keefojifo.tistory.com/31) 
- [source명령어](https://klero.tistory.com/entry/source-%EB%AA%85%EB%A0%B9%EC%96%B4%EB%9E%80) 

