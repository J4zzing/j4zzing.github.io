---
title: Web前端复习指南 - 网络
date: 2020-06-19 17:35:28
tags: 
- HTTP
- 浏览器
---

## 在浏览器输入URL后发生了什么

https://zhuanlan.zhihu.com/p/43369093

1. DNS域名解析
2. 建立TCP连接
3. 发送HTTP请求
4. 服务器处理请求并响应
6. 关闭TCP连接
7. 浏览器解析HTML
8. 浏览器布局渲染

## 浏览器渲染过程



## HTTP安全 - CSRF和XSS

https://en.wikipedia.org/wiki/Cross-site_scripting

### 是什么

什么是同源：协议(protocol)，主机(host)与端口(port)一致的URL为同源，参考：https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie

跨站请求伪造(CSRF)指第三方网站向受攻击的网站发送跨站请求，使浏览器带着Cookie访问目标网站进行

跨站脚本攻击(XSS)指第三方网站利用JS访问受攻击网站Cookie中的敏感信息。

### 如何预防

**减轻CSRF**可以通过首部Set-Cookie的Samesite属性，

Samesite有三个可选参数：

- Strict，只有在同源下浏览器才会发送Cookie给服务器
- Lax，现代浏览器默认值，第三方通过子请求(访问图片等)，Cookie不会被发送，但是可以通过网站导航的方式发送
- None，旧浏览器的默认值，任何跨源请求都会同时发送Cookie

也可以通过实现Restful API来预防

**减轻XSS**可以通过设置首部Cookie的Httponly属性，使得Cookie只能被发送到服务器，而无法被document.cookie接口访问。

同时还可以通过设置短暂的Cookie有效期限(`Expires`或`Max-Age`)~~或者用Web_Storage_API取代Cookie~~来预防这两种攻击。

同时也应设置Secure属性，只允许Cookie在HTTPS协议中发送，一定程度上减轻中间人攻击。

## HTTP跨源资源共享

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

**同源政策**：https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy

协议，主机与端口一致的URL为同源

[`Access-Control-Allow-Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Origin)

**Preflight request**

https://developer.mozilla.org/en-US/docs/Glossary/Preflight_request

preflight request是使用HTTP OPTIONS请求方法询问服务器是否支持CORS与一些特定方法和首部。

请求时，使用[`Access-Control-Request-Method`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Method), [`Access-Control-Request-Headers`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Request-Headers)和[`Origin`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Origin)首部；如果服务器允许，会响应 [`Access-Control-Allow-Methods`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Allow-Methods)表示允许那些请求方法，

preflight request一般由浏览器自动发起。

## HTTP缓存

Status Code: 200 OK (from memory cache)



https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Controlx

各种首部

[Access-Control-Max-Age](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Access-Control-Max-Age) 

Cache-Control

## HTTP 响应状态码

**101 Switching Protocol**

表示服务器正在按客户端要求切换协议（通过Upgrade首部）。[Protocol upgrade mechanism详情](https://developer.mozilla.org/en-US/docs/Web/HTTP/Protocol_upgrade_mechanism)

Websockets用例

```http
HTTP/1.1 101 Switching Protocols
Upgrade: websocket
Connection: Upgrade
```

#### 成功 - 2xx

**200 OK**

请求成功。

针对不同的请求方式有不同意义：

- GET：取得了资源，放在报文体。
- HEAD：取得了首部，放在报文体。
- POST：处理结果，放在报文体。
- TRACE：请求报文，放在报文体。

**201 Created**

请求成功。在返回响应时，新的资源已经被积极创建并且包含在响应体中。Location首部指示资源URL。

**202 Accepted**

请求被接受，但还未开始或完成处理。202不保证处理的结果，通常表示这个请求被交予其他进程或服务器处理。

#### 重定向 - 3xx

**301 Moved Permanently**

请求的资源被永久移动到了Location首部的URL。浏览器重定向，搜索引擎**会**更新资源的URL。

虽然标准要求重定向时请求方法和请求体不能改变，但并不是所有的UA都遵从，所以推荐仅对GET和HEAD请求响应301。使用308 Permanent Redirect响应POST请求，严格要求不能改变。

**302 Found**

请求的资源被临时移动到了Location首部的URL。浏览器重定向，搜索引擎**不会**更新资源的URL。

虽然标准要求重定向时请求方法和请求体不能改变，但并不是所有的UA都遵从，所以推荐仅对GET和HEAD请求响应302。使用307 Temporary Redirect响应POST请求，严格要求不能改变。

如果你想让请求方法改变为GET，请使用303 See Other。

**303 See Other**

表示重定向到另一个与新创建资源无关的页面，比如确认页面或者处理进度页面。一般只在POST与PUT请求返回303。

#### 客户端错误 - 4xx

[**401 Unauthorized**](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/401)

拒绝请求，因为针对目标资源的权限不足。

同时应响应 [`WWW-Authenticate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/WWW-Authenticate)首部，表明应该如何正确授权。

**403 Forbidden**

明白你的请求，但是拒绝授权。

和401相似，但是这种情况下重新授权也没用，因为这个操作与程序逻辑绑定，永远禁止。

**404 Not Found**

服务器无法找到请求的资源。

#### 服务器错误 - 5xx

**500 Internal Server Error**

服务器遇到了一个未预料的错误导致其无法完成处理请求。

通常用来表示找不到一个更好的5xx状态码来响应。记录到日志来预防同样的事情发生。

**502 Bad Gateway**

服务器（作为网关或代理）从上游接收到了一个无效的响应。

**504 Gateway timeout**

服务器（作为网关或代理）在规定的时间内没有从上游收到响应。

## 传输层

[TCP](https://zh.wikipedia.org/wiki/%E4%BC%A0%E8%BE%93%E6%8E%A7%E5%88%B6%E5%8D%8F%E8%AE%AE)

### TCP和UDP的区别

TCP发送数据前需要先建立连接，UDP则不需要。

包括三次握手与四次挥手

TCP提供差错检测，按序到位，拥塞控制。

UDP则不提供，所以它适用于对数据完整性要求不高的场景，如流媒体。

### TCP三次握手

