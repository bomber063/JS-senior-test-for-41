### 第 2 题
```
function Fn(){
    console.log(this)
}
new Fn()
```
* new Fn() 会执行 Fn，并打印出 this，请问这个 this 有哪些属性？这个 this 的原型有哪些属性？

### 回答见下面
* this 自身没有属性（只有一个隐藏的 __proto__ 属性）
* this 的原型是 fn.prototype，只有一个属性 constructor，且 constructor === fn（另外还有一个隐藏属性 `__proto__`，指向 Object.prototype）