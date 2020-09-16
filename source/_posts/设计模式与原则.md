---
title: 设计模式与原则
date: 2020-06-30 22:24:46
tags:
- Design Pattern
- Design Principle
- SOLID
- OOP
- Functional Programming
---

## 通用原则



https://en.wikipedia.org/wiki/Single_source_of_truth



https://en.wikipedia.org/wiki/Separation_of_concerns

模组化

https://en.wikipedia.org/wiki/Modularity_(programming)



https://en.wikipedia.org/wiki/Abstraction_principle_(computer_programming)

DRY vs WET

[DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself)

High cohesion, Low coupling

https://en.wikipedia.org/wiki/Coupling_(computer_programming)



## [Programming Paradigms](https://en.wikipedia.org/wiki/Programming_paradigm)

### Imperative Programming

### [Object-Oriented Programming - OOP](https://en.wikipedia.org/wiki/Object-oriented_programming)

#### [Encapsulation](https://en.wikipedia.org/wiki/Encapsulation_(computer_programming))

https://lostechies.com/derickbailey/2011/03/28/encapsulation-youre-doing-it-wrong/



#### [Inheritance](https://en.wikipedia.org/wiki/Inheritance_(object-oriented_programming))

[Implementation Inheritance Is Evil](https://medium.com/hackernoon/inheritance-based-on-internal-structure-is-evil-7474cc8e64dc)



#### Polymophism

https://en.wikipedia.org/wiki/Polymorphism_(computer_science)

- Ad hoc Polymorphism(function overloading, operator overloading)

> *Ad hoc polymorphism* refer to polymorphic functions that can be applied to arguments of different types, but that behave differently depending on the type of the argument to which they are applied.

- Parametric Polymorphism

> *Parametric polymorphism* allows a function or a data type to be written generically, so that it can handle values *uniformly* without depending on their type.

- Subtyping

> Subtyping allows a function to be written to take an object of a certain type *T*, but also work correctly, if passed an object that belongs to a type *S* that is a subtype of *T* (according to the [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)).

Note: Inheritance should not be confused with subtyping.

More

https://en.wikipedia.org/wiki/Method_dispatch

#### Multiple Inheritance

[The Diamond Problem](https://en.wikipedia.org/wiki/Multiple_inheritance#The_diamond_problem)



#### 原则

#### [Composition over inheritance](https://en.wikipedia.org/wiki/Composition_over_inheritance)

> Classes should achieve [polymorphic](https://en.wikipedia.org/wiki/Polymorphism_(computer_science)) behavior and [code reuse](https://en.wikipedia.org/wiki/Code_reuse) by their [composition](https://en.wikipedia.org/wiki/Object_composition) (by containing instances of other classes that implement the desired functionality) rather than [inheritance](https://en.wikipedia.org/wiki/Inheritance_(computer_science)) from a base or parent class.

#### [SOLID](https://en.wikipedia.org/wiki/SOLID)

- [Single Responsibility Principle](https://en.wikipedia.org/wiki/Single-responsibility_principle)

> The single-responsibility principle (SRP) states that **every module, class or function in a computer program should have responsibility over a single part of that program's functionality**, which it should encapsulate.

https://pasztor.at/blog/clean-code-responsibilities/

[Application of the Single Responsibility Principle (SRP) leads to many small classes.](https://blog.ploeh.dk/2011/06/07/SOLIDCodeisnt)

- [Open-closed Principle](https://en.wikipedia.org/wiki/Open%E2%80%93closed_principle)

> The open–closed principle states "software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification"; that is, such an entity can **allow its behaviour to be extended without modifying its source code**.



- [Liskov substitution principle](https://en.wikipedia.org/wiki/Liskov_substitution_principle)

> Substitutability stating that, **if S is a subtype of T, then objects of type T may be replaced with objects of type S** (i.e. an object of type T may be substituted with any object of a subtype S) without altering any of the desirable properties of the program (correctness, task performed, etc.). 



- [Interface Segregation Principle](https://en.wikipedia.org/wiki/Interface_segregation_principle)

> The interface-segregation principle (ISP) states that **no client should be forced to depend on methods it does not use.** ISP splits interfaces that are very large into smaller and more specific ones so that clients will only have to know about the methods that are of interest to them. ISP is intended to keep a system decoupled and thus easier to refactor, change, and redeploy.Such shrunken interfaces are also called [*role interface*s.](https://martinfowler.com/bliki/RoleInterface.html)



- [Denpendency Inversion Principle](https://en.wikipedia.org/wiki/Dependency_inversion_principle)

> 1. High-level modules should not depend on low-level modules. Both should depend on abstractions (e.g. interfaces).
> 2. Abstractions should not depend on details. Details (concrete implementations) should depend on abstractions.

https://pasztor.at/blog/clean-code-dependencies/

More

https://blog.ploeh.dk/2011/06/07/SOLIDCodeisnt/

#### GRASP

https://en.wikipedia.org/wiki/GRASP_(object-oriented_design)



#### 设计模式

[Factory Pattern](https://en.wikipedia.org/wiki/Factory_(object-oriented_programming))



如何正确的使用class

https://medium.com/javascript-scene/how-to-fix-the-es6-class-keyword-2d42bb3f4caf

https://medium.com/@dan_abramov/how-to-use-classes-and-sleep-at-night-9af8de78ccb4

http://blog.wolksoftware.com/about-classes-inheritance-and-object-oriented-design-in-typescript-and-es6



[IOC](https://en.wikipedia.org/wiki/Inversion_of_control)

> IoC inverts the flow of control as compared to traditional control flow. In IoC, custom-written portions of a computer program receive the flow of control from a generic framework. 

https://pasztor.at/blog/what-is-the-ioc-container/

[Dependency injection](https://en.wikipedia.org/wiki/Dependency_injection)

https://pasztor.at/blog/clean-code-dependencies/

#### 

#### Q&A

Dependency inversion Principle in Dynamic programming languages.

https://softwareengineering.stackexchange.com/questions/195176/how-does-dependency-inversion-principle-work-in-languages-without-interfaces

Dependency injection 和动态语言

https://blog.tonyseek.com/post/notes-about-ioc-and-di/



### Declarative Programming

### Functional Programming - FP

#### [Pure Function](https://en.wikipedia.org/wiki/Pure_function)

> A **pure function** is a [function](https://en.wikipedia.org/wiki/Subroutine) that has the following properties:
>
> 1. Its [return value](https://en.wikipedia.org/wiki/Return_statement) is the same for the same [arguments](https://en.wikipedia.org/wiki/Argument_of_a_function) (no variation with local [static variables](https://en.wikipedia.org/wiki/Static_variable), [non-local variables](https://en.wikipedia.org/wiki/Non-local_variable), mutable [reference arguments](https://en.wikipedia.org/wiki/Value_type_and_reference_type) or input streams from [I/O devices](https://en.wikipedia.org/wiki/Input/output)).
> 2. Its evaluation has no [side effects](https://en.wikipedia.org/wiki/Side_effect_(computer_science)) (no mutation of local static variables, non-local variables, mutable reference arguments or I/O streams).

Thus a pure function is a computational analogue of a mathematical function.

#### [Currying](https://en.wikipedia.org/wiki/Currying)

> Currying is the technique of converting a function that takes multiple arguments into a sequence of functions that each take a single argument. 

[Why Curry Helps](https://hughfdjackson.com/javascript/why-curry-helps/) by Hugh Jackson

[Hey Underscore, You're Doing It Wrong!](https://www.youtube.com/watch?v=m3svKOdZijA&app=desktop) by Brian Lonsdorf

Javascript library - Ramda

- [Introducing Ramda](http://buzzdecafe.github.io/code/2014/05/16/introducing-ramda) by Buzz de Cafe
- [Favoring Curry](http://fr.umio.us/favoring-curry/) by Scott Sauyet
- [Why Ramda?](http://fr.umio.us/why-ramda/) by Scott Sauyet
- [Thinking in Ramda](https://randycoulman.com/blog/categories/thinking-in-ramda) by Randy Coulman

#### [Partial Application](https://en.wikipedia.org/wiki/Partial_application)

> Partial application (or partial function application) refers to the process of fixing a number of arguments to a function, producing another function of smaller arity.





Other Insights

http://wiki.c2.com/?ClosuresAndObjectsAreEquivalent