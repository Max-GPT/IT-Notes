# Java 学习笔记

## super() 不是函数，而是 关键字语法
在子类构造函数中，调用父类的构造函数。

1. 你手写 super()
```
class Child extends Parent {
    Child() {
        super();  // 调用父类构造函数
        System.out.println("子类构造");
    }
}
``` 
2. 你不写 super()，Java 会自动帮你写
```
Child() { 
    // Java 会自动加：super();
}
```
但前提是：父类必须有 无参构造函数。


## 基本类型的<mark>包装类</mark>
八个基本类型是 非对象，不能直接用于许多 需要对象 的场景，所以需要 包装类（Wrapper Class）。
| 基本类型    | 包装类       |
| ------- | --------- |
| int     | Integer   |
| double  | Double    |
| boolean | Boolean   |
| char    | Character |
| 其他同理    | 
 
包装类的意义

1. 让基本类型可以当对象使用
```
List<int> list; // ❌ 不允许
List<Integer> list; // ✔ 用包装类
```
2. 提供丰富的工具方法
```
Integer.parseInt("123");
Boolean.parseBoolean("true");
Double.isNaN(x);
```
3. 支持 null
```
Integer count = null; // ✔ 允许
int count = null;     // ❌ 不允许
```

## 自动拆箱 自动装箱
指 基本类型 / 包装类 之间互相转换
```
Integer a = 10; // 自动把 int 10 转成 Integer.valueOf(10)
Integer a = Integer.valueOf(10); // 相当于：
```
```

int b = a;            // 自动拆箱，相当于 a.intValue()
int b = a.intValue(); // 相当于：
```

 
## 数组常用方法
- 输出 Arrays.toString(arr)
- 排序 Arrays.sort(arr)
- 查找 Arrays.binarySearch(arr,key)
- 复制 Arrays.copyOf(arr,newLength)
- 比较 Arrays.euqals(arr1,arr2)
- 填充 Arrays.fill(arr,val)

## 快速输出数组
```
// 控制台输出数组 arr
System.out.println(Arrays.toString(arr));
```

## 比较数组
如果使用 == 比较数组，比较的是数组的地址，结果为false

要使用 `Arrays.equals( a , b )`

## 数组的 foreach 遍历
```
int[] numbers = {1, 2, 3, 4, 5};

for (int n : numbers) {
    System.out.println(n);
}
```
```
for (类型 变量名 : 数组名) {
    // 使用变量名
}
```
foreach 不能做这些：
- 不能通过索引访问元素（比如 arr[i]）
- 不能直接删除元素
- 不能修改数组长度（数组本来就固定长度）


## 局部 / 实例 / 静态 变量
| 位置          | 名称                       | 特点        |
| ----------- | ------------------------ | --------- |
| **类里（方法外）** | **实例变量**（没有 static）      | 每个对象一份    |
| **类里（方法外）** | **类变量**（static 变量）       | 全类共享一份    |
| **方法内部**    | **局部变量（local variable）** | 方法结束后自动消失 |


## 三元运算符
```
int age = 20;
String type = age >= 18 ? "adult" : "child";
```
三元运算符可以嵌套，比如：
```
int score = 85;
String grade = score >= 90 ? "A" :
               score >= 80 ? "B" :
               score >= 70 ? "C" : "D";

System.out.println(grade); // B
```

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