# 개요
- 쉘 스크립트에서 오늘 날짜를 가져오는 방법에 대해서 서술한다. 
- 오늘 날짜에 생성된 파일이라던지 혹은 오늘 날짜를 넣어서 로그 파일명 등을 만들 때 사용하자. 


## 방법
- date 명령어를 사용한다. 
```sh
#!/bin/bash 

today=$(date "+%Y%m%d")
echo ${today}

echo "sample_${today}.txt"  ## 문자열과 붙여서 사용
```

## 오늘 외의 날짜 구하기 
- [자료 출처](https://mydb.tistory.com/217) 

### 과거(리눅스)
- "-d" 옵션 뒤에 기간 정보 + ago 를 적어서 사용해준다. 
```sh
date -d 'yesterday'		# 어제
date -d '1 day ago'		# 1일전 == 어제
date -d '2 day ago'		# 2일전
date -d '35 day ago'		# 20일전
date -d '1 week ago'		# 1주일전
date -d '2 month ago'		# 1달전
date -d '3 year ago'		# 3년전
date -d '10 second ago'		# 10초전
date -d '20 minute ago'		# 20분전d
ate -d '30 hour ago'		# 30시간전
date -d '3 year 7 month ago'	# 3년 7개월전

```

### 과거(UNIX)
- 유닉스(UNIX)는 다르게 접근해야 한다. 
- UNIX는 Time Zone이라고 해서 지역별 시간대를 가지고 있습니다. 
- 한국은 표준시에 대해서 TZ=KST-9 입니다. 하지만 하루전으로 가기 위해서는 24시간을 더해준답니다. 
- [자료 출처](https://ls-altr.tistory.com/7)

```sh 

yesterday = `TZ=KST+15; date +%Y%m%d`
echo ${yesterday} 

```


### 미래 
- 과거 옵션에서 ago만 빼면 된다. 
```sh 
date -d 'tomorrow'		# 내일
date -d '1 day'			# 1일후 = 내일
date -d '2 day'			# 2일후
date -d '35 day'			# 20일후
date -d '1 week'		# 1주일후
date -d '2 month'		# 1달후
date -d '3 year'		# 3년후
date -d '10 second'		# 10초후
date -d '20 minute'		# 20분후
date -d '30 hour'		# 30시간후
date -d '3 year 7 month'		# 3년 7개월후
```

