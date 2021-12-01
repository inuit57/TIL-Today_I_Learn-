# 개요
- Excel 파일의 내용을 받아서 화면 단의 form에 데이터를 채워줘야하는 간단한 예제.
- 간단하면서도 조금 삽질을 하였던 부분이 있었기에 정리를 하고자 적습니다. 

- 언젠가 Excel 입출력에 관해서는 몇 가지 좀 만들어보는 것이 좋으리라 여겨집니다. 

## javascript
```javascript

function put_excel(){
    var form = $('#excel_form')[0]; 
    var frmData = new FormData(form); // form 데이터를 따로 뽑아내줘야 합니다. 

    $.ajax({
        enctype: 'multipart/form-data', // ajax로 파일을 던지려면 이렇게 설정해야 합니다. 
        type: 'POST',
        url: './inputExcel.wn',
        processData: false,   
        contentType : false,
        cache: false,
        data: frmData, // 앞서 뽑아낸 form 데이터를 넣어줍니다. 
        success: function(data) {
        	form.reset(); 
            console.log(data);
            
            var jsonObj = JSON.parse(data);
            
            $("#data1").val(jsonObj.data1);
            $("#data2").val(jsonObj.data2);
            $("#data3").val(jsonObj.data3);
            
            
        },
        error: function(e) {
            console.log(e);
            alert('파일업로드 실패');
        }
    });
}
```

## jsp 
```jsp 
 	 
 	<div class="test">
 		<form action="" enctype="multipart/form-data" id="excel_form" name="excel_form" method="post">
 			[엑셀입력]<input type="file" name="excel_file" id="excel_file" accept=".xlsx"></input>
 			[데이터1]<input type="text" name="data1" id="data1"></input>
 			[데이터2]<input type="text" name="data2" id="data2"></input>
 			[데이터3]<input type="text" name="data3" id="data3"></input>
 			
 			<input type="button" value="확인" onclick="put_excel();">
 		</form>
 	</div>
  ```
  
  ## Controller (java)
  ```java
  // produces = "application/text; charset=utf8"  : 설정을 해줘야 jsp 로 넘어갈 때 한글이 안 깨진다. 
  // method = RequestMethod.POST  : 파일 전송은 POST 방식만 가능 
  // 	@ResponseBody : ajax 결과값으로 리턴해줄 거니까. 
  
  @RequestMapping(value= "/inputExcel.wn" , produces = "application/text; charset=utf8" , method = RequestMethod.POST )
	@ResponseBody
	public String inputExcel(MultipartHttpServletRequest req, HttpServletResponse res) {
		
		logger.debug("엑셀 입력 발생!!"); 
		
		MultipartFile file = null;
		Iterator<String> mIterator = req.getFileNames();
		if(mIterator.hasNext()) {
			file = req.getFile(mIterator.next());
		}
		
		String result = ""; 
		
		if(file != null) {
			try {
				result = service.readExcel(file);
			} catch (Exception e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			} 
		}
		return result;
	}
```

## Service (java) 
```java
public String readExcel(MultipartFile file) throws Exception {
		// TODO Auto-generated method stub
	    // 엑셀파일 열기 (엑셀버전 2007 이상일때, 오픈방법)
	    OPCPackage opcPackage = OPCPackage.open(file.getInputStream());
	    XSSFWorkbook wb = new XSSFWorkbook(opcPackage);

	    Map<String, String> excelMap = new HashMap<String, String>(); 
	    String[] strArr = new String[3] ; 
	    Gson gson = new Gson();
	    

	      XSSFSheet sheet = wb.getSheetAt(0);
	      int maxRow = sheet.getLastRowNum(); 
	      
	      // row
	      for(int i =0 ; i <= maxRow ; i++) {
	    	  Row currentRow = sheet.getRow(i); 
	    	  
	    	  // cell
	    	  for( int j =0 ; j < currentRow.getLastCellNum(); j++) {
	    		  Cell currentCell = currentRow.getCell(j);
	    		  if ( currentCell != null) {
		    		  if(currentCell.getCellType() == Cell.CELL_TYPE_STRING) {
			            	if(strArr[i] == null || "".equals(strArr[i]) ){
			            		strArr[i] = currentCell.getStringCellValue() ; 
			            	}else {
			            		strArr[i] += (","+ currentCell.getStringCellValue()) ;
			            	}
			            	
			          }else if (currentCell.getCellType() == Cell.CELL_TYPE_NUMERIC) {
			            	if(strArr[i] == null || "".equals(strArr[i]) ){
			            		strArr[i] = currentCell.getStringCellValue() ; 
			            	}else {
			            		strArr[i] += (","+ currentCell.getStringCellValue()) ;
			            	}
			          }else if ( currentCell.getCellType() == Cell.CELL_TYPE_BLANK) {
			        	  System.out.print("blank\t"); 
			          }
	    		  }else {
	    			  System.out.print("blank2\t");  
	    		  }
	    	  }
	    	  System.out.println(); // Row를 구분해주기 위한 엔터
	      }
	      
	      excelMap.put("data1", strArr[0]);
	      excelMap.put("data2", strArr[1]); 
	      excelMap.put("data3", strArr[2]); 
	      
	    return gson.toJson(excelMap); 	
	  } 
```

