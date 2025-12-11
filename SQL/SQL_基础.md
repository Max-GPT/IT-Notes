## MySQL
SQL = Structured Query Language  结构化查询语句

A5M2 (エーゴエムツー)

## SQL 语法
[BETWEEN AND](#BETWEEN-AND)

[IN](#IN)

## 多表查询 连接方式
| 连接类型 | SQL 语法示例 | 返回结果 | 说明 |
|----------|--------------|----------|------|
| 内连接 (INNER JOIN) | `SELECT * FROM table1 INNER JOIN table2 ON table1.col = table2.col;` | 仅返回满足条件的匹配行 | 不匹配的行不会显示 |
| 左连接 (LEFT JOIN) | `SELECT * FROM table1 LEFT JOIN table2 ON table1.col = table2.col;` | 返回左表所有行，右表无匹配列显示 NULL | 保留左表所有数据 |
| 右连接 (RIGHT JOIN) | `SELECT * FROM table1 RIGHT JOIN table2 ON table1.col = table2.col;` | 返回右表所有行，左表无匹配列显示 NULL | 保留右表所有数据 |
| 全连接 (FULL OUTER JOIN) | `SELECT * FROM table1 LEFT JOIN table2 ON table1.col = table2.col UNION SELECT * FROM table1 RIGHT JOIN table2 ON table1.col = table2.col;` | 返回左右表所有行，无匹配列显示 NULL | MySQL 不直接支持，需要用 UNION 模拟 |
| 交叉连接 (CROSS JOIN) | `SELECT * FROM table1 CROSS JOIN table2;` | 左表 × 右表所有组合 | 笛卡尔积，返回所有可能组合 |
| 自连接 (SELF JOIN) | `SELECT a.*, b.* FROM table1 a INNER JOIN table1 b ON a.manager_id = b.id;` | 表自身的匹配行 | 用于找同类关系，如员工与经理 |


## BETWEEN AND
```
-- 查询年龄在 18 到 30 岁之间的用户
SELECT * FROM users
WHERE age BETWEEN 18 AND 30;
```
```
-- 查询年龄不在 18 到 30 岁之间的用户
SELECT * FROM users
WHERE age NOT BETWEEN 18 AND 30;
```

## IN
```
-- 查询城市在北京、上海、广州的用户
SELECT * FROM users
WHERE city IN ('北京', '上海', '广州');
```
```
-- 查询城市不是北京、上海、广州的用户
SELECT * FROM users
WHERE city NOT IN ('北京', '上海', '广州');
```


### 注释
`-- SQL注释`

### 导出数据
- Export data
- CSV
- Encoding: UTF-8 


### 数据类型
|数据类型|用法|
|:--:|:--:|
|`datetime`| 时间不会根据时区变更|
|`timestamp`| 时区信息|
|`char`| 固定长度|
|`varchar`| 可变长度|


### 约束 CONSTRAINT 
|约束|用法|
|:--:|:--:|
|`PRIMARY KEY`|唯一，不为空|
|`unique`|不可以重复，但是可以空|
|`not null`|不能为空|
|`default`|默认值|

主键
```
CREATE TABLE users (
    id INT PRIMARY KEY,      -- 主键
    name VARCHAR(50)
);
```
```
CREATE TABLE course_enrollments (
    student_id INT,
    course_id INT,
    PRIMARY KEY (student_id, course_id)  -- 两列一起作为主键
);
```

外键
```
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)  -- 外键引用 users 表的 id
        ON DELETE CASCADE  -- 用户删除时，该用户的订单也删除
        ON UPDATE CASCADE  -- 用户 id 改变时，订单表同步更新
);
```
DELETE ???   -- 删除父表用户时子表行为

ON UPDATE ???   -- 更新父表用户 id 时子表行为
|选项||
|:--:|:--:|
|`CASCADE`|父表删除/更新，子表也跟着删除/更新|
|`SET NULL`|父表删除/更新时，子表对应列变成 NULL|
|`NO ACTION / RESTRICT`|阻止父表删除或更新，如果子表有依赖记录|



### 把 MySQL 注册成 Windows 的系统服务
```
cd C:\Program Files\MySQL\MySQL Server 8.0\bin

mysqld --install mysql
```

启动 MySQL：
```
net start mysql
```
停止 MySQL：
```
net stop mysql
```
查看服务状态：
```
sc query mysql
```