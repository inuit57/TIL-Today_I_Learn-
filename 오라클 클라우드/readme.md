# 방화벽(포트) 설정 관련
1) 오라클 클라우드 사이트에서 설정하기
- https://ldne.tistory.com/247

![image](https://user-images.githubusercontent.com/24216471/160729731-8bcbd7ec-0420-45fd-a16c-c673012c8219.png)

![image](https://user-images.githubusercontent.com/24216471/160729780-6dac8e8f-35d0-48d2-a50e-84e152900d17.png)


![image](https://user-images.githubusercontent.com/24216471/160729569-7529387d-cef5-4aaa-91f6-e60a641fdd50.png)
![image](https://user-images.githubusercontent.com/24216471/160729629-6546368e-61f1-46e5-aad0-d1f4a76d3290.png)

이렇게 한 뒤 cmd 에서 오라클VM IP로 ping을 날려서 테스트해보면 정상적으로 받아오는 것을 확인할 수 있다. 

![image](https://user-images.githubusercontent.com/24216471/160729805-ed166e26-d8fa-4f5d-ac2d-61f083036917.png)

추가를 진행해주면 된다. 

2) VM 내부 방화벽 설정하기
- firewall-cmd  혹은 iptables 로 설정되어있을 듯 하다. 
- 구글링해서 추가로 작업해주거나 내부적으로만 사용한다면 방화벽을 아예 내려버리면 된다. 


## 기타
- centOS 8 버전은 뭔가 버그가 있어보입니다. ( yum 명령어 사용시에 )
- 그렇기에 가급적이면 사용하지 말고 centOS 7 버전을 사용하거나 합시다. 
