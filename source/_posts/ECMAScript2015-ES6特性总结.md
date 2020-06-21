---
title: ECMAScript2015/ES6特性总结
date: 2020-06-19 23:11:23
tags: 
- JavaScript
---

## JavaScript历史

https://medium.com/@madasamy/javascript-brief-history-and-ecmascript-es6-es7-es8-features-673973394df4

### Proposal

https://tc39.github.io/process-document/

## ECMAScript 2015/ES6 特性

https://babeljs.io/docs/en/learn/

https://ponyfoo.com/articles/es6

#### 模组化：CommonJS和ES6 import

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import

require() and module.exports

import and export 

#### 模板字面量(Template literals/Template strings)

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Template_literals

#### 解构赋值；Spread syntax vs. (Rest parameter vs. argument object) 

[数组和对象解构赋值](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

对象解构赋值 对比 Object.assign()

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/arguments

#### getter & setter

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/get

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/set

#### 简短的定义对象的方法

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Method_definitions

#### 类

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes

类是“特殊的函数”，主要是基于JS原型继承的语法糖。

特点：

- 和函数一样，声明类有两种语法 —— 类声明和类表达式

- 与函数声明不一样，类声明不会被hoisted（提升）
- 类里面的代码永远以strict mode执行，为了提高性能
- 支持功能：构造函数，实例属性，静态属性（在声明类之外定义），方法，静态方法，继承

注意：

- 由于在strict mode中this的指向

实验性功能

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes#Field_declarations

#### 回调，Promise

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise

Promise构造函数

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/Promise

#### Map & Set



#### Symbol

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol

#### BigInt



#### 迭代器和生成器

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Iterators_and_Generators

