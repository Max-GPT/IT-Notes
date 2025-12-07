# Java 学习笔记

## 逻辑运算符 短路运算
| 运算符 | 名称            | 是否短路 | 用途                     |
|--------|------------------|----------|---------------------------|
| `\|\|`   | 逻辑 OR          | ✔ 会短路 | if 条件判断（推荐）       |
| `&&`   | 逻辑 AND         | ✔ 会短路 | if 条件判断（推荐）       |
| `\|`    | 位 OR            | ✘ 不短路 | 位运算，不推荐用于逻辑     |
| `&`    | 位 AND           | ✘ 不短路 | 位运算，用于 boolean 有风险 |



## static + final 关键字
static：全程序共享，整个程序里只有一份
- static 变量 → 一份，共享
- static 方法 → 不用 new 对象就能用
- static 类 →（只能用于内部类，不是所有类都可以 static）

final：不能被重新赋值 / 不能被修改
- final 变量 → 不能重新赋值
- final 方法 → 不能被子类重写
- final 类 → 不能被继承
- 如果 final 是对象，里面的属性还是能改的（引用不能改，对象内容可以改）


## 注释
`/** ... */` Javadoc 注释 文档注释

`/* ... */` 普通块注释

## 引用数据类型 枚举 enum
```
enum Weekday {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
}
```
```
Weekday w = Weekday.MONDAY;
System.out.println(w);  // MONDAY
```
它代表什么意思？
- Monday 是一个对象
- Tuesday 也是一个对象
- 一共 7 个对象
- 程序启动时就自动创建
- 程序所有地方都共享这 7 个对象
- w 是一个指向 MONDAY 对象的指针
```
enum OrderStatus {
    NEW(1),
    PAID(2),
    SHIPPED(3),
    DONE(4);

    private int code;

    OrderStatus(int code) {
        this.code = code;
    }

    public int getCode() {
        return code;
    }
}
```
```
OrderStatus s = OrderStatus.SHIPPED;

System.out.println(s);            // SHIPPED
System.out.println(s.getCode());  // 3
```
它代表什么意思？
- NEW(1) → 创建了一个 OrderStatus 对象，内部 code=1
- PAID(2) → 创建另一个对象
- SHIPPED(3) → 第三个对象
- DONE(4) → 第四个对象
- 一共 4 个对象，整个程序共享

枚举 enum 是一个类，这个类在内部自动生成固定数量的对象，这些对象就是枚举常量，整个程序共享。


## 基本数据类型
Java 一共 8 个基本类型：

- byte / short / int / long

- float / double
- boolean
- char

## Java 命名规范
| 项目  | 写法例子                 | 是否大写 |
| --- | -------------------- | ---- |
| 类名  | `String`, `MyClass`  | 大写开头 |
| 方法名 | `print`, `getName()` | 小写开头 |
| 变量名 | `age`, `userName`    | 小写开头 |
| 常量名 | `MAX_LENGTH`, `PI`   | 全大写  |


## 函数
```java
public int sum(int a, int b) {
    return a + b;
}
# 修改