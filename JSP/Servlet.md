# 서블릿(Servlet)
#### 클라이언트 요청을 처리하고 그 결과를 다시 클라이언트에게 전송하는 servlet 클래스의 구현 규칙을 지킨 자바프로그램
- 자바를 사용하여 웹을 만들기 위해 필요한 기술
- 클라이언트의 요청에 대해 동적으로 작동하는 웹 어플리케이션 컴포넌트
- HTML을 사용하여 요청에 응답한다.
- Java Thread를 이용한다.
- HTTP을 지원하는 javax.servlet.http.HttpServlet 클래스를 상속받는다.
- HTML 변경 시 Servlet을 재 컴파일해야 하는 단점이 있다.

## 매핑
  (1) web.xml
  ~~~
  <servlet>
  <servlet-name>MyServlet</servlet-name> <!-- 대상으로 한 클래스 이름 -->
  <servlet-class>com.jh.ex.Ex01_servlet</servlet-class>	<!-- 대상으로 할 클래스 패스 -->
  </servlet>
  <!-- 2. 서블릿과 URL 간의 매핑 -->
<servlet-mapping>
<servlet-name>MyServlet</servlet-name>
<url-pattern>/welcome</url-pattern>	<!-- 웹 주소에서 MyServlet을 welcome으로 부르자! ★무조건 슬래시(/)로 시작한다! -->
</servlet-mapping>
~~~
(2) 어노테이션
- 서블릿 3.0 버전부터는 @WebServlet 어노테이션을 사용하면 web.xml에 등록하지 않아도 된다.
- 톰캣 7~ 서블릿 3.0 지원

## 서블릿 JSP 차이점
#### 서블릿
1. 자바코드로 구현하고 컴파일하고 배포해야 한다.
2. HTML태그로 문자열("")스크림으로 처리해야 한다.
3. 코드가 수정되면 다시 컴파일하고 배포해야 한다.
#### JSP
1. 키워드가 태그화 되어 서블릿에 비해 배우기 쉽다.
2. 자바코드를 <%%>태그 안에 처리해주어야 한다.
3. HTML처럼 태그를 사용하여 자바코드도 사용이 가능하다.

## 서블릿 JSP 역할
- 서블릿이나 JSP나 만드는 방법에 차이가 있을 뿐 동일한 역할을 한다.
- JSP는 JSP기술의 장점을 최대한 활용 할 수 있는 웹에플리케이션 구조에서 사용자에게 결과를 보여주는 프리젠테이션 층을 담당한다.
- Servlet은 장점을 최대한 활용 할 수 있는 사용자의 요청을 받아 분석하고 비지니스 층과 통신하여 처리하고 처리한 결과를 다시 사용자에게 응답하는 컨트롤러 층을 담당한다.
- JSP와 Servlet 동시에 사용 MVC모델(View는 JSP, Controller는 Servlet을 사용)
- 프리젠테이션 로직과 비즈니스 로직 분리
(보여지는 부분은 HTML이 중심이 되는 JSP, 다른 자바클래스에게 데이터를 넘겨주는 부분은 Java코드가 중심이 되는 Servlet이 담당)
- 유지보수 용이
