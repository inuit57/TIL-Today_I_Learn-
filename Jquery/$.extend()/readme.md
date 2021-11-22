# 자료출처
- [자료출처](https://damedame.tistory.com/entry/jQueryextend-%ED%95%A8%EC%88%98-%EC%82%AC%EC%9A%A9-%EB%B0%A9%EB%B2%95)

# 개요
- JQuery.extend() 함수는 복수의 오브젝트를 합쳐서(merge) 되돌려 주는 함수입니다.

## 사용법
```javascript 

  jQuery.extend(target[, object1][, objectN])

```

## 예시
```javascript 

var a = {
    id: 1,
    name: 'TAM'
};
 
var b = {
    name: 'TAM-new',
    hobby: 'football'  
};
 
$.extend(a, b);
 
console.log(a);
// 결과:
//  {
//      id: 1,
//      name: "TAM-new",
//      hobby: "football"
//  }

```
- $.extend(a, b) 를 실행하면 a에 b를 합쳐 줍니다.
- 같은 프로퍼티가 존재 한다면 b의 값으로 덮어쓰기를 하며 b에 있는 프로퍼티가 새로운 값이라면 추가를 합니다.



