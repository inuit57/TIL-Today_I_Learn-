# 개요
- DBA들과 대화를 진행할 때 문제가 되지 않도록 용어를 정리한다. 

## 종류
- Data WareHouse (DW)
- Data Mart (DM)
- Data Lake (DL)

# Data Warehouse
- [자료참고](https://hengbokhan.tistory.com/165?category=919198)
- 한 마디로 대량의 데이터를 분석하기 좋게 체계적으로 정리해놓은 창고이다. 
- 당연히 분석을 위한 데이터들이므로 정제되고 가공된 데이터들이다.

## 주요특징 4가지
1) 주제지향 (Subject Oriented)
      + 정보를 이용하는 사람 관점에서 보았을 때, 업무 중심이 아닌 주제 중심으로 데이터를 조직화한다.
      + 예를 들어, 고객 거래처,상품, 활동 등의 데이터
    + 또한 의사결정에 필요없는 데이터는 저장하지 않는다. 
2) 통합(Integrated)
      + DW 에서는 보관되는 데이터를 활용하기 좋은 형태로 변환할 필요가 있다.
      + 표준화 기준을 설정하고 적용함으로써 데이터를 통합한다. 
3) 시계열(Time Variant)
      + DW 에는 시간별로 데이터 버전들이 저장된다. 과거와 현재의 데이터가 모두 존재한다. 
      + 가공된 정보로써 의사결정을 지원하는데 목적이 있기에 시간에 따라 수시로 갱신/변경되지 않는다.
4) 비휘발성(Nonvolatile)
      + DW의 데이터들로 수행할 수 있는 작업은 2가지가 있다.
      + 데이터로딩, 데이터 접근으로 사실상 select,insert만 가능하다고 보면 된다. 

# Data Mart
- [자료참고](https://hengbokhan.tistory.com/167?category=919198)
- 필요에 따라 만들어지는 작은 데이터 웨어하우스.
- 금융,마케팅, 영업과 같은 특정 부서 중심의 요구를 충족시키기 위해 만들어진다.
- 목적에 특화되어있으며 유연성과 접근성이 더 뛰어나다. 
- 일반적으로 DW 에서 일부분을 가져오는 식으로 만들어진다. 

# Data Lake 
- [자료참고](https://hengbokhan.tistory.com/162?category=919198)
- 정제되지 않은 데이터(원시 데이터,raw data)들을 넣어놓은 거대한 데이터 창고
- 다양한 소스에서 수집된 데이터들이 수집된 형태 그대로 저장된다. 


  
