# 개요 
- javascript 에서 특정 객체를 name 등의 속성으로 조회해올 때 유용한 기법에 대해 서술한다. 

## 사용법 
### 전방일치
```
$("input[name^='value']")
```
### 포함하는 단어
```javascript
$("input[name*='value']")
```
### 공백포함해서 포함하는 단어
```javascript
$("input[name~='value']")
```
### 후방일치
```javascript
$("input[name$='value']")
```
### 일치하지 않는
```javascript
$("input[name!='value']")
```
### ex)
```javascript
$("tr[class^='className']") tr태그로 시작하는 것에서 클래스이름이 className으로 시작하는 객체
```

# 출처 
- [javascript 일치하는 name 객체](https://joelweon.github.io/2018/05/17/js_name.html)
- [jQuery API Document](https://api.jquery.com/category/selectors/attribute-selectors/)
