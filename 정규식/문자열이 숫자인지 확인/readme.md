# 개요
- 문자열이 숫자만으로 구성되었는지 확인하는 방법에 대해서 정리한다. 
- 여러 가지 방법이 있지만 정규식을 활용한다면 훨씬 쉽게 처리를 할 수 있다. 


## 정규식을 사용한 방법 : String.matches( [정규식] ) 함수를 사용
```java
BufferedReader br = new BufferedReader(new InputStreamReader(System.in)); 
	  StringTokenizer st = new StringTokenizer(br.readLine());
		String file_name = st.nextToken("\n"); //st.nextToken(); 
		
		for( String tmp_s : file_name.split(" ")) {
			if ( tmp_s.matches("[+-]?\\d*")) {  // + 또는 - 로 시작하는 숫자 데이터가 있는지 검사 
				file_name = '\"'+ file_name + '\"';  // 만약 있다면 앞/뒤에 "를 붙여주는 처리를 수행 
				break;
			}
		}
```

## 다른 방법들
- [자료참고](https://m.blog.naver.com/PostView.naver?blogId=hoon4672&logNo=222204799623&categoryNo=4&proxyReferer=)
