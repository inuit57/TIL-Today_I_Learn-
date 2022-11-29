# 개요
- 프로젝트를 진행하다보면 현재 올라간 서버와 jar 파일(class 파일) 버전이 맞지 않아서 오류가 나곤 한다. 
- 확인할 수 있는 방법에 대해서 기술한다. 

## 방법
```
$> javap -verbose 클래스명.class | find "version"
```

## 주요 JAVA 버전
|버전 | 숫자|
|----|-----|
|1.6 | 50 |
|1.7 | 51 |
|1.8 | 52 |


## 출처 
- [출처](https://coding-factory.tistory.com/836) 
