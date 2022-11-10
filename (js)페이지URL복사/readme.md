# 개요
- 특정 버튼을 눌렀을 때 현재 페이지의 "링크 복사" 기능
- 또는 특정 텍스트 박스의 글자들을 복사하는 기능

이러한 기능 구현 방법에 대해서 서술한다. 


## 방법
- 핵심은 document.execCommand("copy"); 로 브라우저에서 지원하는 copy 명령어를 실행하는 것이다. 
```javascript
<script type="text/javascript">

function clip(){

	var url = '';
	var textarea = document.createElement("textarea");
	document.body.appendChild(textarea);
	url = window.document.location.href;
	textarea.value = url;
	textarea.select();
	document.execCommand("copy");
	document.body.removeChild(textarea);
	alert("URL이 복사되었습니다.")
}

</script>
```

## 출처 
- [페이지 URL 복사](https://chobopark.tistory.com/179)
