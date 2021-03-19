# Controller

## RequestMapping

- HTTP 요청에 따라 요청 처리 및  Service로 처리 위임
- HTTP 응답 방법을 결정하고 뷰 이름 리턴



### 요청 경로를 메소드와 매핑하는 방법

- 클래스에 `@RequestMapping` 적용되면 공통 경로
- 메소드에 `@RequestMapping`, `@GetMapping`, `@PostMapping` 적용되면 세부 경로



### HTTP 구조

![화면 캡처 2021-03-19 002319](https://user-images.githubusercontent.com/60080744/111651193-5978a100-8849-11eb-908d-686e32a35eaa.jpg)

- 시작 행은 실행되어야 할 요청, HTTP 버전, 요청 수행에 대한 성공 또는 실패가 기록
- 헤더 행은 요청에 대한 설명, 메시지 본문에 대한 설명
- 빈행은 요청에 대한 모든 정보가 전송되었음을 알린다.
- 본문은 요청과 관련된 내용이 들어간다. 



### 요청 방식

#### GET

- URL에 파라미터를 포함시켜 요청하는 방식
- 데이터를 헤더에 포함
- 보안에 취약
- 캐시가능

##### 방법

- `<a>`태그로 요청
- `<form action="get">` 요청
- ajax method get 요청
- location.href 에 parameter 붙여서 요청



#### POST

- BODY에 데이터를 넣어 전송
- 요청 헤더에 `Content-Type`에 요청 데이터 타입을 명시해야한다.
  - `application/x-www-form-urlencoded`
    - GET방식과 마찬가지로 BODY에 `key`와 `value`쌍으로 데이터를 넣는다. 똑같이 구분자 &를 쓴다.
- `text/plain`
  - Body에 단순 텍스트를 넣는다.
- `multipart/form-data`
  - 파일전송을 할때 많이 쓰는데 BODY의 데이터를 바이너리 데이터로 넣는다는걸 알려준다.



##### 방법

- `<form action="post">` 요청
- ajax method post 요청



#### 요청방식 매핑

- GET/POST 모두 허용
  - @RequestMapping("/경로")
- GET 방식 허용
  - @RequestMapping(value="/경로", method=RequestMethod.GET)
  - @GetMapping("/경로")
- POST 방식 허용
  - @RequestMapping(value="/경로", method=RequestMethod.POST)
  - @PostMapping("/경로")



## 요청 파라미터 얻기

### 요청 파라미터명과 매개변수명이 같을 경우

```html
<a href="method1?param1=1"></a>

<form method="post" action="method1">
    param1 : <input type="text" name="param1"/>
</form>
```

```java
@RequestMapping("/method1")
public String mehtod1(String param1) {
    pass
}
```



### 요청 파라미터명과 매개변수명이 다를 경우

```html
<a href="method1?param1=1"></a>

<form method="post" action="method1">
    param1 : <input type="text" name="param1"/>
</form>
```

```java
@RequestMapping("/method1")
// param1을 arg1으로 바꿈
public String mehtod1(@RequestParam("param1") String arg1) {
    console.log(arg1);
}
```



### 디폴트값

```java
@RequestMapping("/method1")
public String method1(@RequestParam(defaultValue="문자열") String param1) {
    
}
```



## 넘겨주기

```java
@RequestMapping("/method1")
public String method1(HttpServletRequest request, HttpServletResponse response) {
    logger.info("실행");
    // getParamter로 파라미터 값을 얻는다.
    String name = request.getParameter("name");
    
    request.setAttribute("username", name);
    return "exam02/method1";
```

