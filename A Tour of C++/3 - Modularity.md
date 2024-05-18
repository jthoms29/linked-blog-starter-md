TARGET DECK
A Tour of C++::3 - Modularity

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

# Namespaces



