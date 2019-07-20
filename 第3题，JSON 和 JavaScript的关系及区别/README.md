### 问题1 JSON 和 JavaScript 是什么关系？
* JSON（JavaScript Object Notation，JavaScript对象表示法，读作“Jason”）是一种轻量级的数据交换语言，尽管JSON是JavaScript的一个子集，但JSON是独立于语言的文本格式。JSON的语法就是JS对象字面量表示法语法的一个子集
* JSON 只抄袭了一部分 JavaScript 语法，而且没有新增任何原创的语法
* JSON 是 JavaScript 对象的字符串表示法，它使用文本表示一个 JavaScript 对象的信息，本质是一个字符串。
### 问题2 JSON 和 JavaScript 的区别有哪些？
1. JSON没有抄袭function和undefined
2. JSON字符串的首尾必须是双引号""
3. 对象的key不支持单引号也不支持不加引号、没有内置的 Date、Math、RegExp 等
4. 表格列出更多各种类型的区别

|JSON|JavaScript|
|:--:|:--:|
|没有|undefined|
|null|null|
|数组["a","b"]|数组['a','b']|
|没有函数|函数function fn(){}|
|对象{"name":"bomber"}|对象{name:'bomber'}|
|字符串"bomber"|字符串'bomber'|
|搞不定，因为JSON没有变量，不能引用|声明一个对象引用自己var a={}<br>a.self=a|
|没有原型链|有原型链|

### 其他
* 字面量可以理解为对象的简单写法，比如用new去创建一个对象
```
var obj=new Object()
```
* 但我们还可以写成创建对象的特殊简写
```
obj={}
```
* {}就是字面量，而new Object()不是字面量
* 字面量学习[链接](https://www.jianshu.com/p/0f2816805da6)
* MDN 关于字面量的说明[链接](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/Spread_syntax)