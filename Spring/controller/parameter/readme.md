# 개요 
- Spring의 @Controller 에서 parameter 값들을 받아오는 다양한 방법들에 대해서 기술한다. 
- [자료 출처](https://takeknowledge.tistory.com/39)
- [자료 출처2](https://gs.saro.me/dev?tn=556)

## HttpRequest로 받아오는 방법
```
@GetMapping("/temp")
String temp(HttpServletRequest request)
{
    String a = request.getParameter("a");
    String b = request.getParameter("b");
    
    System.out.println("a : " + a);
    System.out.println("b : " + b);

    return "none";
}
```
```
콘솔결과 : /temp?a=1&b=2
a : 1
b : 2
```

## Map으로 가져오는 방법
```
@GetMapping("/temp")
String temp(@RequestParam Map<String, String> param)
{
    String a = param.get("a");
    String b = param.get("b");

    System.out.println("a : " + a);
    System.out.println("b : " + b);

    return "none";
}
```
```
콘솔결과 : /temp?a=1&b=2
a : 1
b : 2
```
- 자동으로 name을 key값으로 value를 value값으로 하여 Map에 저장합니다.

## Model 클래스를 통한 직접 매칭 
```
@GetMapping("/temp")
String temp(Abc abc)
{
    System.out.println("a : " + abc.getA());
    System.out.println("b : " + abc.getB());
    
    return "none";
}

@Getter @Setter
static public class Abc
{
    String a;
    int b;
}
```
- 자동으로 모델 클래스에 값들을  저장해줍니다. 

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

## @RequestBody 활용
- HTTP 요청의 Body 부분을 java 객체로 받을 수 있게 해주는 어노테이션.
- 주로 json을 받을 때 활용한다. 

- json 객체의 데이터 형태와 일치하도록 java class를 만든 뒤 해당 객체를 파라미터를 담을 변수로 적어주면 고스란히 java 객체 안에 담긴다. 

```
// json 데이터
{
    "id" : "wisenut",
    "uid" : 59 
}

@Getter @Setter
public class WisenutParam{
    private String id ; 
    private int uid; 
}

@Controller
@RequestMapping(path = "/api")
public class WisenutTestController {
 
    @PostMapping(path = "/wisenutParam")
    public String setReservations(@RequestBody WisenutParam wisenutParam) {
        //TO DO 
    }
```
