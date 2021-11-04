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


