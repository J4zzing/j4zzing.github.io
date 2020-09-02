---
title: SVG
date: 2020-08-18 19:09:33
tags:
---

## Everything You Need To Know About SVG

https://css-tricks.com/lodge/svg/01-intro-course/

### 使用SVG

- `<img src='x.svg' />` or `<img src='dataURL' />` 
- CSS background-image property
- Inline SVG `<svg>...</svg>`
- Iframe/object/~~embed~~

### 获得

https://css-tricks.com/lodge/svg/10-getting-svg-stock-photography-sites/



### 实验

https://codepen.io/Rockham/pen/yLOaXEB

### 工具

https://www.freeformatter.com/xml-formatter.html

https://pdfmall.com/xml-to-svg

https://base64.guru/converter/decode/image

https://jakearchibald.github.io/svgomg/





### Data URLs

https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs

#### 语法

```
data:[<mediatype>][;base64],<data>
```

Data URLs是由data:开头的，随后跟上MIME类型、;base64标识与数据组成的。

默认值为text/plain;charset=US-ASCII。

举几个例子🌰：

```
data:,Hello%2C%20World!
```

文本类型，ASCII编码的数据。

```
data:text/plain;base64,SGVsbG8sIFdvcmxkIQ==
```

上面的base64编码版本

```
data:image/png;base64,ln8A2f4MRWX71NIAAAAASUVORK5CYII=
```

PNG类型，base64编码的图片

```
data:image/svg+xml;base64,ln8A2f4MRWX71NIAAAAASUVORK5CYII=
```

SVG类型，base64编码的图片

#### SVG

https://codepen.io/Rockham/pen/yLOaXEB