---
title: TypeScript Tough Points
date: 2020-09-11 10:50:37
tags:
- TypeScript
---

## Decorator

https://www.typescriptlang.org/docs/handbook/decorators.html

装饰器可以用来观察，修改，替换一个类，成员方法，Accessor（getter和setter），成员属性，形参的定义。

装饰器不能用在声明文件或任何其他环境上下文（如在一个declare class内 

Evaluation

> There is a well defined order to how decorators applied to various declarations inside of a class are applied:
>
> 1. *Parameter Decorators*, followed by *Method*, *Accessor*, or *Property Decorators* are applied for each instance member.
> 2. *Parameter Decorators*, followed by *Method*, *Accessor*, or *Property Decorators* are applied for each static member.
> 3. *Parameter Decorators* are applied for the constructor.
> 4. *Class Decorators* are applied for the class.

#### Class Decorators



#### Method Decorators

签名：

```typescript
interface accessorDecorator {
  target: Object;
  propertyKey: string | symbol;
  descriptor: PropertyDescriptor;
}
```

如果有，装饰器的返回值将会成为该成员的*Property Descriptor*

注意：如果编译*target*低于*ES5*，*Property Descriptor*会等于`undefined`

#### Accessor Decorators

> NOTE  TypeScript disallows decorating both the `get` and `set` accessor for a single member. Instead, all decorators for the member must be applied to the first accessor specified in document order. This is because decorators apply to a *Property Descriptor*, which combines both the `get` and `set` accessor, not each declaration separately.

Accessor decorator的签名为：

```typescript
interface accessorDecorator {
  target: Object;
  propertyKey: string | symbol;
  descriptor: PropertyDescriptor;
}
```

如果有，装饰器的返回值将会成为该成员的*Property Descriptor*

注意：如果编译*target*低于*ES5*，*Property Descriptor*会等于`undefined`

#### Property Decorators

签名：

```typescript
interface propertyDecorator {
  target: Object;
  propertyKey: string | symbol;
}
```

> NOTE  A *Property Descriptor* is not provided as an argument to a property decorator due to how property decorators are initialized in TypeScript. This is because there is currently no mechanism to describe an instance property when defining members of a prototype, and no way to observe or modify the initializer for a property. The return value is ignored too. As such, a property decorator can only be used to observe that a property of a specific name has been declared for a class.



#### Parameter Decorators

签名：

```typescript
interface parameterDecorator {
    target: Object;
    propertyKey: string | symbol;
    parameterIndex: number;
}
```

The return value of the parameter decorator is ignored.



### Reference

关于*Property Descriptor*

https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/defineProperty

Playground

https://www.typescriptlang.org/play?target=1#code/FAYwNghgzlAEAKB7AlgOwC6wN7FrAHgFyyoCuAtgEYCmATgNy6wCexZVdjAvsKJDLAAyaatiYAHWsgBuEdKID64gAzEkadIzySZcxeICMalBkZMAArLDIAJnqZRqmFQAorpasY0BKMXjzoABbIUAB0SsqwALyw7tRasDx4AOZOsK6+OP6wtE6ktKiwQSHhKgk8Fla29niOzgZuEGAeXhiZTAHBYUoG0bFNHuVMqfUu7dm56PmFxd2GQxUAZqSoIOjIiIVVdvIAPAAqAHwuTOgQtCPEEKjMADQStIjidOjMANLUrLBQ6FKoyfc8DZqFAQFJxOhELRiPtmM8bPBHs9aK8ACIgsHICFQg6HYDjWBgNJ1PrA0HgyG0UJ1BJkzHYqkkmLLVbrTawRrNTywfYEvBEzCvZ59ABK1EWRLWoRGAFknBAdhAXAAiMnIZKoQhC6jK25Fc4jPWSJ4vd6fbwJPDIRYcgCEnI8sDQP2uIGoiBt2u8fP8QUeAHcSNRA7DngBRWiPWgqgCSqG2RTh1FCyotHUS6bqoRATTALjOFyceriabwXG4QA