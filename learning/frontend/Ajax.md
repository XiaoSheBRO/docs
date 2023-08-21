# Ajax

## Http (_Hyper Text Transfer Protocol 超文本传输协议_)

基于 TCP/IP 通信协议来传递数据

### HTTPS (_HyperText Transfer Protocol Secure 超文本传输安全协议_)

经由 HTTP 进行通信，利用 SSL/TLS 来加密数据包  
供对网站服务器的身份认证，保护交换资料的隐私与完整性  
HTTP 默认使用端口 80，而 HTTPS 默认使用端口 443

### http 请求

其中 HTTP 1.0 定义了三种请求方法： `GET`, `POST` 和 `HEAD` 方法。
HTTP 1.1 新增了五种请求方法：`OPTIONS`, `PUT`, `DELETE`, `TRACE` 和 `CONNECT` 方法。

- get
- post
- put
- delete

http 请求本身不会进行操作，具体操作由后端服务器实现与响应，请求方法名只是约定

> http 请求的异同 ？

### http 请求状态码

- 200：请求成功
- 301：资源被永久转移到其它 URL
- 404：请求的资源（网页等）不存在
- 500：内部服务器错误

## ajax

按需加载数据，异步数据，数据格式通常为 json(_js 对象表示法_)

### readyState

- 0 : 请求未初始化
- 1 ：服务器链接已建立
- 2 ：请求已接受
- 3 ：请求处理中
- 4 ：请求已完成，响应已就绪

## axios

封装 ajax

```js
axios.get('url').then((res) => {
  console.log(res.data)
})

axios.post('url', { params }).then((res) => {
  console.log(res.data)
})
```

## 跨域

> 同源请求：相同 IP、端口；默认无法使用 ajax

### jsonp 原理

利用 `<script>` 标签跨域引入 js 文件
并不是 ajax，实质是 get 请求

> koa (第三方封装)
>
> 后端：引入 jsonp
> 前端：jquery 设置 `dataType:"jsonp"`

### **设置响应头**

后端：设置服务器响应头信息 `ctx.set('Access-Control-Allow-Origin', 'url')` (_url 为`_`则允许所有\_)  
由于存在安全问题，一般开发环境(前后端分离)设置，部署生产环境则不跨域

```js
let xhr = new XMLHttpRequest()
xhr.open('post', '/url') //请求类型;路径
xhr.send()
xhr.onreadystatechange = function () {
  // 监听onreadystatechange事件变化
  if (xhr.readyState === 4 && xhr.state == 200) {
    alert(xhr.responseText)
  }
}

// 封装ajax方法
function myAjax1(method, url, next) {
  let xhr = new XMLHttpRequest()
  xhr.open(method, url) //请求类型;路径
  xhr.send()
  xhr.onreadystatechange = function () {
    // 监听onreadystatechange事件变化
    if (xhr.readyState === 4 && xhr.state == 200) {
      // 异步获取结果
      next(xhr.responseText) // 回调函数方式，不能大量使用，很难维护，不建议使用
    }
  }
}
// 回调一个promise
function myAjax2(method, url) {
  return new Promise(function (resolve) {
    let xhr = new XMLHttpRequest()
    xhr.open(method, url) //请求类型;路径
    xhr.send()
    xhr.onreadystatechange = function () {
      // 监听onreadystatechange事件变化
      if (xhr.readyState === 4 && xhr.state == 200) {
        // 异步获取结果
        resolve(xhr.responseText)
      }
    }
  })
}

myAjax2('get', '/data').then(alert(res))
```
