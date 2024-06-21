TARGET DECK
Home::A Tour of C++::03 - Modularity

# Declaration #flashcard

Specifies all that's needed to use a function or type
```C++
double sqrt(double);
//
class Vector {
public:
	Vector(int s);
	double& operator[](int i);
	int size();
}
```
Function definitions can be *elsewhere*
These functions need to be defined
<!--ID: 1716066969092-->


# Separate Compilation #flashcard 

C++ supports a notion of separate compilation where user code sees only declarations of the types and functions used. This can be done in two ways, header files and module files
<!--ID: 1716066969109-->


## Header Files #flashcard

(`#include xxx.h`)
Traditionally, we place declarations that specify the interface to a piece of code we consider a module in a file with a name indicating its intended use
```C++
// Vector.h:
class Vector {
public:
	Vector(int s);
	double& operator[](int i);
	int size();
private:
	double∗ elem; // elem points to an array of sz doubles
	int sz;
};
```
This declaration would be placed in `Vector.h`. We would then `#include` this header file
<!--ID: 1716066969123-->


### Header definitions #flashcard 

To help the compiler ensure consistency, the `.cpp` file providing the implementation will also include the `.h` file providing its interface
```C++
// Vector.cpp:
#include "Vector.h" // get Vector’s interface
Vector::Vector(int s)
	:elem{new double[s]}, sz{s} // initialize members
{
}
//
double& Vector::operator[](int i)
{
	return elem[i];
}
//
int Vector::size()
{
	return sz;
}
```
![[Pasted image 20240518152201.png]]
<!--ID: 1716067343237-->


## Modules #flashcard 

```C++
//Vector.cpp
//
export module Vector; // defining the module called "Vector"
//
export class Vector {
public:
	Vector(int s);
	double& operator[](int i);
	int size();
private:
	double∗ elem; // elem points to an array of sz doubles
	int sz;
};
//
Vector::Vector(int s)
	:elem{new double[s]}, sz{s} // initialize members
{
}
//
double& Vector::operator[](int i)
{
	return elem[i];
}
//
int Vector::size()
{
	return sz;
}
//
export bool operator==(const Vector& v1, const Vector& v2)
{
	if (v1.size()!=v2.size())
		return false;
	for (int i = 0; i<v1.size(); ++i)
		if (v1[i]!=v2[i])
			return false;
	return true;
}
```
This defines a `module` called `Vector`, which exports the class `Vector`, all its member functions, and a non-member function defining the operator `==`.
Import this module to use it
```C++
import vector
```
Modules are faster than including headers too
<!--ID: 1716068006185-->

# Namespaces #flashcard 

C++ offers *namespaces* as a mechanism for expressing that some declarations belong together and that their names shouldn't clash with other names
```C++
namespace My_code {
	class complex {
		// ...
	};
	//
	complex sqrt(complex);
	// ...
	//
	int main();
}
//
int My_code::main()
{
	complex z {1,2};
	auto z2 = sqrt(z);
	std::cout << '{' << z2.real() << ',' << z2.imag() << "}\n";
// ...
}
//
int main()
{
	return My_code::main();
}
```
By putting it in the namespace `My_code`, there is an assurance that the names will not conflict with the standard library names in namespace std.
<!--ID: 1716072651713-->


## Accessing Namespaces #flashcard

Qualify it with the namespace name
```C++
std::cout
My_code::main
```
the real main() is defined in the global namespace, it's not local to anything
You can also use the `using` declaration
```C++
void my_code(vector<int>& x, vector<int>& y)
{
	using std::swap; // make the standard-library swap available locally
	// ...
	swap(x,y); // std::swap()
	other::swap(x,y); // some other swap()
	// ...
}
```
It applies to the scope in which it appears
<!--ID: 1716072651744-->


# Function Arguments and Return Values

## Argument Passing

**Pass by value** #flashcard 

Default argument passing, copying the value
<!--ID: 1716072865346-->


**Pass by Reference** #flashcard 

Refer to an object itself in the callers environment 
<!--ID: 1716072865363-->
```C++
void test(vector<int> v, vector<int>& rv) // v is passed by value; rv is passed by reference
{
	v[1] = 99; // modify v (a local variable)
	rv[2] = 66; // modify whatever rv refers to
}
```

### When to pass by value / reference #flashcard 

When we care about performance, we usually pass small values by value and larger ones by reference
If we want to pass by reference for performance without modifying, use `const`
<!--ID: 1716073230823-->


## Default Function arguments #flashcard 

We can specify default arguments in functions
```C++
void print(int value, int base =10); // print value in base "base"
	print(x,16); // hexadecimal
	print(x,60); // sexagesimal (Sumerian)
	print(x); // use the default: decimal
```
This is simpler than overloading
<!--ID: 1716073230849-->


## Value Return #flashcard 

The default for value return is to copy (for small objects this is ideal)
We return by reference when we want to grant a caller access to something not local to the function
**Remember, local variables disappear when functions return, don't return references to those**
<!--ID: 1716074658536-->


### Getting large amounts of info out of a function #flashcard 

```C++
Matrix operator+(const Matrix& x, const Matrix& y)
{
	Matrix res;
	// ... for all res[i,j], res[i,j] = x[i,j]+y[i,j] ...
	return res;
}
//
Matrix m1, m2;
// ...
Matrix m3 = m1+m2; // no copy
```
A Matrix may be very large and expensive to copy, so we give `Matrix` a move constructor that cheaply moves `Matrix` out of `operator+()`.
<!--ID: 1716074658558-->


# Return Type Deduction #flashcard 

```C++
auto mul(int i, double d) { return i*d; }
```
<!--ID: 1716074658572-->


### Suffix return type #flashcard 

When using return type deduction, we can still specify the return type afterwards
```C++
auto next_elem() -> Elem∗;
auto exit(int) -> void;
auto sqrt(double) -> double;
```
<!--ID: 1716074658585-->



# Structured Binding #flashcard 

A function can only return a single value, but that may be a class object with many members
```C++
struct Entry {
	string name;
	int value;
};
//
Entry read_entry(istream& is) 
{
	string s;
	int i;
	is >> s >> i;
	return {s,i};
}
```
<!--ID: 1716074658599-->


