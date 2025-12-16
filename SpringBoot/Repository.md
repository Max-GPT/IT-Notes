# JPA vs MyBatis
| 对比点        | JPA          | MyBatis    |
| ---------- | ------------ | ---------- |
| 思想         | **面向对象**     | **面向 SQL** |
| SQL        | 自动生成         | 手写         |
| Repository | 接口           | 接口         |
| 实现类        | Hibernate 生成 | MyBatis 代理 |
| 复杂查询       | 较难           | 非常强        |
| 学习成本       | 低            | 中          |
| 可控性        | 较弱           | 极强         |


## MyBatis

接口定义方法，XML 写 SQL

## MyBatis 接口 + XML 的标准写法
### 1️⃣ Entity（和 JPA 类似）
```
public class User {
    private Long id;
    private String name;
    private Integer age;
}
```
📌 MyBatis 不强制用注解（@Entity 不需要）

### 2️⃣ Mapper 接口（Repository 层）
```
@Mapper
public interface UserMapper {

    User selectById(Long id);

    int insert(User user);

    List<User> selectAll();
}
```
📌 这是接口，没有实现类

### 3️⃣ XML 文件（真正的 SQL 在这）
```
<!-- resources/mapper/UserMapper.xml -->
<mapper namespace="com.example.demo.mapper.UserMapper">

    <select id="selectById" resultType="User">
        SELECT id, name, age
        FROM user
        WHERE id = #{id}
    </select>

    <insert id="insert">
        INSERT INTO user(name, age)
        VALUES (#{name}, #{age})
    </insert>

</mapper>
```
📌 XML 中的 id 必须和接口方法名一一对应

### 4️⃣ Service 调用 Mapper
```
@Service
public class UserService {

    private final UserMapper userMapper;

    public UserService(UserMapper userMapper) {
        this.userMapper = userMapper;
    }

    public User get(Long id) {
        return userMapper.selectById(id);
    }
}
```
📌 Spring 启动时会自动帮你生成 Mapper 的代理实现