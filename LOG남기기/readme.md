# 개요
- 디버깅 또는 로그조차 찍어보지 않고 선배들이나 동기들한테 물어보는 핑거프린세스가 되지 말자. 
- 코더가 아닌 프로그래머가 되기 위해서는 기본적으로 프로그램이 어떻게 흘러가는지 정도는 알아야하며<br>
  그것을 확인하는 가장 좋은 방법은 함수 호출이 이뤄지는 곳마다 log를 찍어가면서 확인하는 것이 좋다. 

- java에서 log 기능을 제공해주는 다양한 함수들과 클래스들이 존재하지만, 간단하게 내가 사용해본 것들 위주로 정리를 해보고자 한다. 
  
## log4j 
- [자료참고](https://cofs.tistory.com/354)
```
@Controller
class MainController { 

  private static final Logger LOGGER = Logger.getLogger(MainController.class); //정의
  
  (...)
  
  public static void main(String[] args){
    LOGGER.debug("test"+args[0]) ; 
  }
```

## slf4j
- [자료참고](https://gmlwjd9405.github.io/2019/01/04/logging-with-slf4j.html) 

```
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
public class HelloWorld {   
    public static void main(String[] args) {      
        Logger logger = LoggerFactory.getLogger(HelloWorld.class);  
        logger.info("Hello World");
    }
}
```
- log4j 보다 slf4j 를 보다 많이 사용하는 이유 : slf4j가 좀더 보편적으로 사용될 수 있도록 만들어져있어서 slf4j 에서 다른 logger로 바꾸기 쉽다. 


### 추가 공부
- Logger.getLogger()를 쓰지 않고 LoggerFactory.getLogger()를 사용하는 이유? 
