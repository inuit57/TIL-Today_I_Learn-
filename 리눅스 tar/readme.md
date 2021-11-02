# 개요
- tar 라는 명령어를 보통 압축하는 명령어로 알고 있는 경우가 많은데, 정확하게 말하면 "용량을 줄이는 압축"은 아니다. 
- 보다 정확하게 설명한다면 이것은 여러 개의 파일을 하나의 파일로 합치는 기능을 수행한다고 보면 됩니다. 
- 이후 이렇게 만들어진 파일을 gzip 또는  bzip2 방식 등을 이용해서 용량을 줄이는 압축을 진행할 수 있습니다. 

## tar 명령어 옵션
```
tar [OPTION...] [FILE]... 
-f : 결과물로 나올 아카이브 파일 이름을 지정 (기본 옵션) 
-p : 파일 권한을 지정
-v : 묶거나 푸는 과정을 화면에 출력
-C : 경로를 지정

-c : tar 아카이브 생성. 기존 아카이브 덮어 쓰기. (파일 묶을 때 사용) 
-x : tar 아카이브에서 파일 추출. (파일 풀 때 사용) 

-z : gzip 방식으로 압축하거나 해제함
-j : bzip2 방식으로 압축하거나 해제함
```

## 압축하기
### tar 압축
```
$ tar -cvf [FILE_NAME.tar] [TARGET_FOLDER] 

예) tar -cvf test.tar ./* 
```

### tar.gz 압축
```
$ tar -cvf [FILE_NAME.tar.gz] [TARGET_FOLDER] 
```

### zip 압축
```
$ zip  [FILE_NAME.zip] [TARGET_FOLDER] 
```

## 압축 풀기
```
$ tar -xvf [FILE_NAME.tar] 
$ tar -zxvf [FILE_NAME.tar.gz] 
```


