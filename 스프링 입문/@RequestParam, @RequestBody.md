```
@Controller
public class HelloController {

    @GetMapping("hello-mvc")
    public String helloMvc(@RequestParam("name") String name, Model model) {
        model.addAttribute("name", name);
        return "hello-template";
    }
    
    @GetMapping("hello-string")
    @ResponseBody
    public String helloString(@RequestParam("name") String name) {
        return "hello" + name;
    }
    
    @GetMapping("hello-api")
    @ResponseBody
    public Hello helloApi(@RequestParam("name") String name) {
        Hello hello = new Hello();
        hello.setName(name);
        return hello;
    }
}
```

### @RequestParam  
- @RequestParam("가져올 데이터 이름") [데이터 타입] [가져온 데이터를 담을 변수] 
- url 뒤에 붙는 파라미터 값 가져올 때 사용 (여러 파라미터 가능)  
ex)  http://localhost:8080/hello-mvc?name=spring  

### @ResponseBody
- HTTP의 BODY에 문자 내용을 직접 반환 
- 객체를 반환하면 기본적으로 json 형태로 반환됨  
- viewResolver 대신 HttpMessageConverter가 동작함  
