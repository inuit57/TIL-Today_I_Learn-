# 같다 비교 override 처리시 주의사항

- equal() 함수만 오버라이딩 해줄 것이 아니라 hashCode() 함수도 같이 오버라이딩 해줘야 한다.
- lombok에서 그것을 어노테이션화 해둔 것이 있기에 그것을 그대로 사용하면 된다. 

## 이유
- hashCode() 함수를 오버라이딩 해주지 않을 경우, hashCode를 사용하는 hashXXX 컬렉션들을 사용할 때
- 제대로 존재여부를 판단하는 것이 되지 않는다. 
- 예를 들어서 HashSet<T> 를 사용할 때 제네릭 타입에 우리가 만든 클래스를 사용한다고 하였을 때 제대로 오버라이딩 하지 않는다면
  hash 기능을 제대로 활용하지 못하게 될 수 있다는 의미다. 

  
## 어노테이션 사용 후 equals 를 따로 재정의하는 경우
  - 이렇게 할 경우 HashCode() 함수는 생성되지 않는다. 
  - 만약 어노테이션을 사용하려고 한다면 2개 모두 재정의하거나 혹은 하지 않아야만 한다. 
  
## 추가 공부
  - hashCode 를 만드는 방법들 ( 31 이라는 소수를 사용하곤 한다, 참고로 lombok 에서는 59 를 사용하던가 그렇다.)