# 知识点
## task0002 JavaScript数据类型及语言基础
### 检测数据类型
* `typeof` 返回一个字符串,指示未经计算的操作数的类型
    * `typeof null === 'object'`
    * 对正则表达式字面量的类型判断在某些浏览器中不符合标准：
    ```
    typeof /s/ === 'function'; // Chrome 1-12 , 不符合 ECMAScript 5.1
    typeof /s/ === 'object'; // Firefox 5+ , 符合 ECMAScript 5.1
    ```

* `instanceof` 用来测试一个对象在其原型链中是否存在一个构造函数的 prototype 属性
    * instanceof只能用于对象，不适用原始类型值。
    
* `Object.prototype.toString`
    实例对象可能会自定义toString方法，覆盖掉Object.prototype.toString方法。通过函数的call方法，可以在任意值上调用Object.prototype.toString方法，帮助我们判断这个值的类型。

    | 类型 | 返回值  |
    |------|--------|
    |  数值：|  [object Number] |
    |   字符串：| [object String] |
    |  布尔值：| [object Boolean] |
    |   undefined：| [object Undefined] |
    |   null：| [object Null] |
    |   数组：| [object Array] |
    |   arguments对象：| [object Arguments] |
    |   函数：| [object Function] |
    |   Error对象：| [object Error] |
    |   Date对象：| [object Date] |
    |   RegExp对象：| [object RegExp] |
    |   其他对象：| [object " + 构造函数的名称 + "] |
    

#### 参考链接
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/typeof
* https://developer.mozilla.org/

zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof
* http://javascript.ruanyifeng.com/grammar/types.html#toc1
* http://javascript.ruanyifeng.com/oop/prototype.html#toc5
* http://javascript.ruanyifeng.com/stdlib/object.html#toc5
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString

### 数组去重

#### 方法
* [indexOf](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) 效率不高，部分浏览器不支持
* hash{} 表
* 先排序再比较相邻元素
* 特殊情况：既有数字又有字符串
* [filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) 部分浏览器不支持


#### 参考链接
* http://www.tuicool.com/articles/jA3iE3i
* http://stackoverflow.com/questions/1960473/unique-values-in-an-array

### 获取一个对象里面第一层元素的数量
#### 方法
* Object.keys() 方法会返回一个由给定对象的所有可枚举自身属性的属性名组成的数组，数组中属性名的排列顺序和使用for-in循环遍历该对象时返回的顺序一致 (顺序一致不包括数字属性)(两者的主要区别是 for-in 还会遍历出一个对象从其原型链上继承到的可枚举属性)。
    * Object.keys() IE9以下浏览器不兼容
* Object.getOwnPropertyNames: 获取一个对象的所有属性,包括不可枚举的。

#### 参考链接
* [Object.keys()-MDN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/keys)
* http://stackoverflow.com/questions/5533192/how-to-get-object-length

### 正则验证手机和邮箱
* 参考w3c的 
``` 
 /^[a-zA-Z0-9.!#$%&’*+/=?^_`{|}~-]+@[a-zA-Z0-9-]+(?:\.[a-zA-Z0-9-]+)*$/ 
```

#### 参考链接
* https://www.w3.org/TR/html-markup/input.email.html#input.email.attrs.value.multiple
* http://emailregex.com/
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/RegExp
