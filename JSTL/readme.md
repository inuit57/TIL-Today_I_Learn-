# JSTL 동적 변수 설정

```
<c:forEach items="${COLLECTIONS }" var="col_name" >
          <li><a class="col_list" id="${col_name }" href="#none" onclick="javascript:doCollection('${col_name }');">                  	
          ${col_name }
          <span>
          <c:set var="curr_collect" value="${col_name}_cnt"/>
          <c:set var="curr_cnt" value="${requestScope[curr_collect]}"/>
          <c:if test="${ '0' ne curr_cnt }">
            (${curr_cnt })
          </c:if>
          </span></a></li>						
</c:forEach>              
```        

<c:set> 태그와 requestScope[ name ] 을 활용하면 가능하다. 


# JSTL - HTML 태그 적용하는 법
[자료참고](https://needjarvis.tistory.com/51)
```
<c:out value="${ref_print}" escapeXml="false" />
```
- 간단하게 escapeXml="false" 옵션을 주는 것만으로 HTML 태그로 인식하여 동작하게끔 만들어줄 수 있다.
- 만약 설정해주지 않을 경우, string으로 인식해서 출력해준다. 

# JSTL import 
- <%@include %> , <jsp:include> 와 동일하게 현재 페이지에 다른 페이지를 추가한다. 

## <%@ include %> 
- 정적인 방식 : 먼저 페이지들을 추가한 뒤에, 컴파일을 수행하고 같이 출력해준다. 
- 변수들이 모두 공유된다. 
- 현재 프로젝트 외부에 존재하는 페이지에 대해서는 접근할 수 없다. 

## < jsp:include >
- 동적인 방식 : 각각 컴파일 해준 뒤, 실행 결과를 합쳐서 출력한다. 
- 변수들이 공유되지 않으므로 파라미터로 넘겨줘야만 한다. ( <c:param> 을 주로 사용한다.)
- 현재 프로젝트 외부에 존재하는 페이지에 대해서는 접근할 수 없다. 

## <c:import>
- 동적인 방식 : 각각 컴파일 해준 뒤, 실행 결과를 합쳐서 출력한다. 
- 변수들이 공유되지 않으므로 파라미터로 넘겨줘야만 한다. ( <c:param> 을 주로 사용한다.)
- 현재 프로젝트 외부에 존재하는 페이지에 대해서도 접근할 수 있다.. 
 
# 조건문 
## <c:if> 
- if문과 동일하게 작동하지만 차이점이라면 else 문이 없다. (따로 if문으로 적어줘야 한다.)
- 숫자 값을 EL 표현식 안에서 비교를 수행하려고 한다면 작은 따옴표(')로 묶어서 표시해줘야만 한다. 

## <c:choose> ~ <c:when>
- 일종의 switch ~ case 문과 유사한 기능을 수행하는 구문.
- <c:choose>태그로 감싼 틀 안에 여러 개의 <c:when> 태그를 사용가능하다. 
- 각각의 <c:when> 태그들은 <c:if>와 동일하게 조건을 설정하고 일치하는 경우 내부의 동작을 수행한다. 


