### 第 2 题
```
function Fn(){
    console.log(this)
}
new Fn()
```
* new Fn() 会执行 Fn，并打印出 this，请问这个 this 有哪些属性？这个 this 的原型有哪些属性？

### 回答见下面
* 这个this有一个__proto__属性
* this的原型的属性包括两个
1. constructor
2. __proto__