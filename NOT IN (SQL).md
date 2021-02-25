출처 : https://aljjabaegi.tistory.com/459


IN, NOT IN 문 안에 서브쿼리 사용시에는 주의 하셔야 될 경우가 있습니다. <br>
NOT IN문 서브쿼리의 결과 중에 NULL이 포함되는 경우 <B>데이터가 출력되지 않기 때문에</B><br>
조회 컬럼에 IS NOT NULL 조건을 주셔야 합니다. <br>



