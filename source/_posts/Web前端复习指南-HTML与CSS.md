---
title: Web前端复习指南 - HTML与CSS
date: 2020-05-23 00:00:05
tags:
- HTML
- CSS
---

## HTML

### 元素

https://developer.mozilla.org/en-US/docs/Web/HTML/Element

### 全局属性

https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes

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



**tabindex**

tabindex="0"

tabindex="-1"

https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex

role

aria-*

### 浏览器本地支持的懒加载（loading=“lazy”

https://css-tricks.com/native-lazy-loading/

### 与XHTML的区别

https://en.wikipedia.org/wiki/XHTML#Relationship_to_HTML

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

定位：

https://developer.mozilla.org/en-US/docs/Web/CSS/position

cotent

https://developer.mozilla.org/en-US/docs/Web/CSS/content

字体

阴影

https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Background_and_Borders/Box-shadow_generator

使用阴影改变select option：

https://stackoverflow.com/questions/10484053/change-select-list-option-background-colour-on-hover



https://developer.mozilla.org/en-US/docs/Web/CSS/pointer-events

### 数据类型与自动转换

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Types

**length**

https://developer.mozilla.org/en-US/docs/Web/CSS/length

### 布局

**网格布局（grid-layout**

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout/Basic_Concepts_of_Grid_Layout

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout

**弹性布局（flex-box**

复习：https://developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox

测试：https://wiki.developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox_skills

**其他古老的布局：流式布局，表格布局**

布局手册：

https://developer.mozilla.org/en-US/docs/Web/CSS/Layout_cookbook

### 动画

```css
transition: <property> <duration> <timing-function> <delay>;
```

https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Transitions/Using_CSS_transitions

https://easings.net/

### 变量 --*

```css
/* 声明全局变量 */
:root {
  --primary-color: lightblue;
  --secondary-color: orange;
}
div {
  color: var(--primary-color);
}
```

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

