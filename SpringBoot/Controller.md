# 「整体认知」

### Controller 层用 DTO，Service 内部用 Entity
```
Controller —— DTO

Service —— 业务 + Entity

Repository —— Entity + SQL
```

## Spring Boot 项目结构一眼看懂
```
src
 └─ main
    ├─ java
    │   └─ com.example.demo
    │       ├─ controller
    │       ├─ service
    │       └─ DemoApplication.java
    └─ resources
        ├─ application.yml   ← ⭐ 放这里
        ├─ static
        └─ templates
```
- resources 用来放 "非 Java 代码，但程序运行时要用的东西"
- 包名规则:公司域名反过来 + 项目名`com.google.xxx`

| 类型         | 举例                    |
| ---------- | --------------------- |
| 配置文件       | `application.yml`     |
| 页面模板       | `templates/`          |
| 静态资源       | `static/`             |
| 国际化        | `messages.properties` |
| mapper XML | MyBatis XML           |

### static vs templates
| 对比             | static | templates |
| -------------- | ------ | --------- |
| 是否走 Controller | ❌      | ✅         |
| 是否可写变量         | ❌      | ✅         |
| 是否后端渲染         | ❌      | ✅         |
| 前后端分离          | ✅      | ❌         |
| 传统 MVC         | ❌      | ✅         |

templates 放的是“要被后端渲染的 HTML 模板”.

也就说 templates 的 HTML 里有变量，要后端塞数据进去

static 放的是“不会被后端加工的前端资源”
```
static/
 ├─ css/
 ├─ js/
 ├─ images/
 └─ favicon.ico
```

## controller 接受参数 返回数据的流程
```
HTML / 前端
  ↓ 参数（URL / Path / JSON）
Controller
  ↓
Service
  ↓
Controller
  ↓ 返回（HTML / JSON / 状态码）
前端
```

## controller 是从 HTTP 的哪一部分拿数据？

### HTTP 结构
先理解 HTTP 请求长什么样（关键）

一个 HTTP 请求可以拆成：
```
POST /user/1?type=admin HTTP/1.1
Host: localhost:8080
Content-Type: application/json

{
  "name": "Tom",
  "age": 20
}
```
我们来标记三种数据来源👇
```
/user/1          ← 路径变量
?type=admin      ← URL 参数
{ ... }          ← 请求体（JSON）
```
对应三个注解
```
@PathVariable // “你在操作哪个资源”
@RequestParam // 传“附加条件 / 可选参数”
@RequestBody // 传“结构化、复杂数据”
```

### 三种数据来源 三个注解 
| 注解              | 数据来自哪里             | URL 示例       | 
| --------------- | ------------------ | ------------ | 
| `@RequestParam` | **URL 查询参数**       | `/user?id=1` | 
| `@PathVariable` | **URL 路径本身**       | `/user/1`    | 
| `@RequestBody`  | **HTTP 请求体（Body）** | POST JSON    | 

##  controller 返回数据的几种方法？
| 返回方式   | 注解 / 写法            | 返回给前端的是什么    | 典型场景   |
| ------ | ------------------ | ------------ | ------ |
| 返回页面   | `String` + `Model` | HTML 页面      | 传统 MVC |
| 返回数据   | 对象 / List / Map    | JSON         | 前后端分离  |
| 返回完整响应 | `ResponseEntity`   | 状态码 + 头 + 数据 | 标准接口   |

### 返回 HTML 页面（@Controller）
1️⃣ 最基础写法：返回页面名
```
@Controller
public class PageController {

    @GetMapping("/hello")
    public String hello() {
        return "hello";
    }
}
```
Spring 会去找：
```
resources/templates/hello.html
```
2️⃣ 带数据返回页面（Model）
```
@Controller
public class PageController {

    @GetMapping("/hello")
    public String hello(Model model) {
        model.addAttribute("msg", "Hello Spring");
        return "hello";
    }
}
```
HTML 里：
```
<p th:text="${msg}"></p>
```
📌 Model = 给 HTML 的数据盒子

### 返回数据（JSON）（@RestController）
1️⃣ 返回字符串
```
@RestController
public class ApiController {

    @GetMapping("/api/hello")
    public String hello() {
        return "ok";
    }
}
```

前端收到：
```
ok
```
2️⃣ 返回对象（最常用）
```
@RestController
public class ApiController {

    @GetMapping("/api/user")
    public User user() {
        return new User(1, "Tom");
    }
}
```

前端收到：
```
{
  "id": 1,
  "name": "Tom"
}
```
3️⃣ 返回 List / Map
```
@GetMapping("/users")
public List<User> list() {}
```
```
@GetMapping("/map")
public Map<String, Object> map() {}
```
### 返回 HTTP 的“完整控制权”（进阶）ResponseEntity
```
@GetMapping("/user/{id}")
public ResponseEntity<User> get(@PathVariable int id) {
    User user = findUser(id);
    if (user == null) {
        return ResponseEntity.notFound().build();
    }
    return ResponseEntity.ok(user);
}
```
你能控制：
```
状态码（200 / 404 / 400）
响应头
响应体
```
📌 专业接口必备