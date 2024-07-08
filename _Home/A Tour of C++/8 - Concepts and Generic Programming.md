TARGET DECK
Home::A Tour of C++::08 - Concepts and Generic Programming

# Concepts <!--fc-->
*Concepts* are what the constraints on an arguments a template can take are known as
![[Pasted image 20240701114506.png]]
	 `typename` is the most general, it is able to take any sort of *sequence* that supports `begin()` and `end()`, and any sort of similar arithmetic type `Value`
<!--ID: 1719877534436-->


## Use of Concepts

### Constraining Templates <!--fc-->
It is good practice in using templates to make them constrained, i.e. more specific than `typename`.
For example, this `sum()` function:
![[Pasted image 20240701163241.png]]
Versus:
![[Pasted image 20240701163301.png]]
Once we have defined what the concepts `Sequence` and `Number` mean, the compiler can reject bad calls by looking at the functions interface only, rather than its implementation.
- We may further specify that we should be able to add elements of `Sequence` to the given `Number`
	![[Pasted image 20240701163522.png]]
<!--ID: 1719877534444-->


#### ==\*\*==`range_value_t` <!--fc-->
The `range_value_t` of a sequence is the type of the elements in that sequence.
It comes from the standard library where it names the type of the elements of a `range`.
<!--ID: 1719877534463-->


#### ==\*\*==`arithmetic<X,Y>` <!--fc-->
A concept specifying that we can do arithmetic with numbers of type `X` and `Y`. (can mix different arithmetic types)
Typically, when an algorithm requires arguments of differing types and their is a relationship between them, it is good to make that explicit
<!--ID: 1719877534475-->


#### ==\*\*==Requirements clause <!--fc-->
```C++
template<Sequence Seq, Number Num>
	requires Arithmetic<range_value_t<Seq>,Num>
Num sum(seq s, Num n);
```
`requires Arithmetic<range_value_t<Seq>,Num>` is called a requirements clause.
.
- `template<Sequence seq>` is shorthand for an explicit use of `requires Sequence<Seq>`
**Verbose Version**
![[Pasted image 20240701174254.png]]
**Nicer Version**
![[Pasted image 20240701174330.png]]
<!--ID: 1719877534484-->


## Concept-based Overloading <!--fc-->
Once we have properly specified templates with their interfaces, we can overload based on their properties, similar to how we can do for functions
- *Example*: Consider a simplified version of the standard lib function `advance()` that advances an iterator
	![[Pasted image 20240701175830.png]]
	The compiler will choose the template with the strongest requirements met by the arguments.
	- In this case, `list` only supplies forward iterators, while `vector` offers random access iteration
		![[Pasted image 20240701180015.png]]
<!--ID: 1719878500194-->


# Valid Code

## Requires expression <!--fc-->
Using a `requires` expression, we can check if a set of expressions is valid
- *Example:* Trying to write `advance()` without the use of the standard-library concept `random_access_iterator`
	![[Pasted image 20240701192210.png]]
	`requires requires` is not a typo. The first `requires` start the requirements-clause and the second starts the requires expression
	- `requires(iter p, int i) { p[i]; p+i }`
		A requires-expression is a predicate which is `true` if the statements are valid code and `false` if not.
requires-expressions should not be seen in ordinary code. They belong in implementations of abstractions.
<!--ID: 1719939587884-->

# Definition of Concepts <!--fc-->
Many useful concepts can be found in libraries, like `forward_iterator`. It is often easier to use a concept from a good library than to write a new one. If need be, this is how you would define them:
```C++
template <typename T>
concept Equality_comparable = 
	requires (T a, T b) {
		{ a == b } -> Boolean; // compare Ts with ==
		{ a != b } -> Boolean: // compare Ts with !=
	}
```
We're saying that given two values of the same type, they must be comparable using `==` and `!=` and they must return a Boolean. For example:
![[Pasted image 20240706142342.png]]
<!--ID: 1720307195677-->


## Non-homogenous comparisons in concept definition <!--fc-->
![[Pasted image 20240706163735.png]]
Making the operations work for both types in either order
<!--ID: 1720307195682-->


## Default template argument <!--fc-->
```C++
template<typename T, typename T2=T>
```
`typename T2=T` says that if we don't specify a second template argument, `T2` will be the same as `T`
<!--ID: 1720307195687-->


## ==\*\*==Example: Defining concept that requires arithmetic to be valid between numbers
	![[Pasted image 20240706144952.png]]
	Given one argument type, `Number<X>` checks whether `X` has the desired properties of `Number`.
	Given two arguments, `Number<X,Y>` checks that the two can be used together with the required operations.
- To make it go both ways:
```C++
concept Arithmetic = Number<T,U> && Number<U,T>	
```

## ==\*\*==Example: Defining Sequence
- Defining a sequence concept:
	![[Pasted image 20240706164033.png]]
	For `S` to be a sequence, it must
	- Provide a value type
	- Provide and iterator type
	- Have `begin()` and `end()` functions
	- Must have at least an `input_iterator`
	- All values must be the same

## Definition Checking <!--fc-->
The concepts specified for a template are used to check arguments at the point of use of the template. **They are not used to check the use of parameters in the definition of the template**
- Example:
	![[Pasted image 20240706164504.png]]
	If `equality_comparable` guarantees the presence of `==` but not `<`, then it won't be guaranteed you won't have errors.
<!--ID: 1720307195691-->


# Concepts and `auto`

## Constraining `auto` function arguments <!--fc-->
The keyword `auto` can be used to indicate than an object should have the type of its initializer
```C++
auto x = 1;
```
However, it doesn't just take place in simple variable definitions.
It denotes the least constrained concept for a value, it simply requires that it must be a value of some type. Taking an `auto` parameter makes a function into a function template
- Given concepts, we can strengthen requirements of all such initializations by preceding `auto` by a concept
	![[Pasted image 20240706170532.png]]
<!--ID: 1720362896142-->


## Constraining initialization of `auto` variables <!--fc-->
You can use concepts to constrain the values allowed by an `auto` type variable.
![[Pasted image 20240706182905.png]]
<!--ID: 1720362896147-->


# Concepts and Types

## Difference between concepts and types <!--fc-->
Types:
- Specify the set of operations that can be applied to an object
- Rely on function definitions and language rules
- Specify how an object is laid out in memory
Concepts:
- Specify the set of operations that can be applied to an object
- Rely on patterns reflecting function declarations and language rules
- Say nothing about the layout of the object
- Enable the use of a set of types
Constraining code with concepts gives more flexibility than constraining with types.
<!--ID: 1720362896153-->


![[Pasted image 20240706184447.png]]


# Generic Programming <!--fc-->
The form of *generic programming* directly supported by C++ centers around the idea of abstracting from concrete, efficient algorithms to obtain generic algorithms that can be combined with different data representations to produce a wide variety of useful software.
The abstractions that represent the fundamental operations and data structures are called *concepts*
<!--ID: 1720362896157-->


## Use of concepts in generic programming <!--fc-->
*Concept* more in the theoretical sense as opposed to syntactical
Concepts (e.g.: integer, floating point, sequence) represent fundamental concepts of a field of application. That is why they're called *concepts*.
![[Pasted image 20240707072233.png]]
<!--ID: 1720362896161-->


## Abstraction using templates <!--fc-->
Don't try to write around every use case at the start, this can lead to bloated and inelegant code.
Start with one (or a few more) use cases and then try to eliminate inessential details:
	![[Pasted image 20240707072440.png]]
- Consider:
	Why just `ints`?
	Why just `vectors`?
	Why accumulate in a `double`?
	Why start at 0?
	Why add?
	![[Pasted image 20240707072624.png]]
This process is called *lifting*.
<!--ID: 1720362896165-->


# Variadic Templates <!--fc-->
A template can be defined to accept an arbitrary number of arguments of arbitrary types. This is called a *variadic template*
**Example:**
- Function that writes out values of any type that has a `<<` operator
	![[Pasted image 20240707080553.png]]
	Traditionally, implementing a variadic template works by separating the first argument from the rest and then recursively calling the variadic template for the tail of the arguments
	![[Pasted image 20240707082932.png]]
	`Printable...` indicates that `Tail` is a sequence of types
	`Tail...` indicates that `tail` is a sequence of `Tail`s
	Eventually `tail` will become empty, so we need a no-argument version of print. Or, we can eliminate print using a compile time `if`
	![[Pasted image 20240707083216.png]]
<!--ID: 1720362896169-->


## Parameter Pack <!--fc-->
Putting `...` after a type (`Tail... tail`) means you can have multiple arguments of that type.
<!--ID: 1720362896173-->


## Fold Expressions <!--fc-->
To simplify the implementation of variadic templates, C++ offers a limited form of iteration over elements of a parameter pack
	![[Pasted image 20240707150609.png]]
	This `sum()` can take any number of arguments of any types:
	![[Pasted image 20240707150710.png]]
	`return (v + ... + 0)` means add all the elements of `v` starting with the initial value 0. The first element to be added is the rightmost (with the highest index) 
	**Right fold:** `(v[0]+(v[1]+(v[2]+(v[3]+(v[4]+0)))))`
	Alternatively, you can do a left fold
	![[Pasted image 20240707195346.png]]
	**Left fold: `(((((0+v[0])+v[1])+v[2])+v[3])+v[4])`
<!--ID: 1720404306221-->


## Forwarding Arguments <!--fc-->
Passing arguments unchanged through an interface is an important part of variadic templates.
Consider a notion of a network input channel for which moving values is a parameter.
![[Pasted image 20240707195908.png]]
The standard library function `forward()` is used to move arguments unchanged from the `inputChannel` constructor to the `Transport` constructor.
<!--ID: 1720404306229-->


# Template Compilation Model <!--fc-->
To use an unconstrained template, it's definition (not just declaration) must be in scope at its point of use. You would write them in header files and `#include` them.
<!--ID: 1720404306234-->
