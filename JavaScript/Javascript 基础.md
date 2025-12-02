## VSCode快捷键
注释 Ctrl + /

## 运算符
```
var a = 100
console.log( ++a ) 先计算再输出 输出101
console.log( a-- ) 先输出再计算 输出100
```

## JavaScript 的引入方式
### 1. 内联
```
<button onclick="alert('Hello World!')">点击我</button>

<input value="按钮" type="button" onclick="alert('Hello World!!行内式')">
```

### 2. 内部脚本
```
<head>
  <title>内部脚本示例</title>
  <script>
    function sayHello() {
      alert('Hello World!');
    }
  </script>
</head>
```

### 3. 外部脚本

引入格式
```
<head>
  <title>外部脚本示例</title>
  <script src="script.js"></script>
</head>
```

script.js 文件：
```
function sayHello() {
  alert('Hello World!');
}
```

## 一些用法
```
<script>
    alert(90);
    alert('Hello World!弹出提示');

    prompt('弹出输入框')

    document.writeln('页面输出')

    console.log('控制台打印')
</script>
```


## 常用函数 语法
- typeof a
```
var a = 90
var b = "Hello"
console.log(typeof a,typeof b)
```

- isNaN()
```
console.log(isNaN(a)) //数字，结果false
console.log(isNaN(b)) //字符串，结果true
```

- 字符串 单引号 双引号
```
let msg = "I'm Max";   // ✔ 这样写很方便
let msg = 'I\'m Max';  
```

- 字符串长度
```
let name = "JavaScript";
console.log(name.length);  

var fullName = name + "Java" //字符串拼接
```

- Null undefined
```
var A;
console.log(A + 1); 
//结果为 NaN
console.log(A + "-Hello"); 
//结果为 undefined-Hello

var B= null;
console.log(B + 1); 
//结果为 1
console.log(B + "-Hello"); 
//结果为 null-Hello
```

- 值类型转换

parseInt( )
```
var number = "777"
var afterNumber = parseInt(number)
```
还有parseFloat( ) 

- 显示转换
```
Number("123");     // 123
Number("123abc");  // NaN
Number(true);      // 1
Number(false);     // 0
Number(null);      // 0
Number(undefined); // NaN

String(123);       // "123"
String(true);      // "true"
String(null);      // "null"
String(undefined); // "undefined"

(123).toString();  // "123"
true.toString();   // "true" 
// toString 对于null 和 undefined 不可用

Boolean(1);         // true
Boolean(0);         // false
Boolean("");        // false（空字符串为 false）
Boolean("hello");   // true
Boolean(null);      // false
Boolean(undefined); // false
Boolean([]);        // true（数组为 true）
Boolean({});        // true（对象为 true）
```

- 隐式转换
```
1 + "2"   // "12"
true + "" // "true"

// 除了 + 号会触发拼接，其它都是转数字
"3" - 1   // 2

"1" == 1      // true
0 == false    // true
"" == false   // true
null == undefined // true

因为自动转换太混乱，所以推荐用 ===（严格比较）。

```

- 最常用

|目标类型|常用写法|
|---|---|
|数字|Number(x)、+x|
|字符串|String(x)、x + ""、toString(x)|
|布尔|Boolean(x)、!!x|
|JSON 对象 → 字符串|JSON.stringify(x)|
|字符串 → JSON 对象|JSON.parse(x)|

- 数组

数组中添加元素 push( ) pop( )


| 语言         | 是否允许数组混合类型       | 原因                 |
| ---------- | ---------------- | ------------------ |
| JavaScript | ✔ 允许             | 动态类型，不检查数组元素类型     |
| Python     | ✔ 允许             | 动态类型，list 可以存任何对象  |
| Ruby       | ✔ 允许             | 动态类型               |
| PHP        | ✔ 允许             | 数组是“字典+列表”，可以混合    |
| Java       | ⚠ 仅 Object[ ] 能混合 | 静态类型，数组需要声明类型      |
| C#         | ⚠ 仅 object[ ] 能混合 | 静态类型               |
| C/C++      | ❌ 通常不允许          | 数组元素必须同一类型         |
| Go         | ❌ 不允许            | 数组强类型，slice 也要一致类型 |

数组排序 sort( )

数组反转 reverse( )

数组连接2数组 concat( )


- JavaScript 的函数声明会被提升
```
function A() {
  console.log("B");
}

A();

function A() {
  console.log("C");
}
```
JS 的行为是：

函数声明会被整体提升到作用域顶部，并且后声明的会覆盖前面的。

最后输出是 C。

- 数组复制
