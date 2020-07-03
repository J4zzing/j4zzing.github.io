---
title: Web前端面试题整理-网络
date: 2020-06-19 17:35:28
tags: 
- 前端
---

## 在浏览器输入URL后发生了什么

1. DNS域名解析
2. 建立TCP连接；
3. 发送HTTP请求
4. 服务器处理请求
5. 返回响应结果
6. 关闭TCP连接
7. 浏览器解析HTML
8. 浏览器布局渲染

## 浏览器渲染过程

## CSRF和XSS是什么以及如何预防

什么是同源：协议(protocol)，主机(host)与端口(port)一致的URL为同源，参考：https://developer.mozilla.org/en-US/docs/Web/Security/Same-origin_policy

https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie

跨站请求伪造(CSRF)指第三方网站向受攻击的网站发送跨站请求，使浏览器带着Cookie访问目标网站进行

跨站脚本攻击(XSS)指第三方网站利用JS访问受攻击网站Cookie中的敏感信息。

**减轻CSRF**可以通过首部Set-Cookie的Samesite属性，

Samesite有三个可选参数：

- Strict，只有在同源下浏览器才会发送Cookie给服务器
- Lax，现代浏览器默认值，第三方通过子请求(访问图片等)，Cookie不会被发送，但是可以通过网站导航的方式发送
- None，旧浏览器的默认值，任何跨源请求都会同时发送Cookie

也可以通过实现Restful API来预防

**减轻XSS**可以通过设置首部Cookie的Httponly属性，使得Cookie只能被发送到服务器，而无法被document.cookie接口访问。

同时还可以通过设置短暂的Cookie有效期限(`Expires`或`Max-Age`)~~或者用Web_Storage_API取代Cookie~~来预防这两种攻击。

同时也应设置Secure属性还减轻中间人攻击

## HTTP缓存

## HTTP跨源资源共享

https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS

协议，主机与端口一致的URL为同源

## 传输层

### TCP和UDP的区别

