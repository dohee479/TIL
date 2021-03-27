# Tomcat, JSP, Servlet의 기본 개념 및 구조

JSP와 Servlet 은 모두 자바로 웹 어플리케이션을 만들기 위한 도구이다.



## JSP

- .jsp인 파일
- Java Server Page
- HTML 문서 안에 자바 언어를 사용할 수 있도록 한다.



## Servlet

- .java인 파일
- 자바의 일반 적인 클래스와 동일한 개념
- 웹을 다룰 수 있도록 해주는 **HttpServlet** 클래스를 상속받은 클래스를 의미함



## 웹 어플리 케이션의 일반적인 구조

1. 사용자가 **URL(또는 IP)**을 통해 **WEB 서버**를 호출하고 요청사항을 **객체(request)**에 담아 전송한다.
2. WEB 서버는 **요청 객체(request)**를 받아서 바로 처리하거나 **웹 어플리케이션 서버(WAS)**로 객체 전달한다.
3. **WAS**는 요청에 대한 내용과 **요청 객체(request)**를 받아 적절히 처리한다. (필요시 DB 작업 진행)
4. **WAS**는 처리후 결과를 **응답 객체(response)**에 담아 **WEB 서버**로 회신하다.
5. **WEB 서버**는 **응답 객체(response)**를 다시 사용자에게 회신
6. 사용자의 브라우저는 **WEB 서버**가 보내준 코드를 해석해 화면을 구성하여 출력



### WEB 서버 단일 구성

개발자는 미리 모든 페이지를 다 만들어 둔 뒤 웹 서버에 올려두고 사용자가 URL을 입력하거나 하이퍼링크가 걸린 부분을 클릭하면 웹서버가 해당하는 페이즈를 사용자에게 보내준다. 웹 브라우저는 페이지를 받아서 화면으로 만든 뒤 사용자에게 시각화하여 보여준다.

페이지는 html, CSS, Javascript로 이루어져 있다. 세 언어 모두 웹서버에서 코드를 보내주면 브라우저가 해석해서 실행한다.

![1](https://user-images.githubusercontent.com/60080744/112500739-fc8e6500-8dcb-11eb-8279-5076eeb3b4c7.jpg)



### WEB - WAS 구성

web 서버 단일 구성 방식은 사용자가 요청하면 해당 페이지를 넘겨주는 정적인 방식이다.

필요한 페이지마다 Javascript 등으로 복잡한 로직을 구성해서 모든 페이지를 미리 준비해놔야한다는 단점이 있다.

그리고 복잡한 로직이 들어있는 페이지를 모두 사용자에게 전송해야 한다는 문제도 있다. 컴퓨터의 성능과 네트워크 기술이 발전하며 웹 서비스의 복잡도가 점차 증가했고, 그만큼 효율적으로 웹 서비스를 구성해야 했다. 이를 위해 **WAS(Web Application Server)** 가 등장했다.

기본 웹 서버가 요청하는  페이지를 단순하게 반환했다면, WAS는 사용자의 요청 내용(request)을 받아 짜여진 로직대로 잘 처리한 뒤 웹 페이지를 만들어 사용자에게 응답(response) 해주는 방식이다. 만들어진 웹페이지는 웹서버를 통해 사용자에게 전달 된다. 자바와 같은 언어로 로직을 처리해서 복잡한 로직 처리가 수월하고, 사용자는 페이지만 받으므로 로직을 알 수없어 보안도 강화된다. 사용자 입장에서는 빠르게 받아 볼 수 있고 네트워크 부하도 줄어든다.

WEB서버와 WAS는 물리적으로 나눌 수도 있고 한 서버안에 기능적으로 나눠둘 수도 있다. 서로 수행하는 기능이 다르다는 것을 알아야 한다. 

웹서버는 정적 페이지(또는 이미지, 파일 등)는 자신이 처리하고, 연산이 필요할 경우 WAS에게 요청 객체를 넘겨 연산을 수행한 뒤 다시 결과를 반환한다.

![2](https://user-images.githubusercontent.com/60080744/112504058-c56d8300-8dce-11eb-8bde-4a123be020fc.jpg)

### WEB-WAS-DB 구성

사용자와 서버 간 데이터를 효율적으로 관리하기 위해 **DBMS(DataBase Management System)**가 개발 되었다.

DB에서는 서버가 연산을 위해 필요한 각종 정보를 저장해두고 WAS에서 연산을 수행하며 필요한 정보를 DB에서 가져오고 사용한다. 

![3](https://user-images.githubusercontent.com/60080744/112505081-c5ba4e00-8dcf-11eb-9140-1cd30c21285b.jpg)

## JAVA SE/ JAVA EE

JAVA EE는 JAVA SE의 확정 버전으로 서버 개발을 위한 추가 기능을 제공하는 플랫폼이다. 

간단한 응용프로그램과 서버 구축은 JAVA SE만으로도 구성이 가능하지만, Tomcat 등의 WAS를 이용하는 서버 개발은 JAVA EE 에서 추가로 제공하는 기능을 사용한다.

JSP와 Servlet을 만들고 실행하는 규칙과, EJB(Enterprise JavaBeans)의 분산 컴포넌트, 웹 서비스의 규칙 등을 추가로 가지고 있으며, 서블릿과 JSP를 구현하는 기능을 서블릿 컨테이너라고 합니다.



## Apache Tomcat(톰캣)

- Apache : WEB 서버
- Apache Tomcat : WAS



Apache는 웹서버 전용 기능이고 Tomcat은 WAS 기능을 한다. Tomcat도 기본적인 웹 서버 기능이 있어 웹서버를 구성할 수 있다. Apache Tomcat = 경량 Apache + Tomcate이라고 생각하면 된다. 

Tomvat은 WEB/WAS 기능을 가진 자바 어플리케이션이다. JAVA EE 기반이다. WAS는 자바로 만들어진 JSP와 Servlet을 구동하기 위한 서블릿 컨테이너 역할을 한다. 컨테이너란 JSP를 Servlet으로 바꿔서 실행해주는 역할과       Servlet 의 생명주기를 관리하며 웹 환경에서 Servlet이 구동될 수 있도록 해주는 프로그램이다. WAS에서는 여러개의 컨테이너를 구성해서 각각 독립적인 서비스로 구동시키는 것도 가능하다.

WAS의 컨테이너는 웹서버에서 보내준 요청을 가지고 스레드를 생성한 후, 필요한 JSP나 Servlet 파일을 구동해서 로직을 수행하게 한 뒤 결과로 생성된 응답 객체를 웹서버에 보내주는 역할을 한다. 하나의 WAS에 하나의 컨테이너만 사용한다면 굳이 WAS와 컨테이너를 별도로 나눠서 생각할 필요가 없다.

![4](https://user-images.githubusercontent.com/60080744/112508635-15e6df80-8dd3-11eb-922e-ee10e5e97851.jpg)



## Servlet(서블릿)과 JSP

Servlet은 JAVA EE에서 제공하는 서블릿 클래스를 상속받은 클래스를 말한다. .java의 클래스 파일과 동일하다.

다만, 최종적으로 클라이언트가 받아야하는 HTML 코드를 출력해주는 작업이 너무 번거롭다.  IO 입출력과 같이 스트림 객체를 생성해서 클라이언트에게 보내줄 HTML 코드를 전부 print 해줘야 한다.

```java
writer.println("<html>");
writer.println("<head>");
writer.println("</head>");
writer.println("<body>");
writer.println("<h1>helloWorld~</h1>");
writer.println("name : " + request.getParameter("name") + "<br/>");
writer.println("id : " + request.getParameter("id") + "<br/>");
writer.println("pw : " + request.getParameter("pw" + "<br/>"));
writer.println("major : " + request.getParameter("major") + "<br/>");
writer.println("protocol : " + request.getParameter("protocol") + "<br/>");
writer.println("</body>");
writer.println("</html>");
writer.close();
```

자바 안에 HTML 코드가 들어가긴 하지만 저건 출력만 해주는 거다. 복잡한 레이아웃일 수록 길어질 수 밖에 없다.

이로 인해 JSP가 등장했다. JSP는 Servlet과 반대로 기본적으로 HTML 코드 형식을 하고, 중간에 자바를 사용해 로직을 구성할 수 있다.

```JSP
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>

<%-- 자바 코드 삽입 --%>
<% 
	for(int i = 0; i < 10; i++) {
		out.println(i);
	}
%>

</body>
</html>
```

JSP는 먼저 Servlet 파일(.java)로 변환된다. 변환된 Servlet 파일을 다시 컴파일해서 .class 파일로 만든 뒤 실행한다. 실행 결과는 자바가 사라진 HTML 코드다. 처음 구동할 때는 변환 과정이 한 번 더 있으므로 Servlet보다 느리지만, 첫 구동에서 class 파일을 생성해 두면 두번째 부터는 변환과정 및 컴파일 과정이 없기 때문에 Servlet과 거의 동일하게 작동한다.

![5](https://user-images.githubusercontent.com/60080744/112509908-467b4900-8dd4-11eb-9fd5-2a746d70e529.jpg)

JSP는 화면 구성에 사용되고 Servlet은 로직 수행하는데 사용되는 경우가 일반적이다.

JSP는 서버에서 모두 처리되어 클라이언트에게는 HTML 형식으로 전달되기 때문에 클라이언트단에서 처리가 필요한 동적 처리는 실행할 수 없다. 따라서 클라이언트(브라우저)에서 실행되는 동적 처리는 Javascript로 처리해야한다. JSP에서 Javascript 사용가능하다.



참조 : https://codevang.tistory.com/191?category=844272