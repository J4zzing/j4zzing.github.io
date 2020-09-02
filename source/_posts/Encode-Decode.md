---
title: Encode & Decode
date: 2020-08-18 19:03:46
tags:
---

### 编码

#### BASE64

使用的字符包括大小写[拉丁字母](https://zh.wikipedia.org/wiki/拉丁字母)各26个、数字10个、加号`+`和斜杠`/`，共**64**个字符，等号`=`用来作为后缀用途。https://zh.wikipedia.org/wiki/Base64

#### ASCII

https://zh.wikipedia.org/wiki/ASCII

至今为止共定义了**128**个字符

#### Latin1

https://zh.wikipedia.org/wiki/ISO/IEC_8859-1

> **ISO 8859-1**，正式编号为**ISO/IEC 8859-1:1998**，又称**Latin-1**或“[西欧](https://zh.wikipedia.org/wiki/西欧)语言”，是[国际标准化组织](https://zh.wikipedia.org/wiki/國際標準化組織)内[ISO/IEC 8859](https://zh.wikipedia.org/wiki/ISO/IEC_8859)的第一个8位[字符集](https://zh.wikipedia.org/wiki/字符集)。它以[ASCII](https://zh.wikipedia.org/wiki/ASCII)为基础，在空置的0xA0-0xFF的范围内，加入96个[字母](https://zh.wikipedia.org/wiki/字母)及[符号](https://zh.wikipedia.org/wiki/符号)，藉以供使用[附加符号](https://zh.wikipedia.org/wiki/附加符号)的[拉丁字母](https://zh.wikipedia.org/wiki/拉丁字母)语言使用。

**256**个字符

#### Unicode

https://zh.wikipedia.org/wiki/Unicode

### 关系

Latin1与Unicode的前256位对应



### 编码方式

UTF-8

https://developer.mozilla.org/en-US/docs/Glossary/Base64

https://en.wikipedia.org/wiki/MIME#Content-Transfer-Encoding



#### Javascript APIs

https://www.jianshu.com/p/b2c6dc5fad0a



https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/encodeURIComponent



javascript字符串以UTF-16编码

#### [btoa](https://developer.mozilla.org/en-US/docs/Web/API/WindowOrWorkerGlobalScope/btoa)



btoa接收一个[binary string](https://developer.mozilla.org/en-US/docs/Web/API/DOMString/Binary)类型的参数

所以，

> invoking it on a string that contains codepoints greater than `255` will cause a `Character Out Of Range` error

btoa只能处理一个字节大小的字符，可用以下方法转换：

https://stackoverflow.com/questions/23223718/failed-to-execute-btoa-on-window-the-string-to-be-encoded-contains-characte

