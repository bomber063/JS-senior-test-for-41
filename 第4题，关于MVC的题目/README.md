### 前端 MVC 是什么？（10分）
* 前端MVC是一种代码的组织形式，组织代码的一种思想，就是代码分成三块
* view(视图相关)，controller(逻辑等其他相关)，model(数据相关)，交互的过程就是
1. 用户点击view。
2. controller监听view
3. view一旦被点击就会通知controller
4. 点击之后controller接到view的通知后就会去调用model。
5. model就会向服务器(server)发起请求
6. 服务器(server)就会返回响应的数据
7. model拿到数据之后就会返回给controller
8. controller拿到数据之后就会去更新view
### 请用代码大概说明 MVC 三个对象分别有哪些重要属性和方法。（10分）
* V——view(视图相关),我们在html中找到的被包括的代码，这个就是view。因为view就是用户能看见的东西，所以平时我们一直在使用MVC中的V，简单来说其实就是html
```
    window.View = function (seletor) {
    return document.querySelector(seletor)//这个seletor一般就是一个选择器
}
```
* **V的方法一般就是为了选择一个DOM元素**，其他地方如果用到View的就简写成比如
```
View(seletor)//seletor是选择器
```
***
***
* M——model(数据相关)，model是你的数据有哪些操作，比如数据操作有初始化数据、获取数据和保存数据等
```
window.Model = function (options) {options是传入的参数
    //return前面可以通过传入的参数赋值一些变量或者属性
    return {
        init: function () {
            ...
        },//初始化数据方法
        fetch: function () {
            ...
        },//获取数据方法
        save: function (name, content) {
            ...
        }//保存数据方法
    }
}
```
* **M的方法一般就是初始化数据，获取数据，保存数据等方法**，其他地方如果用到Model的就简写成比如
```
 var model=Model(x)//x是传入的参数
```

* controller(逻辑等其他相关)，包括
```
window.Controller = function (options) {options就是传入的参数
    //如果有参数传入就在return之前先处理参数
    return {
        //view和model设为null
        view:null,
        model:null,
        init: function (view,model) {
            this.view = view//再通过参数把view传进来
            this.model = model//再通过参数把model传进来
            this.model.init()//model如果要初始化就初始化方法
            ...
        },
        xxx:function(){},
        yyy:function(){}
        ...
    }
}
```
* **C的方法一般就是负责除了M和V外的其他的所有事情的方法(包括前面的v和m参数的传入，整个函数的初始化，绑定事件，对v的操作方法等)**，其他地方如果用到Controller的就简写成比如
```
 Controller({根据函数Controller的要求传入一个参数})
```

### 参考答案补充
* MVC 是什么
1. MVC 是一种设计模式（或者软件架构），把系统分为三层：Model数据、View视图和Controller控制器。
Model 数据管理，包括数据逻辑、数据请求、数据存储等功能。前端 Model 主要负责 AJAX 请求或者 LocalStorage 存储
2. View 负责用户界面，前端 View 主要负责 HTML 渲染。
3. Controller 负责处理 View 的事件，并更新 Model；也负责监听 Model 的变化，并更新 View，Controller 控制其他的所有流程。

* 代码说明
```
var model = {
    data: null,
    init(){}
    fetch(){}
    save(){}
    update(){}
    delete(){}
}
view = {
    init() {}
    template: '<h1>hi</h1'>
}
controller = {
    view: null,
    model: null,
    init(view, model){
        this.view = view
        this.model = model
        this.bindEvents()
    }
    render(){
        this.view.querySelector('name').innerText = this.model.data.name
    },
    bindEvents(){}
}
```
