---
title: C++ Primer 重点摘选
tags: C++
---

## Chapter 2 - Variables and Basic Types

### 2.1 Primitive Built-in Types

> C++ defines a set of primitive types that include the **arithmetic types** and a special type named **void**. The arithmetic types represent characters, integers, boolean values, and floating-point numbers. The void type has no associated values and can be used in only a few circumstances, most commonly as the return type for functions that do not return a value.

#### 2.1.1 Arithmetic Types

> The arithmetic types are divided into two categories: **integral types**(which include character and boolean types) and **floating-point types**.

#### 2.1.2 Type Conversions

> The type of an object defines the data that an object might contain and what operations that object can perform. Among the operations that many types support is the ability to convert objects of the given type to other, related types.
>
> Type conversions happen automatically when we use an object of one type where an object of another type is expected.

### 2.2 Variables

#### 2.2.1 Variable Definitions

> C++ programmers tend to be cavalier in their use of the term object. Most generally, an object is a region of memory that can contain data and has a type.

1. int number = 1;
2. int number = {1};
3. int number{1};
4. int number(1);

> The compiler will not let us list initialize variables of built-in type if the initializer might lead to the loss of information.

> Initialization in C++ is a surprisingly complicated topic and one we will return
> to again and again. Many programmers are confused by the use of the = symbol to
> initialize a variable. It is tempting to think of initialization as a form of assignment,
> but initialization and assignment are different operations in C++. This concept
> is particularly confusing because in many languages the distinction is irrelevant
> and can be ignored. Moreover, even in C++ the distinction often doesn’t matter.

> ⚠ Initialization is not assignment. Initialization happens when a variable
> is given a value when it is created. Assignment obliterates an object’s
> current value and replaces that value with a new one.

> The value of an object of built-in type that is not explicitly initialized depends
> on where it is defined. Variables defined outside any function body are initialized
> to zero. With one exception, which we cover in § 6.1.1 (p. 205), variables of built-in
> type defined inside a function areuninitialized. The valueof an uninitialized vari-
> able of built-in type is undefined (§ 2.1.2, p. 36). It is an error to copy or otherwise
> try to access the value of a variable whose value is undefined.

> Uninitialized objects of built-in type defined inside a function body
> have undefined value. Objects of class type that we do not explicitly
> initialize have a value that is defined by the class.

使用内置类型时最好先初始化。

#### 2.2.2 作用域 - Scope

> Once a name has been declared in a scope, that name can be used by scopes
> nested inside that scope. Names declared in the outer scope can also be **redefined**
> in an inner scope.

> ⚠ It is almost always a bad idea to define a local variable with the same
> name as a global variable that the function uses or might use.

### 2.3 复合类型 - Compound types

#### 2.3.1 引用 - References

A Reference Is an Alias.

A reference must be initialized.

Reference is not object.

References cannot be rebind.

#### 2.3.2 指针 - Pointers

> The most direct approach is to initialize the pointer using the literal nullptr,
> which was introduced by the new standard. nullptr is a literal that has a special
> type that can be converted

> The value (i.e., the address) stored in a pointer can be in one of four states:
> 1. It can point to an object.
> 2. It can point to the location just immediately past the end of an object.
> 3. It can be a null pointer, indicating that it is not bound to any object.
> 4. It can be invalid; values other than the preceding three are invalid.

> It can be easier to understand complicated pointer or reference declarations if you read them from right to left.

### 2.4 const Qulifier

#### 2.4.1 References to const

> we can bind a reference to const to a nonconst object, a literal, or a more general expression. p.61

#### 2.4.2 Pointers and const

Pointers to const

> It may be helpful to think of pointers and references to const as pointers or references ”that think they point or refer to const.”

const Pointers

#### 2.4.3 Top-Level const

> The distinction between top-level and low-level matters when we copy an object. When we copy an object, top-level consts are ignored. On the other hand, low-level const is never ignored.

#### 2.4.4 `constexpr` and Constant Expressions

> A constant expression is an expression whose value cannot change and that can be evaluated at compile time. A literal is a constant expression. A `const` object that is initialized from a constant expression is also a constant expression. 

> In a large system, it can be difficult to determine (for certain) that an initializer is a
> constant expression. 
>
> Under the new standard, we can ask the compiler to verify that a variable is a constant expression by declaring the variable in a `constexpr` declaration. Variables declared as constexpr are implicitly const and must be initialized by constant expressions. *<C++11>*

### 2.5 Dealing with types

#### 2.5.1 Type Aliases



#### 2.5.2 The `auto` Type Specifier *<C++11>*

> By implication, a variable that uses auto as its type specifier must have an initializer.

>  Auto ordinarily ignores top-level consts.

#### 2.5.3 The `decltype` Type Specifier *<C++11>*

> Sometimes we want to define a variable with a type that the compiler deduces
> from an expression but do not want to use that expression to initialize the variable.

> `decltype` returns a reference type for expressions that yield objects that can stand on the left-hand side of the assignment.

> `decltype` of a parenthesized variable is always a reference.

### 2.6 Define Our Own Data Structures

> Ordinarily,it is a bad idea to define an object as part of a class definition. Doing so obscures the code by combining the definitions of two different entities—the class and a
> variable—in a single statement.

> Under the new standard, we can supply an in-class initializer for a data mem-
> ber. When we create objects, the in-class initializers will be used to initialize the
> datamembers. Memberswithout aninitializeraredefaultinitialized. <C++11>

#### 2.6.3 Writing Our Own Header Files

> Headers (usually) contain entities (such as class definitions and const and
> constexpr variables) that can be defined only once in any given file.

> Preprocessor variables, including names of header guards, must be unique throughout the program. Typically we ensure uniqueness by basing the guard’s name on the name of a class in the header. To avoid name clashes with other entities in our programs, preprocessor variables usually are written in all uppercase.

> Headers should have guards, even if they aren’t (yet) included by another header. Header guards are trivial to write, and by habitually defining them you don’t need to decide whether they are needed.

## Chapter 3 - Strings, Vectors and Arrays

> A string is a variable-length sequence of characters. A vector holds a variable-length sequence of objects of a given type

### 3.1 Namespace `using` Declarations

> Headers Should Not Include using Declarations.

### 3.2 Library `string` Type

#### 3.2.1 Defining and Initializing `string`s

copy initializing and direct initializing

#### 3.2.2 Operations on `string`s

> This `getline` function reads the given stream up to and including the first newline and stores what it read—not including the newline—in its string argument.

> Although we don’t know the precise type of string::size_type, we do know that it is an **unsigned** type big enough to hold the size of any string. Any variable used to store the result from the string size operation should be of type string::size_type.

> ⚠ For historical reasons, and for compatibility with C, string literals are not standard library strings. It is important to remember that these types differ when you use string literals and library strings.

#### 3.2.3 Dealing with the Characters in a `string`

> Ordinarily, C++ programs should use the *cname* versions of headers and not the *name.h* versions.

### 3.3 Library `vector` Type

> A vector is often referred to as a container because it “contains” other objects.

> Templates are not themselves functions or classes. Instead, they can be thought of as instructions to the compiler for generating classes or functions. The process that the compiler uses to create classes or functions from templates is called **instantiation**. When we use a template, we specify what kind of class or function we want the compiler to instantiate.

> It is worth noting that earlier versions of C++ used a slightly different syntax
> to define a vector whose elements are themselves vectors (or another template
> type). In the past, we had to supply a space between the closing angle bracket
> of the outer vector and its element type—vector<vector<int> > rather than
> vector<vector<int>>.

#### 3.3.1 Defining and Initializing `vector`s

> when we use the copy initialization form (i.e., when we use =), we can supply only a single initializer; and when we supply an in-class initializer, we must either use copy initialization  or use curly braces.

> If we use braces and there is no way to use the initializers to list initialize the object, then those values will be used to construct the object.

#### 3.3.2 Adding Elements to a `vector`

> The standard requires that vector implementations can efficiently add elements at run time. Because vectors grow efficiently, it is often unnecessary—and can result in poorer performance—to define a vector of a specific size. The exception to this rule is if all the elements actually need the same value. 

> ⚠ We cannot use a range `for` if the body of the loop adds elements to the vector.
>
> ⚠ The body of a range for must not change the size of the sequence over which it is iterating.

#### 3.3.3 Other `vector` Operations

> It is an error to subscript an element that doesn’t exist, but it is an error that the compiler is unlikely to detect. So-called buffer overflow errors are the result of subscripting elements that don’t exist. Such bugs are the most common cause of security problems in  PC and other applications.
>
> A good way to ensure that subscripts are in range is to avoid subscripting altogether by using a range `for` whenever possible.

### 3.4 Introducing Iterators

> All of the library containers have iterators, but only a few of them support the subscript operator.

#### 3.4.1 Using Iterators

> The iterator returned by `end` is an iterator positioned “one past the end” of the associated container (or string). This iterator denotes a nonexistent element “off the end”of the container. It is used as a marker indicating when we have processed all the elements. The iterator returned by end is often referred to as the **off-the-end iterator** or abbreviated as “the end iterator.”

|                | Standard Container Iterator Operations |
| -------------- | -------------------------------------- |
| *iter          |                                        |
| iter->mem      | Equivalent to ( * iter).mem.           |
| ++iter         |                                        |
| --iter         |                                        |
| iter1 == iter2 |                                        |

> KEY CONCEPT : GENERIC PROGRAMMING
> Programmers coming to C++ from C or Java might be surprised that we used != rather
> than < in our for loops such as the one above and in the one on page94. C++ programmers use != as a matter of habit. They do so for the same reason that they use iterators
> rather than subscripts: This coding style applies equally well to various kinds of containers provided by the library.
> As we’ve seen, only a few library types, vector and string being among them,have the subscript operator. Similarly, all of the library containers have iterators that define the == and != operators. Most of those iterators do not have the < operator.
> By routinely using iterators and !=, we don’t have to worry about the precise type of
> container we’re processing.

> To let us ask specifically for the `const_iterator` type, the new standard introduced two new functions named `cbegin` and `cend`.

#### 3.4.2 Iterator Arithmetic

> |               | Operations Supported by vector and string Iterators |
> | ------------- | --------------------------------------------------- |
> | iter + n      |                                                     |
> | iter - n      |                                                     |
> | iter += n     |                                                     |
> | iter -= n     |                                                     |
> | iter1 - iter2 |                                                     |
> | >,>=,<,<=     |                                                     |

### 3.5 Arrays

> An array is a data structure that is similar to the library `vector` type but offers a different trade-off between performance and flexibility.

#### 3.5.1 Defining and Initializing Built-in Arrays

> Arrays are a compound type. An array declarator has the form `a[d]`, where `a` is the name being defined and `d` is the dimension of the array.
>
> The number of elements in an array is part of the array’s type. As a result, the dimension must be known at compile time, which means that the dimension must be a constant
> expression.
>
> By default, the elements in an array are default initialized.

> ⚠ As with variables of built-in type, a default-initialized array of built-in type that is defined inside a function will have undefined values.

> We can initialize such arrays from a string literal. When we use this form of initialization, it is important to remember that string literals end with a null character. That null character is copied into the array along with the characters in the literal.

> We cannot initialize an array as a copy of another array, nor is it legal to assign one array to another.

> It can be easier to understand array declarations by starting with the array’s name and reading them from the inside out.

#### 3.5.2 Accessing the Elements of an Array

> ⚠ The most common source of security problems are buffer overflow bugs. Such bugs occur when a program fails to check a subscript and mistakenly uses memory outside the range of an array or similar data structure.

#### 3.5.3 Pointers and Arrays

> In C++ pointers and arrays are closely intertwined. In particular, as we’ll see, when we use an array, the compiler ordinarily converts the array to a pointer.
>
> In most places when we use an array, the compiler automatically substitutes a pointer to the first element.

> Just as we can use iterators to traverse the elements in a vector, we can use pointers to traverse the elements in an array. Of course, to do so, we need to obtain pointers to the first and one past the last element.

> To make it easier and safer to use pointers, the new library includes two functions, named
> begin and end.

> The result of subtracting two pointers is a library type named `ptrdiff_t`. Like
> `size_t`, the `ptrdiff_t` type is a machine-specific type and is defined in the
> `cstddef` header. Because subtraction might yield a negative distance, `ptrdiff_t` is a signed integral type.

> We can use the subscript operator on any pointer, as long as that pointer points to an element (or one past the last element) in an array.

> The index used with the built-in subscript operator can be a negative value. 
>
> ⚠ Unlike subscripts for vector and string, the index of the built-in subscript operator is not an unsigned type.

#### 3.5.4 C-Style Character Strings

> ⚠ Although C++ supports C-style strings, they should not be used by C++ programs. C-style strings are a surprisingly rich source of bugs and are the root cause of many security problems. They’re also harder to use!

#### 3.5.5 Interfacing to Older Code

> More generally, we can use a null-terminated character array anywhere that we can use a string literal.

> If a program needs continuing access to the contents of the array returned by `c_str`(), the program must copy the array returned by `c_str`.

> Modern C++ programs should use `vector`s and iterators instead of built-in arrays and pointers, and use strings rather than C-style array-based character strings.

### 3.6 Multidimensional Array

> Strictly speaking, there are no multidimensional arrays in C++. What are commonly referred to as multidimensional arrays are actually arrays of arrays.

> As we saw in § 3.5.1 (p. 115), we can more easily understand these definitions by reading them from the inside out.

> ⚠ To use a multidimensional array in a range for, the loop control variable for all but the innermost array must be references.