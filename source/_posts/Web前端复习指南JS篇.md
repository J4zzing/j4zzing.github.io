---
title: Web前端复习指南JS篇
date: 2020-06-18 20:56:50
tags:
- JavaScript
---

**施工中。。。本文目前只适用于个人**

### 简单介绍

https://developer.mozilla.org/en-US/docs/Web/JavaScript

### 简单复习

https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript

### 数据类型与数据结构

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures

7个原始数据类型

- number
- string
- boolean
- undefined
- null
- Symbol
- bigint

引用数据类型

- Wrapper Object
- 

### 表达式和操作符

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Logical

### 控制流

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/break

### Javascript特点或quirks

**Global Object - 全局对象**

https://developer.mozilla.org/en-US/docs/Glossary/Global_object

全局对象通常指window

**Hoisting - 提升**

https://developer.mozilla.org/en-US/docs/Glossary/Hoisting

只有变量和函数声明会提升，类声明则不会提升

提升的真正原因是在程序被执行前声明首先被JS保存到内存中了。

**闭包**

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures

https://www.typescriptlang.org/docs/handbook/variable-declarations.html#variable-capturing-quirks

**Strict mode - 严格模式**

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode

ESModule默认严格模式

**函数参数个数**

https://stackoverflow.com/questions/6446304/question-on-javascript-function-parameters

调用函数时，实参既可以多与形参也可以少于形参，少给的实参值为undefined，多给的实参可以通过函数内置的arguments获取。

**DOM**

https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction

**this**

this会根据调用时的上下文判断。

```javascript

```

ASI - 自动分号插入



### RegExp - 常规表达式

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/RegExp

和其他RegExp不一样的：

- 

### 可迭代对象

[数组](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)

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

### 

for...in vs. for...of

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of

### 函数

所有函数均为Function对象

函数内的arguments对象



#### function declaration, funtion expression and IIFE(Immediately invoked function expression)

https://developer.mozilla.org/en-US/docs/Glossary/Function

什么时候适合使用它们？

https://medium.com/@vvkchandra/essential-javascript-mastering-immediately-invoked-function-expressions-67791338ddc6

还有Function constructor

```
new Function([arg1 [, arg2 [, ...argN]] ,] functionBody)
```

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/Function

#### 箭头函数

特点：

- this指向当前上下文。
- 没有默认的prototype属性（arrow function doesn't have a default prototype property

```
let boundFunc = func.bind(thisArg[, arg1[, arg2[, ...argN]]])
```

### 对象

**JS中都有什么是对象？**

几乎所有JS对象都继承Object

包括Function，Array

JS对象没有所谓的“方法”，只有属性。

https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects



#### 创建对象

创建对象的几种方法：

- Object()构造函数
- Object.create()
- 对象字面量（Object initializer/Object literal

```javascript
function Cat() {
  this.name = "Puss"
}

var cat1 = new Cat() 
cat1.name // "Puss"
// p1继承Person，p1是Person的实例
cat1 instanceof Cat // true

var cat2 = Object.create(Cat) 
cat2.name // "Puss"
cat2 instanceof Cat  // true

var p3 = {name: "Jack"}
```

#### 继承和原型链

> ## [[prototype]]和prototype和__proto__
>
> 请注意！上面标题的第一个prototype外面有两层[]包裹！`[[prototype]] !== prototype`！
> `[[prototype]]`是对象的私有属性，而`prototype`却是只有函数才有的属性！
> **__proto__是JS的非标准但许多浏览器实现的属性，即[[prototype]]**，也就是`someObject.[[Prototype]] === someObject.__proto__`，当然如果你在控制台操作的话会报错，因为浏览器并没有实现`someObject.[[Prototype]]`这样的操作，所以你如果非要验证的话请使用ES6支持的`Object.getPrototypeOf()`方法，即`Object.getPrototypeOf(someObject) === someObject.__proto__`

> It should not be confused with the `*func*.prototype` property of functions, which instead specifies the `[[Prototype]]` to be assigned to all *instances* of objects created by the given function when used as a constructor. The `**Object.prototype**` property represents the [`Object`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object) prototype object.

#### 

```javascript
function Person() {
  this.name = "Jack"
}

var p1 = new Person() 
// p1继承Person，p1是Person的实例
p1 instanceof Person  //true
// 
p1.__proto__ === Person.prototype

var p2 = Object.create(Person)
p2 instanceof Person  //true

var p3 = {name: "Jack"}
// p3直接继承Object
p3.__proto__ === Object.prototype  //true

```

访问一个对象的原型的方法：

- Object.getPrototypeOf()
- Object.setPrototypeOf()
- obj.\__proto__() *（非标准）*

当访问一个对象的属性时，如果在当前的对象找不到属性，JS会根据原型链向上游寻找属性，直到找到它或到达原型链顶层。

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain



#### 熟悉以下方法

```javascript
Object.defineProperty(obj, prop, descriptor)
```



#### getter & setter

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set



### 事件

https://developer.mozilla.org/en-US/docs/Web/API/Event

https://developer.mozilla.org/en-US/docs/Web/Events

Event.target vs. Event.currentTarget

EventTarget.addEventListener

EventTarget.removeEventListener

EventTarget.dispatchEvent

### 事件循环

https://developer.mozilla.org/en-US/docs/Web/JavaScript/EventLoop

Macrotasks and Microtasks

https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API/Microtask_guide

https://jakearchibald.com/2015/tasks-microtasks-queues-and-schedules/

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

Promise构造函数

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise



#### Map & Set



#### Symbol

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol

#### 迭代器和生成器

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators





### ECMAScript 2017特性

#### async/await

https://nodejs.dev/learn/modern-asynchronous-javascript-with-async-and-await

#### [Object.entries()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)



#### Canvas API

https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API



### Ajax

XMLHttpRequest（XHR）

Fetch API: https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API



### 非标准

#### Console

https://developer.mozilla.org/en-US/docs/Web/API/Console

https://developer.mozilla.org/en-US/docs/Web/API/Console/log

#### Babel

property initializers

https://itnext.io/property-initializers-what-why-and-how-to-use-it-5615210474a3



## 设计模式 - Design Pattern

### ReSTful

Best practice:

https://florimond.dev/blog/articles/2018/08/restful-api-design-13-best-practices-to-make-your-users-happy/



代码规范：

https://en.wikipedia.org/wiki/Principle_of_least_privilege

## 自动化构建工具

npm，webpack，babel历史、用途与解释：

https://medium.com/the-node-js-collection/modern-javascript-explained-for-dinosaurs-f695e9747b70



## 框架与库列举

### 工具库

jQuery

lodash

https://css-tricks.com/debouncing-throttling-explained-examples/

https://levelup.gitconnected.com/omit-is-being-removed-in-lodash-5-c1db1de61eaf

Axios

Medium Zoom

https://medium-zoom.francoischalifour.com/#

Velocity.js

### React

Flux

Redux

GraphQL

Relay

Gatsby 

### Angular

### Vue

### Web Component



## More

TypeScript

Interface

https://stackoverflow.com/questions/52534910/difference-between-import-x-requirex-and-const-x-requirex-in-typ

Web Workers

https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers

Cache API

### PWS

service worker

Web worker

IndexedDB

### Hybrid

### WebAssembly