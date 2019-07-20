### 在 ES5 中如何用函数模拟一个类？
* 用函数模拟一个类
```
   function Person(name){
       this.name=name
   }
```
* 生成实例的时候用new关键字
```
    var person1=new Person('bomber')
    console.log(person1)
```
* 还可以定义在构造函数的prototype对象之上
```
    Person.prototype.run=function(){
        console.log('run run run')
    }
    console.log(person1.run())//会打出run run run
```

### 其他
* 阮一峰关于[Javascript定义类（class）的三种方法](http://www.ruanyifeng.com/blog/2012/07/three_ways_to_define_a_javascript_class.html)