# 개요
- 홀수인지 짝수인지 판별하는 일반적인 방법은 2로 나누어서 나머지를 확인하는 것입니다.
- 하지만 0인지 1인지 비교하는 일이라면 비트연산자 & 만을 통해서 더 빠르게 구현도 가능합니다. 

```
if(i&1) {
        //when i is odd
}
if(~i&1) {
        //when i is even
}
```
