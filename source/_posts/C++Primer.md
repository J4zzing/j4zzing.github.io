---
title: C++ Primer - The Basics
date: 2020-09-16 21:14:07
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

> 🚨 As with variables of built-in type, a default-initialized array of built-in type that is defined inside a function will have undefined values.

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
> 🚨 Unlike subscripts for vector and string, the index of the built-in subscript operator is not an unsigned type.

#### 3.5.4 C-Style Character Strings

> 🚨 Although C++ supports C-style strings, they should not be used by C++ programs. C-style strings are a surprisingly rich source of bugs and are the root cause of many security problems. They’re also harder to use!

#### 3.5.5 Interfacing to Older Code

> More generally, we can use a null-terminated character array anywhere that we can use a string literal.

> If a program needs continuing access to the contents of the array returned by `c_str`(), the program must copy the array returned by `c_str`.

> Modern C++ programs should use `vector`s and iterators instead of built-in arrays and pointers, and use strings rather than C-style array-based character strings.

### 3.6 Multidimensional Array

> Strictly speaking, there are no multidimensional arrays in C++. What are commonly referred to as multidimensional arrays are actually arrays of arrays.

> As we saw in § 3.5.1 (p. 115), we can more easily understand these definitions by reading them from the inside out.

> 🚨 To use a multidimensional array in a range for, the loop control variable for all but the innermost array must be references.

## Chapter 4 - Expressions

> This chapter focuses on the operators as defined in the language and applied to operands of built-in type. We will also look at some of the operators defined by the library.

> An expression is composed of one or more operands and yields a result when
> it is evaluated. <u>The simplest form of an expression is a single literal or variable.</u>

### 4.1 Fundamentals

#### 4.1.1 Basic Concepts

> There are both **unary operators** and **binary operators**. Unary operators, such as
> address-of (&) and dereference ( * ), act on one operand. Binary operators, such as
> equality (==) and multiplication ( * ), act on two operands. There is also one **ternary**
> **operator** that takes three operands, and one operator, <u>function call</u>, that takes an
> unlimited number of operands.

> Understanding expressions with multiple operators requires understanding the
> precedence and associativity of the operators and may depend on the order of
> evaluation of the operands.

> As part of evaluating an expression, operands are often converted from one type to another. These operators can be used on operands with differing types so long as the operands can be converted (§ 2.1.2, p. 35) to a common type.

> We can also define what most operators mean when applied to class
> types. Because such definitions give an alternative meaning to an existing opera-
> tor symbol, we refer to them as **overloaded operators**.

> Every expression in C++ is either an **rvalue** or an **lvalue**. These names are inherited from C and originally had a simple mnemonic purpose: lvalues could stand on the left-hand side of an assignment whereas rvalues could not.
>
> In C++, an lvalue expression yields an object or a function. However, some lvalues, such as const objects, may not be the left-hand operand of an assignment. Roughly speaking, when we use an object as an rvalue, we use the object’s value (its contents). When we use an object as an lvalue, we use the object’s identity (its location in memory).
>
> The important point is that (with one exception that we’ll cover in § 13.6 (p. 531))we can use an lvalue when an rvalue is required, but we cannot use an rvalue when an lvalue (i.e., a location) is required. When we use an lvalue in place of an rvalue, the object’s contents (its value) are used.
>
> • Assignment requiresa(nonconst) lvalueas its left-handoperandand yields its left-hand operand as an lvalue.
> • The address-of operator requires an lvalue operand and returns a pointer to its operand as an rvalue.
> • The built-in dereference and subscript operators and the iterator dereferenceand string and vector subscript operators all yield lvalues.
> • The built-in and iterator increment and decrement operators require lvalue operands and the prefix versions (which are the ones we have used so far) also yield lvalues.
>
> When we apply `decltype` to an expression (other than a variable), the result is a reference type if the expression yields an lvalue. As an example, assume p is an `int *` . Because dereference yields an lvalue, `decltype( * p)` is `int&`.

#### 4.1.2 Predence and Associativety

> An expression with two or more operators is a **compound expression**. Evaluating a compound expression involves grouping the operands to the operators. **Precedence** and **associativity** determine how the operands are grouped. Programmers can override these rules by parenthesizing compound expressions to force a particular grouping.
>
> In general, the value of an expression depends on how the subexpressions are grouped. Operands of operators with higher precedence group more tightly than operands of operators at lower precedence. Associativity determines how to group operands with the same precedence.

#### 4.1.3 Order of Evaluation

> Precedence specifies how the operands are grouped. It says nothing about the order in which the operands are evaluated. In most cases, the order is largely unspecified. In the following expression
>
> ```C++
> int i = f1() * f2();
> ```
>
> we know that f1 and f2 must be called before the multiplication can be done. However, we have no way of knowing whether f1 will be called before f2 or vice versa.
>
> For operators that do not specify evaluation order, it is an error for an expression to *refer to and change* the same object. Expressions that do so have undefined behavior (§ 2.1.2, p. 36). As a simple example, the << operator makes no guarantees about when or how its operands are evaluated. As a result, the following output expression is undefined:
>
> ```C++
> int i = 0;
> cout >> i >> " " >> ++i >> endl;  // undefined
> ```

There are four operators that do guarantee the order in which operands are evaluated:

- the logical AND (&&) operator

- the logical OR (||) operator
- the conditional (? :) operator
- the comma (,) operator

> ADVICE: When you write compound expressions, two rules of thumb can be helpful:
> 1. When in doubt, parenthesize expressions to force the grouping that the logic of
> your program requires.
> 2. If you change the value of an operand, don’t use that operand elsewhere in the
> same expresion.

#### 4.2 Arithmetic Operators

> Unless noted otherwise, the arithmetic operators may be applied to any of the
> arithmetic types (§2.1.1,p. 32)or to any type that can be converted to an arithmetic
> type. The operands and results of these operators are rvalues. As described in
> § 4.11 (p. 159), operands of small integral types are promoted to a larger integral
> type, and all operands may be converted to a common type as part of evaluating
> these operators.
>
> *<C++11>* Earlier versions of the language permited a negative quotient to be rounded up or down; the new standard requires the quotient to be rounded toward zero (i.e., truncated).
>
> *<C++11>*  Earlier versions of the language permitted m%n to have the same sign as
> n on implementations in which negative m/n was rounded away from zero, but
> such implementations are now prohibited.

#### 4.3 Logical and Relational Operators

> The relational operators take operandsof arithmetic or pointer type; the logical op-
> erators take operands of any type that can be converted to bool. These operators
> all return values of type bool. Arithmetic and pointer operand(s) with a value of zero are false; all other values are true. The operands to these operators are
> rvalues and the result is an rvalue.

Precedence of Logical and Relational Operators:

1. !
2. <, <=, >, >=
3. ==, !=
4. &&
5. ||

> The logical AND and OR operators always evaluate their left operand before the right. Moreover, the right operand is evaluated if and only if the left operand does
> not determine the result. This strategy is known as short-circuit evaluation:
> • The right side of an && is evaluated if and only if the left side is true.
> • The right side of an || is evaluated if and only if the left side is false.

> ```C++
> if (val == true) { / * . . .* / } // true only if val is equal to 1 
> ```
>
> 🚨 It is usually a bad idea to use the boolean literals true and false as operands in a comparison. These literals should be used only to compare to an object of type bool.

#### 4.4 Assignment Operators

> The left-hand operand of an assignment operator must be a modifiable lvalue.
>
> The result of an assignment is its left-hand operand, which is an lvalue. If the types of the left and right operands differ, the right-hand operand is converted to the type of the left.

> *<C++11>* Under the new standard, we can use a braced initializer list (§ 2.2.1, p. 43) on the right-hand side:
>
> ```C++
> k = {3.14}; // error: narrowing conversion
> vector<int> vi; // initially empty
> vi = {0,1,2,3,4,5,6,7,8,9}; // vi now has ten elements, values 0 through 9
> ```
>
> If the left-hand operand is of a built-in type, the initializer list may contain at most one value, and that value must not require a narrowing conversion (§ 2.2.1, p. 43).
>
> For class types, what happens depends on the details of the class. In the case of
> vector, the vector template defines its own version of an assignment operator
> that can take an initializer list. This operator replaces the elements of the left-hand
> side with the elements in the list on the right-hand side.
>
> Regardless of the type of the left-hand operand, the initializer list maybe empty. In this case, the compiler generates a value-initialized(§3.3.1,p.98) temporary and assigns that value to the left-hand operand.

> Assignment is right associative. Each object in a multiple assignment must have the same type as its right-hand neighbor or a type to which that neighbor can be converted (§ 4.11, p. 159).
>
> ```C++
> int ival, * pval; // ival is an int ; pval is a pointer to int
> ival = pval = 0; // error: cannot assign the value of a pointer to an int
> ```

> Assignments often occur in conditions. Because assignment has relatively low precedence, we usually must parenthesize the assignment for the condition to work properly.
>
> ```C++
> int i;
> while ((i = get_value()) != 42) {
>   // do something . . .
> }
> ```

> Compound Assignment Operators: 
>
> ```C++
> +=, -=, *=, /=, %=   // arithmetic operators
> <<=, >>=, &=, ^=, |= // bitwise operators; see § 4.8 (p. 152)
> ```
>
> when we use the compound assignment, the left-hand operand is evaluated only once. If we use an ordinary assignment, that operand is evaluated twice: once in the expression on the right-hand side and again as the operand on the left hand. In many, perhaps most, contexts this difference is immaterial aside from possible performance consequences.

#### 4.5 Increment and Decrement Operators

> The increment (++) and decrement (--) operators provide a convenient notational shorthand for adding or subtracting 1 from an object. This notation rises above mere convenience when we use these operators with iterators, because many iterators do not support arithmetic.

> There are two forms of these operators: prefix and postfix. The prefix operators increments (or decrements) its operand and yields the changed object as its result. The postfix operators increment (or decrement) the operand but yield a copy of the original, unchanged value as its result.
>
> These operators require lvalue operands. The prefix operators return the object itself as an lvalue. The postfix operators return a copy of the object’s original value as an rvalue.

> <u>ADVICE : USE POSTFIX OPERATORS ONLY WHEN NECESSARY</u>
> Readers from a C background might be surprised that we use the prefix increment in
> the programs we’ve written. The reason is simple: The prefix version avoids unnecessary work. It increments the value and returns the incremented version. The postfix operator must store the original value so that it can return the unincremented value as its result. If we don’t need the unincremented value, there’s no need for the extra work done by the postfix operator.

> Combining Dereference and Increment in a Single Expression:
>
> ```C++
> auto pbeg = v.begin(); // print elements up to the first negative value
> while (pbeg != v.end() && *beg >= 0)
>     cout << *pbeg++ << endl; // print the current value and advance pbeg
> ```
>
> The precedenceof postfix increment is higher than that of the dereference operator, so `*pbeg++` is equivalent to `*(pbeg++)`.

> <u>ADVICE : BREVITY CAN BE A VIRTUE</u>
> Expressions such as `*pbeg++` can be bewildering—at first. However, it is a useful and widely used <u>idiom</u>. Once the notation is familiar, writing
>
> ```C++
> cout << * iter++ << endl;
> ```
>
> is easier and less error-prone than the more verbose equivalent
>
> ```C++
> cout << * iter << endl;
> ++iter;
> ```
>
> It is worthwhile to study examples of such code until their meanings are immediately clear. Most C++ programs use succinct expressions rather than more verbose equivalents. Therefore, C++ programmers must be comfortable with such usages. Moreover, once these expressions are familiar, you will find them less error-prone.

> Because the increment and decrement operators change their operands, it is easy to misuse these operators in compound expressions.
>
> ```C++
> // the behavior of the following loop is undefined!
> while (beg != s.end() && !isspace( *beg))
>     *beg = toupper( *beg++);  // error: this assignment is undefined
> ```
>
> The compiler might evaluate this expression as either
> ```C++
> beg = toupper( *beg);  // execution if left-hand side is evaluated first
> (beg + 1) = toupper( *beg);  // execution if right-hand side is evaluated first
> ```
>
> or it might evaluate it in yet some other way.

#### 4.6 The Member Access Operators

> The dot and arrow operators provide for member access. The dot operator fetches a member from an object of class type; arrow is defined so that `ptr->mem` is a synonym for `(*ptr).mem`.
>
> Dereference has a lower precedence than dot.
>
> The arrow operator requires a pointer operand and yields an lvalue. The dot operator yields an lvalue if the object from which the member is fetched is an lvalue; otherwise the result is an rvalue.

#### 4.7 The Conditional Operators

> The conditional operator has the following form:
> `cond ? expr1 : expr2;`
>
> The conditional operator guarantees that only one of `expr1` or `expr2` is evaluated.
>
> That result of the conditional operator is an lvalue if both expressions are lvalues or if they convert to a common lvalue type. Otherwise the result is an rvalue.

> We can nest one conditional operator inside another:
>
> ```C++
> string finalgrade = (grade > 90) ? "high pass"
> 								 : (grade < 60) ? "fail" : "pass";
> ```
>
> The conditional operator is right associative, meaning (as usual) that the operands group right to left.
>
> 🚨 Nested conditionals quickly become unreadable. It’s a good idea to nest no more than two or three.

> The conditional operator has fairly low precedence. When we embed a conditional
> expression in a larger expression, we usually must parenthesize the conditional
> subexpression. For example:
>
> ```C++
> cout << ((grade < 60) ? "fail" : "pass"); // prints pass or fail
> cout << (grade < 60) ? "fail" : "pass"; // prints 1 or 0 !
> cout << grade < 60 ? "fail" : "pass"; // error: compares cout to 60
> ```

#### 4.8 The Bitwise Operators

> The bitwise operators take operands of integral type that they use as a collection
> of bits. These operators let us test and set individual bits.
>
> As usual, if an operand is a “small integer,” its value is first promoted (§ 4.11.1, p. 160) to a larger integral type. The operand(s) can be either signed or unsigned.
>
> Because there are no guarantees for how the sign bit is handled, we strongly recommend using unsigned types with the bitwise operators.

> The >> and << operators yield a value that is a copy of the (possibly promoted) left-hand operand with the bits shifted as directed by the right-hand operand. The right-hand operand must not be negative and must be a value that is strictly less than the number of bits in the result. Otherwise, the operation is undefined. 
>
> The left-shift operator (the << operator) inserts 0-valued bits on the right. The behavior of the right-shift operator (the >> operator) depends on the type of the left-handoperand: If that operand is unsigned, then the operator inserts 0-valued bits on the left; if it is a signed type, the result is implementation defined—either copies of the sign bit or 0-valued bits are inserted on the left.