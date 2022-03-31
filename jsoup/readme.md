# 개요
- 웹크롤링에 사용되는 jsoup 라는 것에서 사용하는 표현식 등에 대해서 정리한다. 

# 참고 사이트
- [jsoup 해볼 수 있는 사이트](https://try.jsoup.org/)
- [jsoup Selector Docs](https://jsoup.org/apidocs/org/jsoup/select/Selector.html)

## 선택기 구문
- 찾아보면 굉장히 많은데 그 중에서 쓸만한 것들만 정리한다. 

1) : 은 중첩해서 사용가능하다.
```
td:not(#first-child):not(.description)
```

