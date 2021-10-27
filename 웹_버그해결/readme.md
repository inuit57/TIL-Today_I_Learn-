# jsp <-> Java 한글 깨짐 문제 
## 상황 정리 
```
Ajax로 통신을 진행하고 있었는데 java 단에서 받아온 xml String을 jsp에서 읽어올 때
한글이 ? 로 모두 깨지는 현상이 발생하였습니다. 

JSP <-> JSP 간에 통신을 할 때는 문제가 없었는데 Spring MVC 형태로 수정하는 과정에서
UTF-8 변환이 제대로 되지 않은 것이 원인으로 보여집니다. 
```
## 해결법
- [Java 단에서 contentType 추가하기](https://despacito-pasito.tistory.com/8) 
- [인코더/디코더 활용하는 방법](https://zzznara2.tistory.com/94) 
