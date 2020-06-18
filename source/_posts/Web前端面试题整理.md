---
title: Web前端面试题整理
date: 2020-06-18 20:08:18
tags:
- Web前端
---

## 数据类型

### null的数据类型是对象吗

不是，null是JS七种原始数据类型之一。之所以`typeof null === "object"`是因为JS把所有二进制开头为000的数据都当成object类型，而null的二进制全是0。

~~而这个bug到现在还没修复。~~

https://stackoverflow.com/questions/801032/why-is-null-an-object-and-whats-the-difference-between-null-and-undefined



## polyfills

https://en.wikipedia.org/wiki/Polyfill_(programming)