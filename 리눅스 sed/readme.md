# 개요 
- 파일의 내용을 찾아서 일괄 변경하는 명령어 

# 사용법
## 단일 파일의 내용 변경
```
sed -i 's/old/new/g' 파일명.txt
```
## 여러 파일의 내용 변경
```sh
find ./ -name "*.txt" -exec sed -i 's/old/new/g' {} \;
```

# 출처
- [자료1](http://sung.world.kr/bbs/board.php?bo_table=linux&wr_id=281)
- [자료2](https://heum-story.tistory.com/62)
