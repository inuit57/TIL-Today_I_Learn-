# 개요
- 프로젝트를 진행하다보면 현재 올라간 서버와 jar 파일(class 파일) 버전이 맞지 않아서 오류가 나곤 한다. 
  - 관련 오류 : UnsupportedClassVersionError 
- 확인할 수 있는 방법에 대해서 기술한다. 
- 주의할 것은 WAS 서버의 java 버전을 확인해야 한다. 현재 WAS가 올라간 서버의 java 버전이 아니다. <br>
(일반적으로는 같겠지만 그렇지 않은 경우도 있으니 ps 명령어로 어떻게 올렸는지 확인이 필요하다. ) 

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
- [오류 관련](https://mirotic91.tistory.com/34)
