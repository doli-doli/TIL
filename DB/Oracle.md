## 오라클 HR 계정 이용하기
 - HR 계정은 오라클에서 교육용으로 기본적으로 제공하는 계정
 - Employees, Department 등 테이블과 값이 미리 생성되어 있음.
 - 잠금을 풀고 사용해야함.
## HR 잠금풀기
 1. SQL Command Line 실행
 2. sysdba에 연결 `conn /as sysdba;`
 3. hr계정 잠금상태를 푼다. `alter user hr account unlock;`
 4. 사용할 비밀번호를 설정 `alter user hr identified by 비밀번호;`
