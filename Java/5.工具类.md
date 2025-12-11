# Java 工具类
[ArrayList](#ArrayList)

[HashMap](#hashmap)

## 常用容器的长度获取方法
- 数组：`.length`
- 字符串：`.length()`
- 集合（List / Map / Set）：`.size()`

## <mark>ArrayList</mark> 

动态数组（可改变长度的数组）。
- 会自动扩容
- 可以随意添加、删除、修改、查询元素
- 元素允许重复，允许 null

创建 ArrayList
```
List<String> list = new ArrayList<>();
```
## 错误点 
### 把一个 list 里的数据添加到另一个 list 
 addAll 想打碎它，把里面的东西倒进去
 
 add 保留 List 这个壳（list 作为一个单独元素）

###  ArrayList 常用操作
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
有时候用add一个一个添加会很啰嗦。

asList可以一次添加。

```
List<String> list = Arrays.asList("A", "B", "C");
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
键值对（key-value） 数据结构。

钥匙 - 房间

key 不能重复
```
Map<KeyType, ValueType> map = new HashMap<>();
```
### HashMap 最常用操作
✔ `put( )` — 添加数据

✔ `putIfAbsent()` — 检测重复并添加数据  Absent 缺席
```
Map<String, String> map = new HashMap<>();
map.put("A001", "电脑");
map.put("A002", "手机");

map.putIfAbsent("A001", "电脑");
map.putIfAbsent("A001", "手机"); // 不会覆盖！
```
✔ keySet() — 返回所有 key 的集合 Set<K>

✔ values() — 返回所有 value 的集合 Collection<V>

✔ entrySet() — 返回 key + value 的键值对集合
`set<Map.Entry<K,V>>`

✔ `get()` — 根据 key 获取 value
```
String p = map.get("A001");
System.out.println(p); // 输出：电脑
```
✔ `containsKey()` — 是否存在这个 key
```
if (map.containsKey("A001")) {
    System.out.println("存在产品");
}
```
✔ `remove()` — 删除元素
```
map.remove("A002");
```

✔ `size()` — 大小
```
map.size();
```
✔ `clear()` — 清空
```
map.clear();
```

### HashMap 遍历方法
✔ 遍历 key 和 value（最常用）
```
for (Map.Entry<String, String> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " = " + entry.getValue());
}
```

✔ 遍历 key
```
for (String key : map.keySet()) {
    System.out.println("Key: " + key);
}
```

✔ 遍历 value
```
for (String value : map.values()) {
    System.out.println("Value: " + value);
}
```