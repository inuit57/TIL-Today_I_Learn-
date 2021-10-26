# 개요
- 실무에서 Map이라는 자료구조를 어떠한 경우에 사용하는지에 대해 기술한다. 
- 경험 위주로 작성되는 부분이므로, 다르게 사용하는 경우도 있음에 유의할 것. 


## Map<String, Object>
- 일반적으로 Key 값은 String으로 가진다. 
- 그리고 이것은 String 변수형을 그대로 key에 넣어줄 수 있음을 의미하며, 여기에서 더 나아가보자. 

### public Object function(String param) 
- String 을 인자로 받아서 Object 를 return하는 함수를 여러 번 호출하는 경우를 떠올려보자. 
- 그리고 그 결과 값들을 각각 저장한 뒤 Controller로 넘겨주는 상황일 때
- 이를 가장 적절하게 처리할 수 있는 방법은 Map 자료구조에 넣어주고 그것을 Model에 태워서 보내주는 것. 

- 예시)
```
public String starAdd(String param){ return param+"_star"; }
String[] strArr = { "aaa", "bbb","ccc" } ; 

// HashMap을 쓰는 이유 : 빠른 검색을 위해서
// LinkedHashMap : 순서가 부여된 HashMap, Map과 Set은 본래 순서가 없다. 
Map<String, Object> strMap = new HashMap<String,Object>(); 

for(String str : strArr){
  strMap.put(str,starAdd(str)) ; 
}

```

### @RequestParam HashMap<String, Object> paramMap 
- 여러 개의 request parameter들을 Map 으로 손쉽게 처리하는 방법. 
- id 값이 key로 들어가고 value 값은 value로 자동으로 Map에 저장되어서 Controller에서 바로 사용할 수 있다. 

- 단점으로는 어떤 key 값이 있는지 알기 위해서는 front에 지정한 id 값을 확인해야 하기에 유지보수가 귀찮아질 수 있다. 
- Command Object 객체를 만들어서 사용하는 쪽이 좀더 권장되는 방법이다. <br>
(* 받아오는 id(key)값과 동일한 이름의 변수들을 만든 Class를 변수로 지정하는 방법, <br>
해당 Class에는 받아올 모든 값에 대한 변수가 지정되어야 하고 getter/setter가 있어야만 한다. 


