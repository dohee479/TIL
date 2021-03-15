# Spring을 들어가기에 앞서

## JSP(자바 서버 페이지)

- 웹을 개발할 때 가장 기본적인 것을 제공
- HTML 내에 자바 코드를 삽입하여 웹 서버에서 동적으로 웹 페이지를 생성하여 웹 브라우저에 돌려 주는 서버 사이드 스크립트 언어이다.
- java ee 스펙 중 일부로 웹 애플리케이션 서버(WAS)에서 동작한다.



## 파일 구조

### 파일을 생성할 때

- 이클립스에서 new file를 클릭한 후 Dynamic web을 생성하게 될 경우, moudule version은 내가 어떤 WAS를 쓰느냐에 따라 설정을 해야한다.

![화면 캡처 2021-03-15 204413](https://user-images.githubusercontent.com/60080744/111148722-52def500-85cf-11eb-8b8f-f86ab528866c.jpg)

### context root

- http://localhost:8080/context root/



### content directory

- WebContent: 웹에서 쓸 파일들을 갖다 놓는다.



### web.xml

- deployment descriptor(DD)(배치 기술자)

![화면 캡처 2021-03-15 205157](https://user-images.githubusercontent.com/60080744/111149533-57f07400-85d0-11eb-83fd-bb968000da55.jpg)



### 개발 과정

- 내가 작성한 코드 -> .war(압축 파일) -> 운영서버에 배치



### WEB-INF(중요)

- build: github 전송X
- WebContent
  - common 
  - META-INF : 지워도 된다
  - WEB-INF 외부 : html, css, js, 이미지 파일 등이 들어간다.
  - WEB-INF
    - WEB-INF 내부
    - lib : 외부 라이브러리 파일 넣음(xx.jar)
    - .class가 들어간다
- 웹 브라우저에서 바깥쪽은 접근이 가능하지만 내부쪽은 접근이 불가능하다.



### Tomcat v9.0 Server at localhost

- WAS
- WebApplication(.war)를 만든 다음 실행 되는 거다.
  - 위치는 workspace/.metadata/...(어딘가)/



## Servlet 

### superclass

- HttpServlet을 상속받는다(중요)
- service  재정의



### HttpServletRequest/HttpServletResponse

![화면 캡처 2021-03-15 214307](https://user-images.githubusercontent.com/60080744/111155177-773ecf80-85d7-11eb-80f9-7a4679786cd6.jpg)

- WAS가 웹 브라우저로부터 요청을 받으면
  - 요청을 받을 때 전달 받은 정보를 HttpServletRequest객체를 생성하여 저장
  - 웹브라우져에게 응답을 돌려줄 HttpServletResponse객체를 생성(빈 객체)
  - 생성된 HttpServletRequest(정보가 저장된)와 HttpServletResponse(비어 있는)를 Servlet에게 전달
  - Servlet은 HttpServletResponse객체에 Content Type, 응답코드, 응답 메시지등을 담아서 전송함



### controller

- servlet -> controller -> Jsp

![화면 캡처 2021-03-15 220037](https://user-images.githubusercontent.com/60080744/111157158-e74e5500-85d9-11eb-97d0-6ee69b814495.jpg)





