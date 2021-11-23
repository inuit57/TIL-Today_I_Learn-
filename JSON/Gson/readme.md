# 개요
- json 데이터를 다루는데 많이 사용되곤 하는 구글에서 제공하는 라이브러리입니다. 
- [자료모음](https://github.com/inuit57/TIL-Today_I_Learn-/issues/3)

## 사용법
- 우선은 JSON 데이터를 다른 자료형으로 변환 또는 반대의 방향으로 진행하는 함수에 대해서 다뤄본다. 
- 이 밖에도 JSON 데이터를 다룰 수 있는 다양한 함수들을 제공하고 있으니 추가적으로 공부를 진행하도록 하자. 

## JSON -> 다른 자료형 
- Gson의 fromJson( String, Type ) 함수를 사용한다. 
- 인자로는 String 형태로 표현된 Json 데이터, 그리고 변환할 Type명을 넣어준다. 
- 예시로는 아래와 같다. 
```java
Gson gson = new Gson(); // Gson 객체 생성

CommonVO vo = gson.fromJson(jsonObject.toString(), CommonVO.class);
// JSON 에 선언되어있는 key 와 value를 자동으로 
// 해당 VO 에 선언된 변수들에 매핑시켜서 값을 채워준다. 
```

- Type 클래스를 사용해서 Map, List 형의 데이터로도 변환해주는 것이 가능하다. 
```java

String jsonText = jsonTest.toString() ; // json 데이터

Gson gson = new Gson();

Type type = new TypeToken<ArrayList<Map<String, String>>>() {}.getType();
// TypeToken 을 사용해서 이러한 java 자료구조를 하나의 Type으로 정의할 수 있습니다. 

ArrayList<Map<String, String>> data = gson.fromJson(jsonText, type);
// 이후로는 일반적인 클래스에 넣어주는 것과 동일하게 작성하면 됩니다. 
// 대신, 두번째 인자로 저희가 정의해준 Type을 넣어줍니다. 
```

## 다른 자료형 -> JSON 
- toJson( Object ) 함수를 사용하면 아주 손쉽게 json 객체로 변환이 가능합니다. 
```java 
TestObject testObj = new TestObject("test", 20) ; // Test Object. 

Gson gson = new GsonBuilder.Create() ; 

String jsonData = gson.toJson(testObj) ; // json 데이터로 변환
```
