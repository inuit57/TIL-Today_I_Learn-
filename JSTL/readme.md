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
