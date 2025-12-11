## 基本数据类型
Java 一共 8 个基本类型：

- byte / short / int / long

- float / double
- boolean
- char

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