# 개요
- 프로젝트를 진행하다보면 다양한 모양새의 JSON 데이터를 만나게 된다.
- 또한 요즘(2021년 기준) 트랜드가 JSON 형식으로 데이터를 주고 받는 일이 많다보니 익숙해질 필요가 분명 있다.

- 일반적으로는 String 형태로 json 데이터를 변환하여 넘겨주고 받은 String을 다시 json으로 parsing하여 사용한다. 

## JSON 객체 종류
- 크게 JSONObject, JSONArray , JSONElement 로 나눌 수 있다. 

1) JSONObject
    - 가장 기본적인 JSON 형태로 { {} , {} } 처럼 {}로 싸여있는 JSON 데이터를 의미한다. 
    - Map 처럼 key와 value값이 있으며 Set 자료형으로 Key들만 뽑아내는 것도 가능하다. <br>
      (이를 이용해서 key값들을 모를 때 반복문을 돌리기 좋다.)
2) JSONArray
    - List 자료형을 생각하면 쉽다. 
    - [ {} , {} ] 처럼 []로 싸여있는 JSON 데이터 형태를 의미한다. 
    - get(i) 함수를 통해서 i 번째에 해당하는 데이터를 뽑아올 수도 있으며 <br>
      JSONElement 객체와 함께 사용하여 forEach문을 돌리는 것도 가능하다.
3) JSONElement
    - JSONObject, JSONArray 클래스의 부모객체.


## 관련 함수 및 API
- 일반적으로 google에서 제공해주는 gson 라이브러리를 많이 사용하는 것으로 보인다.
- [관련자료](https://hianna.tistory.com/629)
