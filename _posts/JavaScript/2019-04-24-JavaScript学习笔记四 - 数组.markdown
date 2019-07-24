## 数组

数组的所有元素可以不是同一种类型， 数组继承Array.prototype。

### 长度

每个数组都有length属性，length的属性值是这个数组的最大整数属性名加1，它不一定等于数组的属性个数。设置更大的length属性不会给数组分配更大的空间，而把length设小将导致所有下标大于等于length的属性被删除。
```javascript
var arr = [1,2,3];

//向数组尾部添加新元素的两种方式
arr[arr.length] = 5;

arr.push(6);

```
### 删除

```javascript
var arr = [1,2,3];
delete arr[0];
// arr 是 [undefined,2,3]
```
JavaScript的数组就是对象，delete可以从数组中删除元素。不幸的是，那样会在数组中留下空洞。数组有个splice方法，可以从数组中删除一部分元素，并把后面的元素重新插入，这对大型数组来说可能效率不高。

### 枚举

因为JavaScript的数组其实是对象，所以for in 语句可以用来遍历数组的所有属性。遗憾的是for in 无法保证属性的顺序，并可能从原型链得到意外的属性。幸运的for语句可以避免这些问题。

### 易混淆

可以自定义函数来区分数据类型
```javascript
var is_array = function(value) {
  return Object.prototype.toString.apply(value) === '[object Array]';
}
```

### 方法

JavaScript提供一套数组可用的方法，这些方法被储存在Array.prototype中，Array.prototype可以被扩充。因为数组就是对象，所以我们可以直接给一个单独的数组添加方法

array.concat(item...) 拼接数组
array.join(separator) 复制元素拼成字符串
array.pop() 移除最后一个元素并返回
array.push(item...)  
array.reverse() 翻转
array.shift() 移除第一个元素并返回
array.slice() 复制
array.sort() 排序
array.splice() 移除替换
array.unshift() 在头部插入


### 初始值

JavaScript的数组不会预置值，如果你用[]得到一个新数组,它将是空的。如果你访问一个不存在的元素，得到的值则是undefined.