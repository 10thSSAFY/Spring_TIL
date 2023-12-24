[main](../..)

## MVC와 템플릿 엔진
- MVC: Model, View, Controller

**Controller**
```java
@Controller
public class HelloController {

    @GetMapping("hello-mvc")
    public String helloMvc(@RequestParam("name") String name, Model model) {
        model.addAttribute("name", name);
        return "hello-template";
    }
}
```

**View**
`resources/template/hello-template.html`
```html
<html xmlns:th="http://www.thymeleaf.org">
<body>
<p th:text="'hello ' + ${name}">hello! empty</p>
</body>
</html>
```

**실행**
- http://localhost:8080/hello-mvc?name=spring


![img](https://blog.kakaocdn.net/dn/J7iI5/btruiQvjqVH/UTkr11DxkZJZ9YuiOwZN81/img.png)