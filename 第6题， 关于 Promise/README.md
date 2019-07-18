### 用过 Promise 吗？举例说明。
* 一般AJAX都会返回一个Promise对象。
* 在用jQuery发AJAX请求的时候就会用到Promise.成功就会把then函数里面的第一个参数作为回调函数，失败就会把then函数里面的第二个参数作为回调函数
### 如果要你创建一个返回 Promise 对象的函数，你会怎么写？举例说明。
* 因为then方法就会返回一个Promise对象，所以只需要一个函数的return里面有then方法，并且return里面then方法返回的函数里面还有then方法。
```
 window.Promise = function(fn){//接受一个fn作为参数
    ...
   return {
     then: function(){}//这个then里面的函数会继续返回有then方法的对象
   }
 }
```