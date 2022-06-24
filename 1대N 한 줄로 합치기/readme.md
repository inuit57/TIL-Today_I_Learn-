# 개요 
- 여러 개의 DB 테이블들을 JOIN 하다보면 1:N 관계의 테이블을 JOIN 해야하는 경우가 발생한다. 
- 예를 든다면 여러 부서들에 대한 정보를 취합하고 있는데 그 부서에 속한 인원들을 JOIN해서 가져와야 하는 경우가 있겠다. 

- 이런 상황에서 부서명으로 그룹화해서 부서에 속한 인원들을 구분자로 처리해서 한 줄로 가져오면 좋다. 
- 그리고 이미 훌륭한 DBA 분들께서는 그런 함수들을 SQL 내장함수로 지원해주시고 있다. 


# 사용법 
## MYSQL 
```sql 
SELECT DIR_NM, 
       GROUP_CONCAT(user_id SEPARATOR '^') AS users 
  FROM user_info
 GROUP BY DIR_NM
```

## ORACLE 
```sql 
SELECT DIR_NM, 
       LISTAGG(user_id, '^') WITHIN GROUP(ORDER BY user_id) 
  FROM user_info
 GROUP BY DIR_NM
```


### 출처 
-[출처](https://developyo.tistory.com/37)
