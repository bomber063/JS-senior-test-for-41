### 用过 Promise 吗？举例说明。
* 用过Promise，比如 jQuery 或者 axios 的 AJAX 功能，都返回的是 Promise 对象。
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
* Promise有一个函数作为参数，这个里面的函数有两个函数作为参数。第一个是成功调用的函数resolve，第二个是是白泽调用的函数reject
```
function asyncMethod(){
    return new Promise(function (resolve, reject){
        setTimeout(function(){
            成功则调用 resolve
            失败则调用 reject
        },2000)
    })
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

### 其他
* [axios的阮一峰说明链接](http://www.ruanyifeng.com/blog/2018/08/weekly-issue-20.html)