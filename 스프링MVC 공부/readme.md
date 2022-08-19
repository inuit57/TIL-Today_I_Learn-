# 개요 
- 스터디를 진행하기에 앞서 스프링 MVC의 구조에 대해서 복습한다. 

![image](https://user-images.githubusercontent.com/24216471/185538922-43904dd6-acdd-42c3-a4e0-fc0e93c54e49.png)
(출처: 김영한님의 스프링 MVC 강의자료) 

## DispatcherServlet 
- 스프링 MVC도 Front Controller 패턴으로 구현되어 있다. 
- DispatcherServlet이 바로 Front Controller에 해당된다. 

- DispatcherServlet 도 부모클래스에서 HttpServlet을 상속받고 서블릿으로 동작한다. 
- 스프링 부트는 Dispatcher Servlet 을 서블릿으로 자동으로 등록하면서 모든경로(urlPattern="/")에 대해서 매핑한다. 

- 예외처리, 인터셉터 기능은 제외하고 생각하자
- service()를 시작으로 여러 메서드가 호출되면서 DispatchreServlet.doDispatch()가 호출된다. 

### FrontController 패턴 특징
- 프론트 컨트롤러 서블릿 하나로 클라이언트의 요청을 모두 받음
- 프론트 컨트롤러가 요청에 맞는 컨트롤러를 찾아서 호출한다.
- 입구를 하나로 통일
- 공통 처리가 가능해진다. 
- 프론트 커늩롤러를 제외한 나머지 컨트롤러는 서블릿을 사용하지 않아도 된다. 

### DispatcherServlet.doDispatch() 
- 동작순서
  - 핸들러 조회 : 핸들러 매핑을 통해 요청 URL에 매핑된 핸들러(컨트롤러)를 조회한다.
  - 핸들러 어댑터 조회 : 핸들러를 실행할 수 있는 핸들러 어댑터를 조회한다.
  - 핸들러 어댑터 실행 : 핸들러 어댑터를 실행한다. 
  - 핸들러 실행 : 핸들러 어댑터가 실제 핸들러를 실행한다. 
  - ModelAndView 반환 : 핸들러 어댑터는 핸들러가 반환하는 정보를 ModelAndView로 변환해서 반환한다.
  - ViewResolver 호출 : 뷰 리졸버를 찾고 실행한다. 
  - View 반환 : 뷰 리졸버는 뷰의 논리 이름을 물리이름으로 바꾸고 랜더링 역할을 담당하는 뷰 객체를 반환한다. 
  - 뷰 랜더링 : 뷰를 통해서 뷰를 랜더링한다.


### HandlerMapping
```
0 = RequestMappingHandlerMapping : 애노테이션 기반의 컨트롤러인 @RequestMapping에서 사용
1 = BeanNameUrlHandlerMapping : 스프링 빈의 이름으로 핸들러를 찾는다
```

### HandlerAdapter
```
0 = RequestMappingHandlerAdapter : 애노테이션 기반의 컨트롤러인 @RequestMapping 에서 사용 
1 = HttpRequestHandlerAdapter : HttpRequestHandler 처리 
-- 2 = SimpleControllerHandlerAdapter : Controller 인터페이스 (애노테이션 X, 과거에 사용) 처리 
```
