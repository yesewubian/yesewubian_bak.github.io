## 引用

对象通过引用来传递，它们永远不会被复制。

```javascript
var aa = {
    "name":"a",
}
var bb = aa;
bb.name = "bb";
var you_name = aa.name;
console.log(you_name);
// bb
```

## 原型

每个对象都连接到一个原型对象，并且可以从中继承属性。所有通过对象字面量创建的对象都连接到Object.prototype,它是JavaScript中的标准对象。原型链再更新时时不起作用的，只在索引的时候起作用