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

## Initializing Containers
We can create a `vector` with an appropriate number of elements and then assign to those later, but there are more elegant ways of doing this such as:
- *Initializer-list constructor* - Initialize with a list of elements
- `push_back()` - Add a new element at the end of the sequence
```C++
class Vector {
public:
	Vector();        // default initialize to "empty"
	Vector(std::initializer_list<double>);    //initialize with list of doubles
	void push_back(double)    //add element at end, increasing size by one
}
```

### Initializer Lists <!--fc-->
`std::initializer_list` is used to define the initializer list constructor and is a standard-library type known to the compiler. When given a {} list such as `{1,2,3,4}`, the compiler will crate an object of type `initializer_list` to give to the program
```C++
Vector v1 = {1, 2, 3, 4, 5};    // v1 has 5 elements
Vector v2 = {1.23, 3.45, 6.7, 8};    // v2 has 4 elements
```
<!--ID: 1717863084216-->


# Abstract Types <!--fc-->
An *abstract type* is a type that completely insulates a user from implementation details. To do this, we decouple the interface from the implementation and give up genuine local variables. 
- Since we don't know anything about the representation (including size), we must allocate objects on the free store and access them through references or pointers
![[Pasted image 20240608085315.png]]
This class is a pure interface to specific containers defined later
<!--ID: 1717863084223-->


## Virtual functions <!--fc-->
The word `virtual` means "may be redefined in a later class defined from this one"
- `=0` syntax means a function is *pure virtual*, some class derived from this one **must** define the function
<!--ID: 1717863084227-->


## Abstract Class <!--fc-->
A class with only virtual functions. These do not have a constructor
<!--ID: 1717863084231-->


## Use of Abstract Classes <!--fc-->
Abstract classes can be used like this
```C++
void use(Container& c)
{
	const int sz = c.size();
	//
	for (int i=0; i!=sz; ++i)
		cout << c[i] << '\n';
}
```
`use()` uses `size()` and `[]` without any idea of how they are actually implemented
<!--ID: 1717863084236-->


## Implementing abstract classes <!--fc-->
![[Pasted image 20240608100637.png]]
The members `operator[]()` and `size()` are said to *override* the corresponding members in the base abstract class. This use is optional, but it helps make things explicit
- A different function using the abstract class, such as `use(container&)` has no idea what container actually is, allowing for more flexibility
<!--ID: 1717863084240-->


# Virtual Function Table <!--fc-->
For when a virtual function is used, the object must contain information to allow it to select the right function to call at run time. The compiler converts the name of a virtual function into an index into a table of pointers of functions, a *virtual function table (vtbl)*
- Each class with virtual functions has its own vtbl
![[Pasted image 20240609104346.png]]
These allow the object to be used correctly even when the details are unknown to the caller
<!--ID: 1717952847311-->


# Class Hierarchies <!--fc-->
A *class hierarchy* is a set of classes ordered in a lattice created by derivation. *A fire engine is a kind of truck which is a kind of vehicle*
![[Pasted image 20240609104527.png]]
Example of implementation of inheritence
![[Pasted image 20240609104628.png]]
![[Pasted image 20240609104641.png]]
<!--ID: 1717952847319-->


## Using classes in hierarchies <!--fc-->
We tend to allocate them on free storage using `new` and access them through pointers or references. We can return pointers from functions since the objects are allocated on the heap
<!--ID: 1717952847323-->


# Hierarchy Navigation

## `dynamic_cast` <!--fc-->
When using higher order classes, we may want to check if the class is of a more specified type; *is this shape a triangle?*
In this case, use the `dynamic_cast` operator
![[Pasted image 20240609105422.png]]
If the type is not what is expected, `dynamic_cast` returns `nullptr`
<!--ID: 1717952847328-->


### `dynamic_cast` to references <!--fc-->
When a different type is unacceptable, we can `dynamic_cast` to a reference type. If the object is not of the expected type, `dynamic_cast` throws a `bad_cast` exception
```C++
Shape∗ ps {read_shape(cin)};
Smiley& r {dynamic_cast<Smiley&>(∗ps)};  // somewhere, catch std::bad_cast
```
<!--ID: 1717952847333-->


# Avoiding Resource Leaks
Pointers to objects allocated on free store are dangerous, because we may fail to free them
![[Pasted image 20240609105929.png]]
*This will leak unless `x` is positive*

## `unique_ptr` <!--fc-->
From the standard library. You can use these instead of naked pointers when deletion is required
```C++
class Smiley : public Circle {
	// ...
private:
	vector<unique_ptr<Shape>> eyes; // usually two eyes
	unique_ptr<Shape> mouth;
};
```
We don't need to generate a destructor for these, the compiler will generate one implicitly when the object goes out of scope
<!--ID: 1717952847337-->

