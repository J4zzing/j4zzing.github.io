---
title: Web前端复习指南HTML和CSS篇
date: 2020-05-23 00:00:05
tags:
- HTML
- CSS
---

## HTML

## 元素

https://developer.mozilla.org/en-US/docs/Web/HTML/Element

### 表单

```html
<form>
  <label for="name">
      
  <label />
  <input type="text" name="name" value="Michael" required />
  <input type="submit" value="submit" />
<form />
```

1. [label](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/label)
2. [input](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input)
3. button



### 可访问性

https://developer.mozilla.org/en-US/docs/Learn/Accessibility/HTML

https://developer.mozilla.org/en-US/docs/Learn/Accessibility/WAI-ARIA_basics

tabindex="0"

tabindex="-1"

role

aria-*

### 浏览器本地支持的懒加载（loading=“lazy”

https://css-tricks.com/native-lazy-loading/



## CSS

### 选择器

伪类

https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes

伪元素

https://developer.mozilla.org/en-US/docs/Glossary/Pseudo-element

https://developer.mozilla.org/en-US/docs/Web/CSS/::before

### 盒子模型

https://developer.mozilla.org/en-US/docs/Web/CSS/margin

### 属性

https://developer.mozilla.org/en-US/docs/Web/CSS/content

字体

阴影

https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow

### 数据类型与自动转换

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Types

6个假值（相对于真值）：false, undefined, null, "", 0, NaN

https://www.sitepoint.com/automatic-type-conversion/

https://www.w3schools.com/js/js_type_conversion.asp

为什么([] == false)为false，比较算法概况：

http://es5.github.io/#x11.9.3

### 布局

1. 网格布局（grid-layout

   https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout

   https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout

2. 弹性布局（flex-box

   复习：https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox

   测试：https://wiki.developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox_skills

布局手册：

https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook

### 动画

```css
transition: <property> <duration> <timing-function> <delay>;
```

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

https://easings.net/

### 变量

[css variables](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)

#### 函数

https://developer.mozilla.org/en-US/docs/Web/CSS/calc

### [At(@)-rules](https://developer.mozilla.org/en-US/docs/Web/CSS/At-rule)

https://developer.mozilla.org/en-US/docs/Web/CSS/@import

https://developer.mozilla.org/en-US/docs/Web/CSS/@media

https://developer.mozilla.org/en-US/docs/Web/CSS/@supports

https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face

### 响应式设计(Responsive Design)

https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Responsive_Design

```html
<meta >
```

1. meadia queries
2. 使用现代化布局(flexbox, grid layout)
3. images

### 最佳实践

[不使用* { margin: 0; padding: 0; }](https://www.google.com/search?q=*+%7B+margin%3A+0%3B+padding%3A+0%3B+%7D&oq=*+%7B+margin%3A+0%3B+padding%3A+0%3B+%7D)

*{ box-sizing: border-box;}

