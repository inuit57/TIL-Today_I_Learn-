# 개요
- Pattern 과 Macher의 사용법에 대해서 기술한다. 


# 사용법 
```java

        String textPtn ="([0-9]+.[0-9]+.[0-9]+.[0-9]+):([0-9]+)" ;
        //String textPtn ="([0-9]+.[0-9]+.[0-9]+.[0-9]+)(:)([0-9]+)" ;
        // () 로 묶은 것을 하나의 그룹으로 판단하고 pattern 추출한다.

        Pattern pattern = Pattern.compile(textPtn);
        Matcher matcher = pattern.matcher(source);

```
