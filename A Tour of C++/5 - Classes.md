TARGET DECK
A Tour of C++::05 - Classes

# Concrete Types <!--fc-->
These behave just like built-in types
	*i.e.; complex number types work like `int` but with different semantics and operations*
- The defining characteristic of a concrete type is that its representation is part of its definition
	*i.e.; a `vector`'s representation is one or more pointers to data stored elsewhere, but this is present in each object of the concrete class*
<!--ID: 1717784590349-->


## An Arithmetic Type
A classical user-defined arithmetic type is `complex`
![[Pasted image 20240606184027.png]]
The class definition is simple and contains only operations requiring access to the representation

### Default Constructor <!--fc-->
A constructor that can be invoked without an argument
`complex()` would be complex's default constructor
<!--ID: 1717784590354-->


### `Const` specifier on function <!--fc-->
```C++
double real() const { return re; }
```
Indicates that the function does not modify the object for which it is called
<!--ID: 1717784590358-->


### Overloaded Operators<!--fc-->
Many useful operations do not require direct access to the representation of `complex`, so they can be defined elsewhere
```C++
complex operator+(complex a, complex b) { return a+=b; }
complex operator-(complex a, complex b) { return a-=b; }
complex operator-(complex a) { return {-a.real(), -a.imag()}; } // unary minus
complex operator∗(complex a, complex b) { return a∗=b; }
complex operator/(complex a, complex b) { return a/=b; }
```
User defined operators (overloaded operators) should be used cautiously and conventionally

## A Container <!--fc-->
A container is an object holding a collection of elements. We call class `vector` a container. It holds objects, provides a useful invariant and provides range checked access
<!--ID: 1717784590362-->


### Destructor <!--fc-->
Objects initialized onto the heap with `new` will not automatically be deleted; C++ does not have a garbage collector. For this reason, it's a good idea to define a *destructor* within classes
![[Pasted image 20240607121856.png]]
The name of a destructor is the complement operator (~) followed by the name of the class
This will automatically destroy the object when leaving scope or when used with `delete` expression
<!--ID: 1717784590366-->

#### Deleting objects from heap <!--fc-->
`delete` deletes individual objects, `delete[]` deletes arrays
<!--ID: 1717784590370-->


