---
title: JAVA后端开发学习路线
date: 2020-05-05 13:31:13
tags:
---

通过原理理解底层，通过项目学习技术。

## 总纲

这篇文章适用于：**我自己**

首先搭建一个技术博客，用来总结经验。可以写在简历上，是学习能力的一种证明。

### 顺序

从练习项目出发，遇到不懂的再专门学习

随缘学习，先求广度，再求深度。兴趣驱动，想学哪个，就学哪个，遇到有前置条件的，回头学前置条件。

Github上的方向概览

JavaGuide

#### 我个人的学习顺序

=>代表需要

-->代表可选

1. 独立完成一个项目=>(Spring，Mybatis，MySql)=>Java I/O,Java Annotations
2. 分布式

### 额外资料

[Backend Developer](https://roadmap.sh/backend)

#### 书籍

[JAVA相关书籍](https://search.douban.com/book/subject_search?search_text=java&cat=1001)



## JAVA8语言特性

[参考教程：Java Tutorials Learning Paths](https://docs.oracle.com/javase/tutorial/tutorialLearningPaths.html)

《Thinking in Java》

《Effective Java》

《On Java 8》

### 数据类型

[Java Integer Cache: Why Integer.valueOf(127) == Integer.valueOf(127) Is True](https://dzone.com/articles/java-integer-cache-why-integervalueof127-integerva)

#### 包

[Naming a Package](https://docs.oracle.com/javase/tutorial/java/package/namingpkgs.html)

#### 术语

这些术语你应该会在学习途中遇到

Java Language Specification(JLS)：

Plain old Java object(POJO)：普通Java对象，除了JSL不受其他框架或模型限制。

[Java Beans](https://www.geeksforgeeks.org/pojo-vs-java-beans/)：是可序列化的、具有无参构造函数的、字段均为私有且拥有对应的getter和setter方法的POJO。

Enterprise Java Beans(EJB)：

### [抽象类和接口](https://cyc2018.github.io/CS-Notes/#/notes/Java%20%E5%9F%BA%E7%A1%80?id=%e6%8a%bd%e8%b1%a1%e7%b1%bb%e4%b8%8e%e6%8e%a5%e5%8f%a3)

#### 什么时候使用

两者都是用来描述概念的工具，如形状Shape、食物Food等，现实中找不到对应的物体，只存在于我们脑中，这也是为什么他们无法用来创建对象。

#### 区别

抽象类是描述整体，接口是描述部分。所以，一个类只能继承一个抽象类，但是却能实现多个接口。

接口的成员只能是public，接口的字段只能是final与static。为什么？

#### 问题与解答

[What does “ List<Integer> list = new ArrayList<>();” actually mean?](https://stackoverflow.com/questions/43462404/what-does-listinteger-list-new-arraylistinteger-actually-mean)

### [泛型](https://cyc2018.github.io/CS-Notes/#/notes/Java%20%E5%9F%BA%E7%A1%80?id=%e4%b9%9d%e3%80%81%e6%b3%9b%e5%9e%8b)

### 容器

#### 序列化

#### 异常

[Java Exception介绍](https://www.geeksforgeeks.org/exceptions-in-java/)

#### I/O

#### 并发

#### 网络编程

使用ServerSocket编写一个web服务器
，NIO，AIO

#### JVM虚拟机



## 理论知识

### 算法与数据结构

1.剑指Offer

2.Github辅助刷题

3.历年真题

### 操作系统

[《深入理解计算机系统》](https://book.douban.com/subject/26912767/)

6.828

### 计算机网络

《自顶向下》

### Linux底层



## 项目经验

找开源项目看或模仿

要求：项目尽量新，使用技术尽量广泛

### 需要涉及技术

框架：Spring，Spring Boot，Mybatis，Hibernate

数据库：MySQL，Redis，

#### 构建

介绍：

[构建工具的进化：ant, maven, gradle](https://zhuanlan.zhihu.com/p/24429133)

[学习Maven](http://maven.apache.org/guides/getting-started/index.html)

学习gradle

CI

TravisCI

#### 部署：Docker

#### Web服务器：Tomcat，Nginx

#### 设计模式：Restful API，MVC

#### 其他：Linux基础，Git，

## 面试经验

查缺补漏或寻找方向

https://www.jianshu.com/p/745757d373e9



## 实习经验

简历，熟悉流程