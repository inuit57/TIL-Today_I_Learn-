# 개요 
- 오프라인 환경(혹은 내부망)에서 스프링 프로젝트 세팅하는 방법에 대해서 기술한다. 
- 우선 외부에서 작업한 스프링 프로젝트 파일을 WAR로 감싸서 넣어준다. 
- 하지만 그렇게만 한다고 해서 스프링이 되는 것이 아니다. 추가로 설정해야 하는 것이 필요하다. 

- 스프링 설정은 원래 까다롭다. 못한다고 슬퍼하거나 좌절할 필요는 없다. 


## xsd 오류
- 오류 예시
```
org.xml.sax.SAXParseException; lineNumber: 12; columnNumber: 101; schema_reference.4: 스키마 문서 '
https://www.springframework.org/schema/beans/spring-beans.xsd
' 읽기를 실패했습니다. 원인: 1) 문서를 찾을 수 없습니다. 2) 문서를 읽을 수 없습니다. 3) 문서의 루트 요소가 <xsd:schema>가 아닙니다.
```
- 이런 식으로 root-context.xml 또는 servlet-context.xml 에서 오류가 발생한다. 
- 원인은 외부망 환경이라면 설정된 주소에 접근해서 받아오는 것이 가능하지만 내부망 환경에서는 그럴 수 없기 때문이다. 
```
xsi:schemaLocation 에서 http://www.springframework.org/schema/beans에 해당하는 xsd를 
https://www.springframework.org/schema/beans/spring-beans.xsd 에서 받아오고 있다. 
그러니 인터넷이 연결이 안 되면 못 받아온다.
```

### 해결 방법
```
모든 xsd는 해당 jar에 포함되어 있고, 
배포할 때 정상적으로 jar를 가져갔다면 해당 jar 안에서 xsd를 읽어들이는 식으로 처리할 수 있다.

예를 들어 spring-beans.xsd는 spring-beans-5.0.7.RELEASE.jar에 포함되어 있다.
(org.springframework.beans.factory.config.spring-beans.xsd)

그리고 META-INF에 spring.schemas를 보면
```
![image](https://user-images.githubusercontent.com/24216471/209499804-ce1ba114-45f6-4e5f-8b4e-5b3d58efe7e2.png)
```
이렇게 키값 형식으로 매칭 시키고 있다.
http:.........= 옆에 나와있는 org/...부터 원하는 버전으로 복사해서 xsi:schemaLocation에 넣어준다.
```

```
xsi:schemaLocation="
http://www.springframework.org/schema/beans classpath:org/springframework/beans/factory/xml/spring-beans.xsd
"
```
- 비슷한 방식으로 servlet-context.xml 에서도 일어나는 오류를 이렇게 잡아주면 된다. 

### 출처
- [[스프링][Spring][offline]인터넷 없이 오프라인 내부망에서 xsd 읽어오기](https://12teamtoday.tistory.com/83)
