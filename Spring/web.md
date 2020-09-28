# web.xml

## \<web-app\> Element
web.xml의 Root-Element 기능을 담당한다.
- xmlns와 servlet의 버전을 설정
~~~
<web-app version="2.5" xmlns="http://java.sun.com/xml/ns/javaee"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee https://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">
</web-app>
~~~

## \<display-name\> Element
web.xml 파일의 title을 설정하는 부분이다.
default 값 = 프로젝트명으로 설정된다.

## \<welcome-file-list\> Element
서버로 요청이 들어왔을 때 표시할 처음 페이지 welcome-file을 순서대로 정의하는 부분이다.

- welcome-file : 파일이름
~~~
// jsp -> html -> 404페이지 순서로 호출
<welcome-file-list>
	    <welcome-file>index.jsp</welcome-file>
      <welcome-file>index.html</welcome-file>
	</welcome-file-list>
~~~

## \<context-param\> Element
Servlet context의 parameter를 선언해주는 부분이다.
web.xml의 전역 변수 같은 느낌이다
\<init-param\>은 지역변수라고 생각하면 이해가 쉽다.

- param-name: parameter 이름
- param-value: parameter 값
~~~
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/conf/spring-context.xml</param-value>
</context-param>
~~~

## \<error-page\> Element
errorcode, exception type 을 매핑하기 위한 부분.

- error-code: 웹의 에러 코드를 적어주는 변수
- exception-type: java exception type을 적어주는 변수
- location: 매핑할 페이지의 경로를 적는 변수
~~~
<error-page>
    <error-code>404</error-code>
    <location>/error_page/404.jsp</location>
</error-page>
<error-page>
    <exception-type>java.lang.NullPointerException</exception-type>
    <location>/error_page/404.jsp</location>
</error-page>
~~~

## \<listener\> Element
Application Listener Bean을 가리키기 위한 부분으로,
이때 해당 Bean은 웹 애플리케이션에 등록이 되어있어야 한다.

- listener-class: listener bean의 class를 지정해주는 부분
~~~
// spring에서 contextConfigLocation을 설정하기 위한 listener bean 지정
<listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
</listener>
~~~

## \<filter\> Element
Application에서 사용할 filter를 선언하는 부분이다.
어떤 filter를 사용할 것인지 설정하는 부분으로, 대표적으로 encodingFilter가 있다.

- filter-name: Required, unique, filter-mapping Element와 매핑하기 위한 변수
- filter-class: 사용할 클래스의 정규화 된 이름을 나타내는 변수
- init-param: filter에서 사용할 name-value 쌍을 선언하는 부분
- async-supported: Optional, 선언된 경우 async 방식으로 사용이 가능
~~~
// Encoding 방식을 UTF-8로 하기 위한 Filter
<filter>
    <filter-name>encodingFilter</filter-name>
    <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
    <init-param>
        <param-name>encoding</param-name>
        <param-value>UTF-8</param-value>
    </init-param>
</filter>
~~~

## \<filter-mapping\> Element
<filter> element는 사용할 필터를 설정하는 부분이고,
<filter-mapping> Element는 filter를 어디에 적용할 것인지를
URL 또는 Servlet을 통해 선언하는 부분이다.

- filter-name: filter Element와 매핑하기 위한 변수
- url-pattern: filter를 적용할 url을 선언하는 부분
- servlet-name: filter를 적용할 servlet을 선언하는 부분
~~~
// root 이하 모든 url에 이름이 encodingFilter인 filter를 적용
<filter-mapping>
    <filter-name>encodingFilter</filter-name>
    <url-pattern>/*</url-pattern>
</filter-mapping>
~~~

## \<servlet\> Element
Servlet을 선언할 때 사용하는 Element로, 선언에 필요한 정보를 담고 있다.
흔히 spring에서 DispatcherServlet을 선언할 때 자주 볼 수 있다.

- servlet-name: Required, unique, 사용할 servlet의 이름을 지정
- servlet-class: 사용할 클래스의 정규화 된 이름을 나타내는 변수
- init-param: servlet에서 사용할 name-value 쌍을 선언하는 부분
- load-on-startup: servlet이 배치될 때의 우선순위를 지정하기 위한 부분
~~~
<servlet>
    <servlet-name>dispatcherServlet</servlet-name>
    <servler-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <init-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>/WEB-INF/spring-servlet.xml</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
</servlet>
~~~

## \<servlet-mapping\> Element
Servlet과 URL 사이의 매핑을 정의하는 부분이다.

- servlet-name: 매핑할 servlet-name을 선언하는 부분
- url-pattern: servlet과 매핑할 URL 패턴을 선언하는 부분
~~~
// .jjh로 끝나는 모든 URL에 dispatcherServlet을 매핑
<servlet-mapping>
    <servlet-name>dispatcherServlet</servlet-name>
    <url-pattern>*.jjh</url-pattern>
</servlet-mapping>
~~~
