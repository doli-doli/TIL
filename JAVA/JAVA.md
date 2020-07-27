# DAO & DTO(=VO)
- DAO , DTO 개념 정리

## DAO(Data Access Object)
- Data Access Object의 약자로 간단히 Database의 data에 접근을 위한 객체
- 웹서버는 DB와 연결하기 위해서 매번 커넥션 객체를 생성하는데, 이것을 해결하기 위해 나온것이 커넥션 풀
- ConnectionPool 이란 connection 객체를 미리 만들어 놓고 그것을 가져다 쓰는것 / 다쓰고 난 후에는 반환하자

## DTO(Data Transfer Object)
- VO(Value Object)로 바꿔 말할 수 있는데 계층간 데이터 교환을 위한 자바빈즈
- 각 계층간 데이터 교환을 위한 객체를 DTO 또는 VO라고 부릅니다 그런데 VO는 DTO와 동일한 개념이지만 read only 속성을 가짐
- DTO는 로직을 갖고 있지 않는 순수한 데이터 객체, 속성에 접근하기 위한 getter, setter 메소드만 가진 클래스
