# 개요
- 화면에 출력하면서 동시에 파일에도 해당 내용을 기록할 수 있는 명령어, tee 에 대해서 소개한다. 


## 사용법 
### 기존 파일에 출력하는 방법 ( > 연산자 활용)
```sh 
$> echo hello!world > output.txt 
```
- 결과 : 화면 출력 X, output.txt 파일 생성되고 해당 내용 기록됨

### tee 명령어 사용 
```sh
$> echo hello!world | tee output.txt 
```
- 결과 : 화면에도 출력, ouptput.txt 파일 생성되고 해당 내용 기록됨 
