## 继承

代码重用的一种方式。类继承的另一个函数是引入了一套类型系统的规范。JavaScript是一门基于原型的语言，这意味着对象直接从其他对象继承。

### 伪类

JavaScript不直接让对象从其它对象继承，反而插入一个间接层：通过构造器函数产生对象。
```javascript
    var People = function (name) {
        this.temp_name  = name;
    }
    People.prototype.get_name = function (){
        console.log(this.temp_name);
    }

    var Chinese = function(age){
        this.age = age;
    }
    Chinese.prototype = new People(3333);
    Chinese.prototype.get_age = function(){
        console.log(this.age);
    }

    myChinese = new Chinese(20);
    console.log(myChinese.prototype);
    myChinese.get_age();
    myChinese.get_name();
```

### 对象说明符

### 原型

基于原型的继承比基于类的继承根据简单，一个新对象可以继承旧对象的属性。
