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
