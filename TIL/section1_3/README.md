[main](../..)
## View 환경설정

### Welcome Page 만들기
`resources/static/index.html`
```html
<!doctype html>
<html>
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
Hello
<a href="/hello">hello</a>
</body>
</html>
```
- 스프링 부트가 제공하는 Welcome Page 기능
    - `static/index.html`을 올려두면 Welcome page 기능을 제공한다.
    - https://docs.spring.io/spring-boot/docs/3.2.1/reference/htmlsingle/#web.servlet.spring-mvc.welcome-page

### thymeleaf 템플릿 엔진
- thymeleaf 공식 사이트: https://www.thymeleaf.org/
- 스프링 공식 튜토리얼: https://spring.io/guides/gs/serving-web-content/
- 스프링부트 메뉴얼: https://docs.spring.io/spring-boot/docs/3.2.1/reference/htmlsingle/#web.servlet.spring-mvc.template-engines

```java
@Controller
public class HelloController {

    @GetMapping("hello")
    public String hello(Model model) {
        model.addAttribute("data", "hello!!");
        return "hello";
    }
}
```

`resources/templates/hello.html`
```html
<!doctype html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
    <title>Hello</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
<p th:text="'안녕하세요. ' + ${data}" >안녕하세요. 손님</p>
</body>
</html>
```

**thymeleaf 템플릿엔진 동작 확인**
- 실행: http://localhost:8080/hello<br>
![img](https://velog.velcdn.com/images/junsj119/post/8f5938a4-b7e4-46a2-963b-7084f4486366/image.png)

- 컨트롤러에서 리턴 값으로 문자를 반환하면 뷰 리졸버(`viewResolver`)가 화면을 찾아서 처리한다.
    - 스프링 부트 템플릿엔진 기본 viewName 매핑
    - `resources:templates/`+{ViewName}+`.html`

    참고: `spring-boot-devtools`라이브러리를 추가하면, `html`파일을 컴파일만 해주면 서버 재시작 없이 View 파일 변경이 가능하다.<br>
    인텔리J 컴파일 방법: 메뉴 build -> Recomplie
