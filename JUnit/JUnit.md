层级关系
```
Java
 ↑
JUnit   ←—— 负责“怎么写测试”
 ↑
Spring Test  ←—— 负责“怎么测 Spring”
 ↑
Spring Boot Test ←—— 负责“帮你都配好”
```
- 在 Spring Boot 项目中
- JUnit 负责测试框架本身
- Spring Test 负责 Spring 容器的测试支持，
- Spring Boot Test 在此基础上做了自动配置和封装。

## 测试 Controller 层
```
@WebMvcTest(UserController.class)
class UserControllerTest {

    @Autowired
    private MockMvc mockMvc;

    @MockBean
    private UserService userService;

    @Test
    void getUser_should_return_user() throws Exception {

        User mockUser = new User(1L, "Tom");

        when(userService.getUserById(1L))
                .thenReturn(mockUser);

        mockMvc.perform(get("/users/1"))
               .andExpect(status().isOk())
               .andExpect(jsonPath("$.name").value("Tom"));
    }
}
```
### 第一步：`@WebMvcTest`

只启动 Web 层

加载 UserController

### 第二步：`@MockBean UserService`

Spring 放一个 假的 UserService

自动注入进 Controller

### 第三步：`when(...).thenReturn(...)`

你在说：

“当 Controller 调用
`userService.getUserById(1L)`
就返回我准备好的假数据”

### 第四步：`perform(...)`

模拟请求 /users/1

Controller 被调用

### 第五步：`andExpect(...)`

验证返回结果