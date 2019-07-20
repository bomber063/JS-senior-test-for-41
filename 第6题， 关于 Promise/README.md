### 用过 Promise 吗？举例说明。
* 一般AJAX都会返回一个Promise对象。在用jQuery发AJAX请求的时候就会用到Promise.成功就会把then函数里面的第一个参数作为回调函数，失败就会把then函数里面的第二个参数作为回调函数
* 举例，比如
```
$.ajax({
  url: '/xxx',
  method:'get'
})
  .then(success1,error1)//success1代表第一个then前面的代码没有问题的时候执行的函数，error1代表第一个then前面的代码有问题的时候执行的函数
  .then(success2,error2)//success2代表第二个then前面的代码没有问题的时候执行的函数，error2代表第二个then前面的代码有问题的时候执行的函数
```
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
* 详细的Javascript部分代码举例为
```
window.jQuery = function(nodeOrSelector){
  let nodes = {}
  nodes.addClass = function(){}
  nodes.html = function(){}
  return nodes
}
window.$ = window.jQuery

window.jQuery.ajax = function({url, method, body, headers}){
  return new Promise(function(resolve, reject){//如果成功就调用resolve，如果失败就调用reject
    let request = new XMLHttpRequest()
    request.open(method, url) // 配置request
    for(let key in headers) {
      let value = headers[key]
      request.setRequestHeader(key, value)
    }
    request.onreadystatechange = ()=>{
      if(request.readyState === 4){
        if(request.status >= 200 && request.status < 300){
          resolve.call(undefined, request.responseText)
        }else if(request.status >= 400){
          reject.call(undefined, request)
        }
      }
    }
    request.send(body)
  })
}

myButton.addEventListener('click', (e)=>{
  let promise = window.jQuery.ajax({
    url: '/xxx',
    method: 'get',
    headers: {
      'content-type':'application/x-www-form-urlencoded',
      'bomber': '18'
    }
  })

  promise.then(
    (text)=>{console.log(text)},
    (request)=>{console.log(request)}
  )

})
```