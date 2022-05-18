# 개요
- 프로젝트 진행 중 DB에서 수집된 데이터들을 엑셀 파일로 추출해야 하는 경우가 발생.
- 검색을 통해서 진행하긴 하였지만 정리를 위해서 작성합니다. 

- 기회가 된다면 Excel 로 들어온 입력값에 대한 처리도 한 번 진행해봅시다.
- 웹 기반으로 작업을 진행하였습니다. 
- 따라서 파일 업로드에 필요한 FileOutput 객체는 생성하지 않았습니다. 

# 자료
- [엑셀 다운로드 Spring boot](https://velog.io/@haerong22/Spring-%EC%97%91%EC%85%80-%ED%8C%8C%EC%9D%BC-%EB%8B%A4%EC%9A%B4%EB%A1%9C%EB%93%9C-%ED%95%98%EA%B8%B0)

## 유의사항
- 엑셀 1셀에 들어갈 수 있는 글자 수에는 제한이 있습니다. (32,767자)
- 따라서 많은 양의 텍스트 데이터(예/ CLOB )를 처리하게 될 경우 데이터의 손실을 감수해야 할 겁니다. 

# 필요사항
- [poi-5.0.0.jar](https://mvnrepository.com/artifact/org.apache.poi/poi/5.0.0)
- [poi-ooxml-5.0.0.jar](https://mvnrepository.com/artifact/org.apache.poi/poi-ooxml/5.0.0)

- 엑셀 파일을 생성하거나 읽기위해서는 위의 2개의 라이브러리가 필요합니다.
- 우선, 검증이 완료되었고 비교적 최신 버전인 5 버전을 사용하였습니다. 

## 참고사항
```
HSSF : 2007 이전 버전
XSSF : 2007 이후 버전 (2007 포함)
SXSSF : 대용량 엑셀 파일 , XSSF의 Streaming Version 으로 메모리를 적게 사용
```
- 엑셀파일을 생성할 때 import를 시켜줄 때 상황에 따라서 다르게 진행할 것. 


## 코드
- import 부분
```
import org.apache.poi.ss.usermodel.Cell;
import org.apache.poi.ss.usermodel.Row;
import org.apache.poi.ss.usermodel.Sheet;
import org.apache.poi.ss.usermodel.Workbook;
import org.apache.poi.xssf.usermodel.XSSFWorkbook;
```

- 파일 생성 부분
```
public void excelDownload(HttpServletResponse response) throws IOException {
//    Workbook wb = new HSSFWorkbook();
      Workbook wb = new XSSFWorkbook();
      
      Sheet sheet = wb.createSheet("첫번째 시트");
      Row row = null;
      Cell cell = null;
      int rowNum = 0;

      // Header
      row = sheet.createRow(rowNum++);
      cell = row.createCell(0);
      cell.setCellValue("번호");
      cell = row.createCell(1);
      cell.setCellValue("제목");
      cell = row.createCell(2);
      cell.setCellValue("날짜");
      cell = row.createCell(3);
      cell.setCellValue("내용");
      
      // Body
      for (int i=0; i<3; i++) {
          row = sheet.createRow(rowNum++);
          cell = row.createCell(0);
          cell.setCellValue(i);
          cell = row.createCell(1);
          cell.setCellValue(i+"_name");
          cell = row.createCell(2);
          cell.setCellValue(i+"_title");
      }

      // 컨텐츠 타입과 파일명 지정
      response.setContentType("ms-vnd/excel");
      response.setHeader("Content-Disposition", "attachment;filename=example.xlsx");

      // Excel File Output
      wb.write(response.getOutputStream());
}
```
- WorkBook > Sheet > Row > Cell 순서로 작업된다고 이해하면 됩니다.
- WorkBook은 그리고 자동으로 닫아주기 때문에 wb.close() 함수가 없습니다. 
