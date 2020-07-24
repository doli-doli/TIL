# JSTL
- 20-07-24 ~ 20-00-00 까지
## 선언부 
- import에 선언
- <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %><br/>
- taglibs-standard-impl-1.2.5 / jstlel--1.2.5 / spec-1.2.5 .jar 파일 필요
                 

## 변수 선언
- <c:set var="변수명" value="변수값" />

## 사용 예시
- 저장
~~~ 
<c:set var="num1" value="77"/>
<c:set var="num2" value="9"/>
<c:set var="result" value="${num1+num2}"/>
~~~
- 출력
~~~
${num1 }
${num2 }
${result }
~~~
## 파라미터 이용
- 저장
~~~
< c:set var="result" value="${param.num1+param.num2}"/>
~~~
- 출력
~~~
${param.num1 }
${param.num2 }
${param.result }
~~~
## 조건문
- test = "조건내용"

  1. 조건비교 // ge 0 = x >= 0 // lt 0 = x < 0 
~~~
<c:if test="${result ge 60 }">
  <c:set var="pass" value="60점 이상"></c:set>
</c:if>
<c:if test="${result lt 60 }">
  <c:set var="pass" value="60점 미만"></c:set>
</c:if>
~~~
  2. 다중조건비교
~~~
<c:choose>
  <c:when test="${result ge 90 }"><c:set var="grade" value="A"/></c:when>
  <c:when test="${result ge 80 }"><c:set var="grade" value="B"/></c:when>
  <c:when test="${result ge 70 }"><c:set var="grade" value="C"/></c:when>
  <c:when test="${result ge 60 }"><c:set var="grade" value="D"/></c:when>
</c:choose>
~~~
## 반복문
  1. 일반 for문 forEach
  형식 : for(String name : names)
~~~
<% 
String[] names = {"김","이","박","최","신"};
pageContext.setAttribute("NAMES",names);
%>
~~~
출력:
~~~
<c:forEach var="name" items="${NAMES }">
  ${name }
</c:forEach>
~~~
# Ex)
  1. 일반 forEach
  - 최소 크기와 최대 크기를 직접 입력 받아 비교하여 작은 값부터 큰 값까지 차례대로 출력
~~~
최소 크기 : <input type="number" name="num1" min="1" max="7">
최대 크기 : <input type="number" name="num2" min="1" max="7">
~~~
출력:
~~~
<c:choose>
  <c:when test="${num ge num2 }">
  <c:set var="start" value="num2"></c:set>
  <c:set var="stop" value="num1"></c:set>
</c:when>
  <c:otherwise> <%-- else 같은 느낌 --%>
    <c:set var="start" value="num1"></c:set>
    <c:set var="stop" value="num2"></c:set>
  </c:otherwise>
</c:choose>
~~~
## forTokens
- 기호별로 토큰 자르는 기능
~~~
<c:set var="animals" value="사자,호랑이;사슴,곰;이구아나^뱀"></c:set>
~~~
출력: 기호 '.' , ';' , '^'
~~~
<c:forTokens var="animal" items="${animals }" delims=",;^">
${animal }&nbsp;
</c:forTokens>
~~~
결과: 사자 호랑이 사슴 곰 이구아나 뱀
