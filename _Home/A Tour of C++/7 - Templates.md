TARGET DECK
Home::A Tour of C++::07 - Templates

# Template <!--fc-->
A template is a class or a function that we parameterize with a set of types or values. We use templates to represent ideas that are best understood as something general from which we can generate specific types and functions by specifying arguments, such as `double` as `vector`'s element type.
<!--ID: 1719205476399-->


# Parameterized Types <!--fc-->
As an example, we can generalize a vector of any type by making it a *template* and using that specific type parameter:
![[Pasted image 20240622144324.png]]
`template<typename T>` makes `T` a type parameter of the declaration it prefixes, like generics in Java.
<!--ID: 1719205476405-->


## Template Member function definition <!--fc-->
![[Pasted image 20240622153816.png]]
You need to specify `template<typename T>` every time. Given these definitions, we can define vectors like this:
![[Pasted image 20240622155300.png]]
<!--ID: 1719205476410-->


### Implementing range-`for` loop in vector <!--fc-->
We must define suitable `begin()` and `end()` functions
![[Pasted image 20240622155512.png]]
<!--ID: 1719205476414-->


# Constrained Template Arguments <!--fc-->
Often, a template will only make sense for arguments that meet certain criteria.
For example. a `Vector` type typically offers a copy operation, so it follows that its elements must be copyable.
- For this, we must require that the template argument isn't just a `typename`, but an `Element`, where `Element` specifies the requirements of a type that can be an element
In `template<Element T>`, the `Element` is a predicate that checks whether `T` has all the properties that a class requires. Failure to have these properties results in a compile-time error
<!--ID: 1719205476418-->


# Value Template Arguments <!--fc-->
In addition to type arguments, a template can take value arguments
```C++
template<typename T, int N>
struct Buffer {
	constexpr int size() { return N; }
	T elem[N];
	// ...
};
```
In this example, `Buffer` allows us to create arbitrarily sized buffers with no use of dynamic memory
<!--ID: 1719205476423-->


## String Literal as template argument <!--fc-->
For obscure technical reasons, a string literal cannot be a template argument. You can still use a C style character array, however
![[Pasted image 20240623194846.png]]
<!--ID: 1719205476427-->


# Template Argument Deduction <!--fc-->
When defining a type as an instantiation of a template we must specify its template arguments.
```C++
pair<int,double> p = {1, 5.2};
```
This can be tedious, so in many contexts we can simply let `pair`'s constructor deduce the template arguments from an initializer
```C++
pair p = {1, 5.2}
```
- This may not work how you expect at all times
![[Pasted image 20240623230201.png]]
<!--ID: 1719205476432-->


## Deduction Guide for template arguments <!--fc-->
Sometimes we need to resolve an ambiguity. For example, `vector` has a constructor that takes a pair of iterators delimiting a sequence and also an initializer constructor that can take a pair of values
![[Pasted image 20240623230823.png]]
![[Pasted image 20240623230835.png]]
Using a deduction guide, we are able to say that a pair of values of the same type should be considered iterators
![[Pasted image 20240623230926.png]]
Now we have:
![[Pasted image 20240623231014.png]]
<!--ID: 1719205900110-->


# Parameterized Operations
Templates have many more uses than simply parameterizing a container with an element type. They are extensively used for parameterization of both types and algorithms in the standard library
There are three ways of expressing an operation parameterized by types or values:
- A function template
- A function object: *an object that can carry data and be called like a function*
- A lambda expression: *shorthand notation for a function object*

## Function Templates <!--fc-->
- The ability to let a function take multiple argument types
For example:
We can write a function that calculates the sum of the element values of any sequence that range-`for` can traverse like this
```C++
template<typename Sequence, typename Value>
Value sum(const Sequence& s, Value v) {
	for (auto x : s)
		v+=x
	retun v;
}
```
The `Value` template argument and the function argument `v` are there to allow the caller to specify the type and initial value of the accumulator.
![[Pasted image 20240624132737.png]]
<!--ID: 1719260469122-->


## Function Objects <!--fc-->
One particularly useful kind of template is the *function object* (functor), which is used to define objects that can be used like functions. 
For example:
```C++
template<typename T>
class Less_than {
	const T val; // value to compare against
public:
	Less_then(const T& v): val{v} {}
	bool operator()(const T& x) const {return x<val: } // call operator
}
```
The function called `operator()` implements the *application operator*, `()`, also called *function call* or just *call*.
- We can define named variables of type `Less_than` for some argument type:
![[Pasted image 20240624133449.png]]
- We can then call such an object, just as we call a function
![[Pasted image 20240624133525.png]]
The beauty of function objects is that they carry the value to be compared against with them. We don't have to write a separate function for each value or type or hold any global variables.
<!--ID: 1719260469129-->

## Lambda Expressions <!--fc-->
There is a notation for implicitly generating function objects:
![[Pasted image 20240624133905.png]]
The notation `[&](int a){return a<x; }` is called a *lambda expression*.
It generates a function object similar to the previous `Less_than<int>{x}`.
- `[&]` is a capture list specifying that all local names used in the lambda body (such as `x`) will be accessed through references. 
- If we wanted to capture only `x`, we would use `[&x]`. 
- If we wanted to copy we could use `[x]`. 
- To copy all names by value we use `[=]` 
- Capture nothing is `[]`
<!--ID: 1719260469133-->


### Capturing object in lambda expressions <!--fc-->
For a lambda defined member function, `[this]` captures the current object by reference so we may compare to class members
- `[*this]` gets a copy of the current object.
- To capture multiple specific objects we can list them; `[i,this]`
<!--ID: 1719260469137-->


### Lambdas as function arguments <!--fc-->
Using lambdas can be convenient, but also obscure. For nontrivial actions, it's better to name the operation so as to more clearly state its purpose and make it available for use several places in the programs
Earlier, we noted the annoyance of having to write many functions to preform operations on elements of `vector`s of pointers and `unique_ptr`s, such as `draw_all()` and `rotate_all()`. Function objects (in particular, lambdas) can help by allowing us to separate traversal of the container from the specification of what is to be done with each element
![[Pasted image 20240624143129.png]]
Now, we can write a version of `user()` without writing a set of `_all` functions
![[Pasted image 20240624143219.png]]
You can pass the `unique_ptr<Shapes>` to the lambdas by reference
```C++
template<class S>
void rotate_and_draw(vector<S>& v, int r) {
	for_each(v,[](auto& s) {s->rotate(r); s->draw(); })
}
```
`auto` means the value of any type is accepted as an initializer.
- *generic lambda* - a lambda with an auto parameter
When needed, we can constrain the parameter with a concept
We could define `Pointer_to_class` to require `*` and `->` and write
![[Pasted image 20240624151534.png]]
We can call this generic `roate_and_draw()` with any container of objects you can draw and rotate
![[Pasted image 20240624165812.png]]
<!--ID: 1719273002662-->


### Lambdas for initialization <!--fc-->
Consider a complicated initialization
![[Pasted image 20240624173000.png]]
We need to select among a set of alternatives for initializing this data structure.
Instead of this mess, we could convert it to a lambda used as an initializer
![[Pasted image 20240624173201.png]]
<!--ID: 1719273002683-->


### `finally()` <!--fc-->
If we need to do cleanup that isn't associated with a single object, or with an object that doesn't have a destructor, we can define a function, `finally()`, that takes an action to be executed on the exit from the scope
![[Pasted image 20240624173641.png]]
This is better than ad-hoc `free(p)` calls
![[Pasted image 20240624173720.png]]
`[[nodiscard]]` ensures users do not forget to copy a generated `Final_action` into the scope for which its action is intended.
- The class `Final_action` that supplies the necessary destructor can look like this
![[Pasted image 20240624173844.png]]
<!--ID: 1719273002688-->


# Template Mechanisms
To define good templates, we need some supporting language facilities:
![[Pasted image 20240624173946.png]]
These basic mechanisms are primarily tools for building general, foundational abstractions.

## Variable Templates <!--fc-->
When we use a type, we often want constants and values of that type. This is also the case with templates.
When we define `C<T>`, we often want constants and variables of this type depending on T
![[Pasted image 20240624174139.png]]
The standard library uses variable templates to provide mathematical constants such as `pi` and `log2e`
<!--ID: 1719273002693-->


## Aliases <!--fc-->
Sometimes, it is useful to introduce a synonym for a type or template
For example, `<cstddef>` contains a definition of `size_t`. maybe:
	`using size_t = unsigned int;`
`size_t` is implementation dependent, another may be an `unsinged_long`. Having the alias `size_t` allows the programmer to write portable code.
- It is common for a parameterized type to provide an alias of types relating to their template arguments:
- ![[Pasted image 20240624174545.png]]
Every standard library container provides `value_type` as the name for the type of its elements.
![[Pasted image 20240624174648.png]]
<!--ID: 1719273002698-->


## Compile-time `if` <!--fc-->
Consider writing an operation that can be implemented `slow_and_safe(T)` or `simple_and_fast(T)`.
![[Pasted image 20240624174803.png]]
The `is_trivially_copyable_v<T>` is a type predicate that tells us if a type can be trivially copied. `if constexpr` is only checked by the compiler.
<!--ID: 1719273002703-->
