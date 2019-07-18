### 问题1 JSON 和 JavaScript 是什么关系？
* JSON（JavaScript Object Notation，JavaScript对象表示法，读作“Jason”）是一种轻量级的数据交换语言，尽管JSON是JavaScript的一个子集，但JSON是独立于语言的文本格式。JSON的语法就是JS对象字面量表示法语法的一个子集
* JSON 是 JavaScript 对象的字符串表示法，它使用文本表示一个 JavaScript 对象的信息，本质是一个字符串。
### 问题2 JSON 和 JavaScript 的区别有哪些？
1. JSON没有抄袭function和undefined
2. JSON字符串的首尾必须是双引号""
3. 表格列出更多各种类型的区别

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