

# Spring

## Spring vs Spring boot

### Spring

- Java Application을 개발하는데 필요한 하부구조를 포괄적으로 제공한다.
- .Spring이 하부구조를 처리하기 때문에 개발자는 Application 개발에 집중할 수 있다.
- .동적인 웹 사이트를 개발하기 위한 여러 가지 서비스를 제공한다.
- boot에 비해 설정할 것이 많다.



### Spring boot

- Boot는 빠른 시간에 Application이 제품이 될 수 있도록 하는 것을 목표로 한다.
- Actuator : 애플레이켠을 고수준에서 모니터링하고 추적 할 수 있도록 해준다.
- Embedded Server Integrations :  서버가 애플리케이션에 통합되기 때문에 우리는 서버에 설치되는 별도의 애플리케이션 서버를 가질 필요가 없다.



## Spring Legacy project(이클립스에서)

### 생성

- File -> New -> Spring Legacy Project
- Spring MVC Project 선택 -> Next

![화면 캡처 2021-03-15 204413](https://user-images.githubusercontent.com/60080744/111292909-073e5100-868c-11eb-9e44-1d5229779002.jpg)

- 패키지 이름 설정: com.회사도메인이름.프로젝트이름

![화면 캡처 2021-03-16 191712](https://user-images.githubusercontent.com/60080744/111293085-3bb20d00-868c-11eb-9b82-03696752a069.jpg)



## Maven(빌드 도구)

### 빌드

- 소스 -> 컴파일 -> 빌드 -> .war
- 우리가 작성한 소스코드, 프로젝트에서 쓰인 각각의 파일 및 자원등(.xml, .jpg, .jar, .properties)을 JVM이나 톰캣같은 WAS가 인식할 수 있는 구조로 패키징 하는 과정 및 결과물이라고 할 수 있다.



### 특징

- 필요한 라이브러리를 특정 문서(`pom.xml`)에 정의 해놓으면 내가 사용할 라이브러리 뿐만 아니라 해당 라이브러리가 작동하는 데에 필요한 다른 라이브러리들까지 관리하여 네트웨크를 통해서 자동으로 받아준다.



### 메이븐 저장소

- 디펜더시 추가하면 메이븐 중장저장소에서 추가한 것을 차즌ㄴ다
- <user_name>/.m2/respository에 저장
  - 프로젝트는 여기에 있는 것을 참조해서 사용



## 파일 구조

- 프로젝트이름
  - Deployment Descriptor: 프로젝트이름
  - Spring Element
  - Java Resources
    - src/main/java : Java 파일 들어감
    - src/main/resources : 설정 파일들
    - src/test/java : 테스트할 때 사용
    - src/test/resources : 테스트할 때 사용
    - src/~/~ 인 이유는 Maven의 요구이다.
  - src
    - java : src/main/java 와 같다
    - resources : src/main/resources 와 같다
    - webapp(=WebContent) : Dynamic Web Project로 생성했을 시 생성되는 WebContent와 역할이 같다.
      - resources
      - WEB-INF



### Web.xml

- `<url-pattern>`: context root가 생략되어 있다.



### target

- 빌드할 때 쓰인다.



### pom.xml

- `artifactId` : 프로젝트 이름이 들어간다.
- 보통 <artifactId> = <name>
- dependencies에 12개 필요해 -> pom.xml에 정의되어 있다.
- 필요한 라이브러리 -> pom.xml에 등록해야한다.

![화면 캡처 2021-03-16 200139](https://user-images.githubusercontent.com/60080744/111298731-728b2180-8692-11eb-92e9-3ff11b5dd671.jpg)



## Legacy로 생성할 경우 수정과정

- Deploymet 왼쪽에 2.5는 servlet 버전이다.

<img src="https://user-images.githubusercontent.com/60080744/111322338-2b118f00-86ac-11eb-8817-8ebfd286522d.jpg" alt="화면 캡처 2021-03-16 230536" style="zoom:200%;" />

- spring folder 오른쪽버튼 -> properties 
  - Resource -> java build path -> 1.6삭제 -> add  libray -> JRE system library -> Alternate -> JDK 1.8
  - Java compiler 1.6 -> 1.8
  - project facets -> dynamic 4.0, java 1.8로 설정

![화면 캡처 2021-03-16 231024](https://user-images.githubusercontent.com/60080744/111322974-d1f62b00-86ac-11eb-9bc4-a71d6c69d5df.jpg)



- Deployed Resources 안에 있는 web.xml를 web2.xml로 이름을 바꾼다.
- Spring project  오른쪽 마우스 클릭
- java ee tools
- stub 클릭
- Spring project refresh 클릭
- web.xml에 사진부분을 복사

![화면 캡처 2021-03-16 232725](https://user-images.githubusercontent.com/60080744/111325607-30240d80-86af-11eb-9499-b2eada64f063.jpg)

- web.xml 삭제
- web2.xml 를 web.xml 바꿈
- pom.xml 에서 java version 1.8로 바꿈
- pom.xml 에서 수정할 부분이 많다.
- Maven repository 사이트에서 필요한 버전을 검색하여 일일히 수정해주어야한다.



## 2번째 방법

- Maven 연결 끊는다. 
  - Spring project 오른쪽 마우스 클릭
  - Maven
  - disable Maven
- pom.xml 삭제
- spring project 오른쪽 버튼 클릭
  - configure
  - convert to Maven project
  - pom.xml 생성됨
- 필요한 외부라이브러리를 추가해줘야한다
  - pom.xml에 삽입
  - <scope>test</scope> 지워준다.
- spring project 오른쪽 버튼 클릭
  - Maven
  - Update project



## Maven에서 산출물 만드는 방법

- Run as
- Maven Install
- Build가 성공되면 target에 들어가 있음
- war file에는 javax-servlet-api가 들어가지 않는다.



## RequestMapping

- RequestMapping의 주소로 요청 할 때 밑의 메소드를 실행



## Dispatcher

- localhost:8080/`context root`/만 실행하면 Dispatcher가 실행 된다.
- 단, 정적파일들은 cotroller에서 처리할 필요가 없다.
- web application context는 Dispatcher Servlet 등록하는 순간 만들어 진다.



## JSP 내에서 파일경로설정

- 파일 경로를 설정할 때 아래 두가지 중 하나로 설정하면 된다
  - `<%=application.getContext()%>/~~~`
  - `${pageContext.request.context}/~~~`

### redirect

- 해당 URL로 요청을 보냈지만 받아 들일 수 없어서 내가 보내주는 곳으로 다시 접속해