## 比较值

基本数据类型 可以用 == 直接比较

引用数据类型 == 比较的是 内存地址

❌ == 不能用来比较字符串内容
```
String a = "abc";
String b = new String("abc");

a == b; // false
```
✅ .equals() 才能正确比较字符串内容
```
a.equals(b); // true
```

# 1. 数组

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

# 2.枚举
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