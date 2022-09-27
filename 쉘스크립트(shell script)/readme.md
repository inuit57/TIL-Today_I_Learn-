
# 개요 
- 쉘스크립트 관련하여 작성한다. 

## 작성법
```sh
#!/bin/sh 

```
- 시작은 이렇게 쉘스크립트임을 명시해준다. 
- chmod 755 옵션을 줘서 쉘스크립트를 실행할 수 있도록 해준다. 


## 연속적으로 인자 받기 
```sh
#!/bin/sh 

T1=$1
if [ "$#" != "0" ]; then shift; fi  # 만약 첫번째 인자 값이 있다면 shift 한다. 
T2=$1

echo $T1
echo $T2

## usage
# test.sh p1 p2 

## result 
# p1
# p2
```

