# @PostMapping , @PutMapping , @GetMapping , @DeleteMapping 
- [자료출처](https://salon.tistory.com/10)
- [추가 자료(공부필요)](https://ltk3934.tistory.com/185) 
- [이미지 출처](https://javacoding.tistory.com/142)
![image](https://user-images.githubusercontent.com/24216471/140238840-d1c546b1-902f-4c9a-ad2b-bae6bf218037.png)

## @PostMapping 
> POST 요청을 받아서 주로 데이터를 **추가/등록**할 때 사용한다. 
- CRUD의 C(Create)
- **멱등성**이 없습니다. 

## @PutMapping 
> PUT 요청을 받아서 주로 데이터를 **수정**할 때 사용한다. 
- CRUD의 U(Update)
- POST와의 차이점은 **멱등성**에 있다. 
- HTTP 요청에서 멱등성이란 **여러 번 연속해서 호출해도 클라이언트가 받는 응답은 동일**하다는 것입니다. 
- 다시 말해서, POST는 여러 번 호출할 경우 여러 개의 새로운 값을 생성하지만 PUT, GET, DELETE 등은 항상 같은 결과를 반환한다고 이해하면 됩니다. 

## @GetMapping
- CRUD의 R(Read)

## @DeleteMapping 
- CRUD의 D(Delete) 
