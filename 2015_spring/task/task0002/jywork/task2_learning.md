# 知识点
## JavaScript数据类型及语言基础
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
    |---|
    |  数值：|  [object Number]。|
    |   字符串：| [object String]。|
    |  布尔值：| [object Boolean]。|
    |   undefined：| [object Undefined]。|
    |   null：| [object Null]。|
    |   数组：| [object Array]。|
    |   arguments对象：| [object Arguments]。|
    |   函数：| [object Function]。|
    |   Error对象：| [object Error]。|
    |   Date对象：| [object Date]。|
    |   RegExp对象：| [object RegExp]。|
    |   其他对象：| [object " + 构造函数的名称 + "] |

#### 参考链接
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/typeof
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/instanceof
* http://javascript.ruanyifeng.com/grammar/types.html#toc1
* http://javascript.ruanyifeng.com/oop/prototype.html#toc5
* http://javascript.ruanyifeng.com/stdlib/object.html#toc5
* https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Object/toString

## 数组去重

* 方法
    * [indexOf](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/indexOf) 效率不高，部分浏览器不支持
    * hash{} 表
    * 先排序再比较相邻元素
    * 特殊情况：既有数字又有字符串
    * [filter](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/filter) 部分浏览器不支持


* 参考链接
    * http://www.tuicool.com/articles/jA3iE3i
    * http://stackoverflow.com/questions/1960473/unique-values-in-an-array

## 获取一个对象里面第一层元素的数量
