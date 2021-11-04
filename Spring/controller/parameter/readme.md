# 개요 
- Spring의 @Controller 에서 parameter 값들을 받아오는 다양한 방법들에 대해서 기술한다. 
- [자료 출처](https://takeknowledge.tistory.com/39)

##  @RequestParam 활용
```
// Request URL 
// http://localhost:8080/reservation/api/reservations?reservationEmail=test@naver.com 

@Controller
@RequestMapping(path = "/api")
public class ReservationsApiController {
 
    // email로 예약 내역 조회
    @GetMapping(path = "/reservations")
    public Response<List<String>> getReservations(
            @RequestParam(value = "reservationEmail",required = false) String reservationEmail) {
 
        return reservationService.getReservationByEmail(reservationEmail);
    }
}   
```


@RequestParam(value = "reservationEmail",required = false) String reservationEmail
- value : 넘어오는 parameter의 name값
- required : 선언한 parameter가 반드시 있어야 하는지 설정(기본값 : true)
- defaultValue : 넘어온 값이 없을 경우 매핑될 기본값 설정 

- 넘어와야 하는 parameter 값들이 많을 경우 하나하나 일일이 다 적어줘야 한다는 불편함이 있다. 

## @PathVariable 활용
```
// Request URL 
// http://localhost:8080/reservation/api/reservations/2 
@Controller
@RequestMapping(path = "/api")
public class ReservationsApiController {
 
    // 예약 취소
    @PutMapping(path = "/reservations/{reservationId}")
    public Reservations cancleReservations(@PathVariable(name = "reservationId") Integer reservationInfoId) {
 
        return reservationService.cancelReservationById(reservationInfoId);
    }
```
- Mapping하는 Path에 {}를 활용해 변수처럼 적어준 뒤 
- @PathVariable 어노테이션 뒤에 {} 안에 적은 변수 명을 name 속성의 값으로 넣는다.
- 그 후 이를 받을 자료형과 변수명을 옆에 선언해주면 잘 작동한다. 

### @PostMapping , @PutMapping , @GetMapping , @DeleteMapping 
- [자료출처](https://salon.tistory.com/10)
- [추가 자료(공부필요)](https://ltk3934.tistory.com/185) 
- [이미지 출처](https://javacoding.tistory.com/142)
![image](https://user-images.githubusercontent.com/24216471/140238840-d1c546b1-902f-4c9a-ad2b-bae6bf218037.png)

#### @PostMapping 
> POST 요청을 받아서 주로 데이터를 **추가/등록**할 때 사용한다. 
- CRUD의 C(Create)
- **멱등성**이 없습니다. 

#### @PutMapping 
> PUT 요청을 받아서 주로 데이터를 **수정**할 때 사용한다. 
- CRUD의 U(Update)
- POST와의 차이점은 **멱등성**에 있다. 
- HTTP 요청에서 멱등성이란 **여러 번 연속해서 호출해도 클라이언트가 받는 응답은 동일**하다는 것입니다. 
- 다시 말해서, POST는 여러 번 호출할 경우 여러 개의 새로운 값을 생성하지만 PUT, GET, DELETE 등은 항상 같은 결과를 반환한다고 이해하면 됩니다. 

#### @GetMapping
- CRUD의 R(Read)

#### @DeleteMapping 
- CRUD의 D(Delete) 



