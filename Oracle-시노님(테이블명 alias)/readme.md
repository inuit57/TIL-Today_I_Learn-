# 개요 
- Oracle 에서 사용하는 테이블 ALIAS 기능인 "SYNONYM"에 대해 공부한 내용을 정리한다. 
- 테이블 소유자가 다른 경우, {소유자명}.{테이블명} 의 형식으로 접근하게 되는데 쿼리를 작성할 때 불편함이 존재할 수 있습니다. 


## SYNONYM 이란? 
- 쉽게 말해서 ALIAS 같이 이름을 줄여주는 역할을 한다라고 생각하면 된다.
- 시노님(Synonym)은 테이블의 이름을 설정해 주는것이다.
- 보통 다른 유저의 객체(테이블, 뷰, 프로시저, 함수, 패키지, 시퀀스 등)를 참조할 때 많이 사용한다.
- 실제로 SYNONYM을 이용하는 이유는 다른 유저의 객체를 사용할 때 유저의 이름과 객체의 실제 이름을 사용하는데, 그 두 개를 감춤으로써 **데이터베이스의 보안을 개선**하기 위해 사용된다.

## SYNONYM 생성
```sql 
CREATE [ PUBLIC ] SYNONYM [ 시노님 이름 ]
FOR [ 객체 이름 ]

* PUBLIC은 모든 사용자가 접근이 가능하도록 설정해주는 것이다.
* PUBLIC을 선언해주지 않으면 기본값으로 PRIVATE가 선언된다.
```

## SYNONYM 삭제
```sql 
DROP SYNONYM [ 시노님 이름 ] ;
```
