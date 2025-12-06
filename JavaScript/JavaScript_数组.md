## 数组有负数时候排序
默认排序是按字符串，再按 Unicode 编码排序，会导致负数排序不正确
```
const arr = [3, -2, 10, -5, 0];
arr.sort();
console.log(arr); // [-2, -5, 0, 10, 3] ❌
```
比较函数
```
const arr = [3, -2, 10, -5, 0];

// 升序
arr.sort((a, b) => a - b);
console.log(arr); // [-5, -2, 0, 3, 10]

// 降序
arr.sort((a, b) => b - a);
console.log(arr); // [10, 3, 0, -2, -5]
```

## 数组 开头插入 `unshift( )`
```
const arr = [2, 3, 4];

// 在开头插入一个元素
arr.unshift(1);
console.log(arr); // [1, 2, 3, 4]

// 插入多个元素
arr.unshift(-1, 0);
console.log(arr); // [-1, 0, 1, 2, 3, 4]

```

## 数组 开头删除`shift( )`
```
const arr = [1, 2, 3, 4];

const first = arr.shift();  // 删除开头元素
console.log(first);         // 1
console.log(arr);           // [2, 3, 4]
```

## 数组 末尾插入 `push( )`
```
arr.push({ name: 'Alice', age: 19, gender: '女' });
```

## 数组 末尾删除 `pop()`
```
const arr = [1, 2, 3, 4];
const last = arr.pop();  // 删除末尾元素
```

## 数组复制 `[...arr1]`
```
var arr1 = [1, 2, 3];
var arr2 = [...arr1];
```


## 数组长度 `arr.length`
- sort( )
- reverse( )

## 数组拼接 `concat( )`
```
var arr1 = [1, 2];
var arr2 = [3, 4];

var result = arr1.concat(arr2);
```