---
title: 函数声明，函数表达式和IIFE
tags:
---

# 函数声明，函数表达式和IIFE

参考：https://developer.mozilla.org/en-US/docs/Glossary/Function

首先回顾一下创建函数的两种方式

函数声明：

```javascript
function ex1() {
  //
}
```

函数表达式：

```javascript
var ex2 = function () {
  //
}
```

函数还可以分为匿名函数和命名函数，只有函数表达式才能匿名。





## IIFE（Immediately invoked function expression)

IIFE即“立刻执行函数表达式”，该函数在被编译器加载后会立刻执行。

经典的方法有两种方式：

```javascript
(function foo() {
    //
})()
```



```javascript
(function bar() {
    //
}())
```

乍一看可能没看到有什么区别，第一种把括号放到了最后

另一种方法：

```javascript
!function () {
    //
}()

+function() {
    //
}
```

无论哪种方法，都是为了让编译器认为这是一个函数