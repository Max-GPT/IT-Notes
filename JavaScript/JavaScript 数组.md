## 数组开头插入数据 `unshift( )`
```
const arr = [2, 3, 4];

// 在开头插入一个元素
arr.unshift(1);
console.log(arr); // [1, 2, 3, 4]

// 插入多个元素
arr.unshift(-1, 0);
console.log(arr); // [-1, 0, 1, 2, 3, 4]

```

## 删除数组开头元素：`shift( )`
```
const arr = [1, 2, 3, 4];

const first = arr.shift();  // 删除开头元素
console.log(first);         // 1
console.log(arr);           // [2, 3, 4]
```

## 结尾插入数据 `push( )`
```
arr.push({ name: 'Alice', age: 19, gender: '女' });
```

## 删除数组末尾元素 `pop()`
```
const arr = [1, 2, 3, 4];
const last = arr.pop();  // 删除末尾元素
```

## 复制数组 `[...arr1]`
```
var arr1 = [1, 2, 3];
var arr2 = [...arr1];
```


## 数组长度 `arr.length`
- sort( )
- reverse( )

## 拼接数组 `concat( )`
```
var arr1 = [1, 2];
var arr2 = [3, 4];

var result = arr1.concat(arr2);
```