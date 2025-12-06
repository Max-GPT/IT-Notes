## 表单三要素
- 送去哪 `action="https://google.com/search"`
- 怎么送 method get post
- 送什么 input sumbit

```
<form action="http://bing.com/search" method="get">
    <input type="text" name="q" id="">
    <input type="submit" name="" id="">
</form>

<a href="http://google.com/search?q=天气" target="_self">Google搜索天气</a>
```

## 如何筛选元素id为 ul 下的所有特定元素？
```
document.querySelectorAll("#ul li.blue");
```
| 目标                 | 写法            |
| ------------------ | ------------- |
| 所有 `.blue` 元素      | `#ul .blue`   |
| 所有元素               | `#ul *`       |
| 所有 `.blue` 的 li 元素 | `#ul li.blue` |


## 动态改变元素 增删改
| 操作      | 推荐方法                         |
| ------- | ---------------------------- |
| 在末尾添加元素 | `append()` 或 `appendChild()` |
| 在开头添加元素 | `prepend()`                  |
| 在前后插入   | `before()` / `after()`       |
| 删除元素    | `remove()`                   |
| 删除子元素   | `removeChild()`              |
| 清空全部子节点 | `innerHTML = ""`             |



## 如何给一个id下的所有元素统一添加onclick？
```
initLiEvents()

function initLiEvents(){
    // 选中id为ul元素下的所有li标签
    var lis = document.querySelectorAll("#ul li");

    // 为数组lis里所有的元素添加上onclick
     lis.forEach(element => {
        element.onclick=function(){
            this.classList.toggle('selected');
        }
    });
}

<style>
    .selected{
        background-color: yellow;
    }
</style>
```


## 弹窗获取输入 `prompt`
```
var inputData = prompt("请输入数据")；
```


## `classList` 重要的几个方法
① `add()`：添加类名
```
element.classList.add("active");
```
② `remove()`：删除类名
```
element.classList.remove("active");
```
③ `toggle()`：有则删，无则加（最常用）
```
element.classList.toggle("active");
```
④ `contains()`：检查是否包含某个类
```
element.classList.contains("active");  
// 返回 true 或 false
```

⑤ `replace()`：替换类名
```
element.classList.replace("oldClass", "newClass");
```

## 标签
`<br>` → 换行 (break line)

`<hr>` → 分隔符 (horizontal rule) 水平线

`<ul>` → 无序列表（unordered list）
```
<ul>
  <li>苹果</li>
  <li>香蕉</li>
  <li>橘子</li>
</ul>
```
`<ol>` → 有序列表（ordered list）
```
<ol>
  <li>第一步</li>
  <li>第二步</li>
  <li>第三步</li>
</ol>
```
`<li>` → 列表项（list item）