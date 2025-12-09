# Java 工具类
[ArrayList](#ArrayList)

[HashMap](#hashmap)

## <mark>ArrayList</mark>
动态数组（可改变长度的数组）。
- 会自动扩容
- 可以随意添加、删除、修改、查询元素
- 元素允许重复，允许 null

创建 ArrayList
```
List<String> list = new ArrayList<>();
```
ArrayList 常用操作
1. 添加元素：`add()`
```
list.add("apple");
list.add("banana");
list.add("orange");
```
2. 指定位置插入元素: `add()`
```
list.add(1, "pear"); // 在索引 1 插入
```
3. 获取元素：`get()`
```
String fruit = list.get(0);
System.out.println(fruit);
```

4. 修改元素：`set()`
```
list.set(1, "grape");  // 把索引 1 位置改成 grape
```
5. 删除元素：`remove()`
```
// 按索引删
list.remove(0);

// 按元素删
list.remove("banana");
```
注意：<mark>如果放的是数字，必须区分 index 和 数字本身：</mark>
```
List<Integer> nums = new ArrayList<>();
nums.add(1);
nums.add(2);
nums.remove(1);     // 删除 index=1 的元素（即数字 2）

// 如果想删数字 1（元素本身）：
nums.remove(Integer.valueOf(1));
```
6. 判断是否包含元素：`contains()`
```
list.contains("apple"); // true or false
```
7. 获取大小：`size()`
```
int n = list.size();
```
8. 清空：`clear()`
```
list.clear();
```
9. 判断是否为空：`isEmpty()`
```
list.isEmpty();  // true / false
```

### 遍历 ArrayList
1. 增强 for 循环
```
for (String s : list) {
    System.out.println(s);
}

for (类型 变量名 : 集合或数组) {
    // 使用变量名
}
```

2. 经典 for（需要索引时用）
```
for (int i = 0; i < list.size(); i++) {
    System.out.println(list.get(i));
}
```


## <mark>HashMap</mark>

