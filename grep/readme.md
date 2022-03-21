# grep 명령어 제외 
- 특정 프로세스를 ps 명령어를 통해서 찾을 때 grep도 같이 나오지 않도록 하는 방법

```
ps -ef | grep $process_name | grep -v "grep"
```
하지만 script 로 이것을 실행하게 될 경우 문제가 생길 수 있다.
```
ps ax | grep $process_name | grep -v "grep" | grep -v $0
```
뒤에 "grep -v $0" 를 추가해주면 해당 스크립트를 실행시키는 프로세스는 감지되지 않는다. 
```
ps ax | grep $process_name | grep -v "grep" | grep -v $0 | awk '{print $1}'
```
- awk '{print $(숫자)}' 를 사용할 경우 출력되는 항목에서 원하는 대상을 추출해낼 수 있다. 
- $1로 할 경우 프로세스 ID 값을 추출할 수 있다.  

