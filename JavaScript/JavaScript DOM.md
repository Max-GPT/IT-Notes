## JavaScript DOM 动态 添加 / 删除元素
| 操作           | 方法                           | 说明           |
| ------------ | ---------------------------- | ------------ |
| **创建元素**     | `document.createElement()`   | 创建标签         |
| **插入（最后）**   | `appendChild()` / `append()` | 最常用          |
| **插入（最前）**   | `prepend()`                  | 第一个位置        |
| **插入（指定位置）** | `insertBefore()`             | 在某个元素前       |
| **删除元素**     | `removeChild()` / `remove()` | remove() 更现代 |
| **清空内容**     | `innerHTML = ''`             | 删除所有子节点      |

## 已经靠id定位元素，DOM 关系操作表
| 作用        | 属性                             |
| --------- | ------------------------------ |
| 父元素       | `parentNode` / `parentElement` |
| 向上查找最近的祖先 | `closest(selector)`            |
| 全部子元素     | `children`                     |
| 第一个子元素    | `firstElementChild`            |
| 最后一个子元素   | `lastElementChild`             |
| 上一个兄弟     | `previousElementSibling`       |
| 下一个兄弟     | `nextElementSibling`           |


## 1. 事件类型
##### 点击事件 onclick
```
<button onclick="alert('点击')">Click</button>
```
##### 改变事件 onchange

##### 焦点事件 onfocus
##### 失去焦点 onblur

##### 加载事件 onload
##### 表单事件 onsubmit

## 2. 获取事件源头

##### 按 ID 获取
```
const el = document.getElementById("myId");
```
##### 按 class 获取



## 3. 获取元素值
对象的 .value
```
var obj = document.getElementById('textID');
obj.value = "Hello World"
```


## 元素奇偶变色
寻找子类 `.children`

改变样式 `.style='background-color:` 
```
function changeColor(){
            var allTrObj = document.getElementById('mailTboby').children
            for (let index = 0; index < allTrObj.length; index++) {
                if(index % 2==0){
                    allTrObj[index].style='background-color: beige;'
                }else{
                    allTrObj[index].style='background-color: lightgrey;'
                }
            }
        }
```

## 删除元素
`tbody.removeChild(trObj)`

父元素删除子元素 
```
function deleteInfo(thisButton){
    console.log(thisButton)
    var trObj=thisButton.parentNode.parentNode
    
    var tbody =document.getElementById('mailTboby')
    tbody.removeChild(trObj)

    changeColor()
}
```

## 更新元素
`var trObj=thisButton.parentNode.parentNode`

找到要修改的节点

`trObj.children[0].innerHTML=prompt('请输入新的姓名')`

从大的父节点定位要修改的子节点

```
function updateInfo(thisButton){ 
    console.log(thisButton)
    var trObj=thisButton.parentNode.parentNode
    
    trObj.children[0].innerHTML=prompt('请输入新的姓名')
    trObj.children[1].innerHTML=prompt('请输入新的邮箱')
}
```


## 给元素添加点击事件
```
<ul id="ul">
    <li>html</li>
    <li>css</li>
    <li>javascript</li>
    <li>java</li>
</ul>
```

```
// 绑定选择变色
initLiEvents()

function initLiEvents() {
    var lis = document.querySelectorAll("#ul li");

    // 初始给所有li标签添加点击事件
    lis.forEach(element => {
        element.onclick=function(){
            this.classList.toggle('selected');
        }
    });
}
``` 
要绑定的css
```   
<style>
    .selected {
        background-color: yellow;
    }
</style>
```
后续新增加的也要添加
```
function addLi() {
    var addText = prompt("输入新增加列表内容")
    var ulOBj = document.getElementById('ul')
    var newUl = document.createElement('li')
    newUl.innerHTML = addText

    //这里添加了绑定方法
    newUl.onclick= function(){
        this.classList.toggle('selected')
    }
    ulOBj.appendChild(newUl);
}
```
选出所有添加的删除
```
function delSelected(){
    var ul=document.getElementById('ul')
    var selectedLi=document.querySelectorAll("#ul li.selected")

    selectedLi.forEach(element => {
        ul.removeChild(element)
    });
}
```