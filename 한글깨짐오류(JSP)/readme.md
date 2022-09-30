# 개요
- 웹 개발을 진행하면서 마주할 수 있는 한글 깨짐 현상에 대한 해결책을 소개한다. 

## HTML / JSP 문서 자체에서 한글 깨짐
- 해결방법 : 
```
<head> 부분에 <meta charset="UTF-8"> 를 추가해준다.
```  
## get 방식의 표현에서 한글 깨짐
- 해결방법 : 
```
상단의 <%@ page %> 설정에서 pageEncoding="utf-8" 로 변경해준다. 
```  
## 주소줄로 get 방식 전송을 하는데 한글 깨짐
- 예) 
  ```
  localhost:8080/test/test.jsp?param=테스트 
  로 보냈는데 화면상에서 param을 출력하려고 하니까 한글이 깨지는 현상
  ```
- 해결방법 : tomcat의 server.xml 파일을 수정한다. 
 ```
  <Connector ...> 부분에  URIEncoding="utf-8" 을 추가해준다. 
  
  * 기본적으로 URIEncoding 설정이 되어 있지 않음.- 디볼트 값은 : ISO-8859-1 
```

## 참고자료
- [ [jsp]상황별 한글 깨짐 해결 ](https://m.blog.naver.com/alcmskfl17/221913121686)
- [ [Encording] Server.xml 과 URIEncording ](https://seongtak-yoon.tistory.com/20)
