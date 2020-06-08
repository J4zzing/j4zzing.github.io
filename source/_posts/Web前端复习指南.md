---
title: Web前端回忆指南
date: 2020-05-23 00:00:05
tags:
- HTML
- CSS
- JavaScript
---

## HTML

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

role

aria-*

### 浏览器本地支持的懒加载（loading=“lazy”

https://css-tricks.com/native-lazy-loading/



## CSS

### 选择器

伪选择器，伪元素

### 布局

1. 栅格布局（grid-layout

2. 弹性布局（flex-box

复习：https://developer.mozilla.org/zh-CN/docs/Learn/CSS/CSS_layout/Flexbox

测试：https://wiki.developer.mozilla.org/en-US/docs/Learn/CSS/CSS_layout/Flexbox_skills

### 动画



## JavaScript

### 简单介绍

https://developer.mozilla.org/en-US/docs/Web/JavaScript

### 简单复习

https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript

### 数据类型与数据结构

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures

### 表达式和操作符

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Logical

### 控制流

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break

### Javascript特点或quirks

#### Global Object - 全局对象

https://developer.mozilla.org/en-US/docs/Glossary/Global_object

#### Hoisting - 提升

https://developer.mozilla.org/en-US/docs/Glossary/Hoisting

#### 闭包，setTimeout, setInterval：

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures

https://www.typescriptlang.org/docs/handbook/variable-declarations.html#variable-capturing-quirks

更多参见[javascript事件循环](#JS事件循环)

#### Strict mode - 严格模式

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode

#### DOM

https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction

#### this



### RegExp

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp



```
let boundFunc = func.bind(thisArg[, arg1[, arg2[, ...argN]]])
```



### [数组](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

数组字面量

```
Array.from(arrayLike [, mapFn [, thisArg]])
```

Array.prototype.pop()

Array.prototype.slice()

```
arr.filter(callback(element[, index, [array]])[, thisArg])
```

Array.prototype.sort()

Array.prototype.forEach()

Array.prototype.map()

```
arr.reduce(callback( accumulator, currentValue[, index[, array]] )[, initialValue])
```

```
arr.some(callback(element[, index[, array]])[, thisArg])
```

### 函数

#### function declaration, funtion expression and IIFE(Immediately invoked function expression)

https://developer.mozilla.org/en-US/docs/Glossary/Function

什么时候适合使用它们？

https://medium.com/@vvkchandra/essential-javascript-mastering-immediately-invoked-function-expressions-67791338ddc6

#### 箭头函数



### 对象

https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects

#### 创建对象

new Object() , Object.create()和 对象字面量（Object initializer/Object literal

#### getter & setter

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set

#### 继承与原型链

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain

#### 熟悉以下方法

```javascript
Object.defineProperty(obj, prop, descriptor)
```

### 可迭代对象

for...in vs. for...of

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of





### JS事件循环

EventTarget.addEventListener

EventTarget.removeEventListener

EventTarget.dispatchEvent

https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop

https://developer.mozilla.org/en-US/docs/Web/API/Event

https://developer.mozilla.org/en-US/docs/Web/Events



### ECMAScript 2015/ES6 特性

#### 模组化：CommonJS和ES6 import

require() and module.exports

import and export 

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import

#### 模板字面量(Template literals/Template strings)

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals

#### 解构赋值；Spread syntax vs. (Rest parameter vs. argument object) 

[数组和对象解构赋值](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

对象解构赋值 对比 Object.assign()

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments

#### 类

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions

#### 回调，Promise

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise

#### Map & Set



#### Symbol

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol

#### 迭代器和生成器

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators





### ECMAScript 2016/ES7 特性

### async/await



https://nodejs.dev/learn/modern-asynchronous-javascript-with-async-and-await





### Canvas API

https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API

### XHR(XML HTTP request)

js XMLHttpRequest对象

jquery ajax

Fetch API: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API

Axios

### 非标准（因浏览器不同而实现不同）

https://developer.mozilla.org/en-US/docs/Web/API/Console

https://developer.mozilla.org/en-US/docs/Web/API/Console/log

### Performance polyfills



### Web worker

### IndexedDB

### AWS





## 设计模式 - Design Pattern

### 响应式设计(Responsive Design)

```html
<meta >
```

meadia query (@media

### ReSTful

Best practice:

https://florimond.dev/blog/articles/2018/08/restful-api-design-13-best-practices-to-make-your-users-happy/



代码规范：

https://en.wikipedia.org/wiki/Principle_of_least_privilege



## 出色的类库

#### jQuery

### lodash

https://css-tricks.com/debouncing-throttling-explained-examples/

https://levelup.gitconnected.com/omit-is-being-removed-in-lodash-5-c1db1de61eaf

axios

Medium Zoom

https://medium-zoom.francoischalifour.com/#

##### Velocity.js

## React





## TypeScript

### Interface



https://stackoverflow.com/questions/52534910/difference-between-import-x-requirex-and-const-x-requirex-in-typ



### 工具

npm，webpack，babel历史、用途与解释：

https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70



## 不了解

Redux

Flux

Gatsby 

GraphQL



Ant Design

