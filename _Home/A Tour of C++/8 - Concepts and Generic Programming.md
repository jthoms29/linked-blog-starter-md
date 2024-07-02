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


## Valid Code

### Requires expression <!--fc-->
Using a `requires` expression, we can check if a set of expressions is valid
- *Example:* Trying to write `advance()` without the use of the standard-library concept `random_access_iterator`
	![[Pasted image 20240701192210.png]]
	`requires requires` is not a typo. The first `requires` start the requirements-clause and the second starts the requires expression
	- `requires(iter p, int i) { p[i]; p+i }`
		A requires-expression is a predicate which is `true` if the statements are valid code and `false` if not.
requires-expressions should not be seen in ordinary code. They belong in implementations of abstractions.

#### ==\*\*==Use of `requires requires`
