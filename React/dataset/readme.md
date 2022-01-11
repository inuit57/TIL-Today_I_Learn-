# 출처
- [참고자료](https://velog.io/@hwang-eunji/React-HTML-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%84%B8%ED%8A%B8dataset-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0) 

# datatset
- 데이터 세트는 HTML 표준에 정의된 기능
- DOM요소에 값을 저장, JS 코드로 값을 읽어들일 수 있음

## 사용법

### html (정의)
- data-를 시작으로 data-이름을-지정하면-된다와 같이 tag element에 속성으로 사용 : 
```html 
// 예시
<p data-user-name>{state.userName}</p>
```
### js (사용)
- data-user-name 데이터 세트를 읽어들인다면, data-는 제거되며, userName과 같이 카멜케이스로 변경하여 읽는다.

>data- 뒤에 가능 : 소문자 영문, 점(.), 하이픈(-), 로우데시(_), 콜론(:) <br>
>data- 뒤에 사용 불가능 : 대문자 영문 <br>
>html에서 data-abc-def 라는 이름의 속성은 JS에서 abcDef key에 응답 <br>

## 사용예시
```javascript
import React, { useState } from 'react';

function Dataset() {
  const [selectedName, setSelectedName] = useState('none');
  const onClick = (e) => {
    const name = e.target.dataset.name;
    setSelectedName(name);
  };
  return (
    <>
      <button onClick={onClick} data-name='Hwang'>Hwang</button>
      <button onClick={onClick} data-name='Kim'>Kim</button>
      <button onClick={onClick} data-name='Jo'>Jo</button>
      <button onClick={onClick} data-name='Sim'>Sim</button>
      <button onClick={onClick} data-name='Lee'>Lee</button>
      <button onClick={onClick} data-name='Jang'>Jang</button>
	//... 더많은 버튼이 있을 수도..
      <p>selecteName is <strong>{selectedName}</strong></p>
    </>
  );
}

export default Dataset;
```

```javascript
class TOC extends Component{
    render(){
      var lists= [] ; 
      var data = this.props.data;
      var i =0 ; 
      while ( i < data.length){
        lists.push( 
          <li key={data[i].id}>
            <a href={"/content/"+data[i].id}
            
              data-id={data[i].id}
              
              onClick={function(e){
                  e.preventDefault();
                  
                  this.props.onChangePage(e.target.dataset.id);
                  
              }.bind(this)}          
            >{data[i].title}</a></li>)
        i = i+1;
      }
      return(
        <nav>
          <ul>
            {lists}
          </ul>
        </nav>
      );
    }
}
```
