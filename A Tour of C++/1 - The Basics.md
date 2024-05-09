`<<` - put to: writes second argument onto it's first
```C++
std::cout << "Hello, world\n";
```
*The string literal is written onto the standard output stream

### Importing
There are two different ways to import libraries
```C++
import std; //new, presents all of the stanard lib as module std

#include <iostream> //works everwhere, includes code directly
```

`using namespace std;` allows you to not have to write std::whatever

### Functions
Work basically the same as in C
**Member Functions** - functions that are the member of a class
	For these, the name of the class is also part of the function type
	
```C++
char& String::operator[](int index)
```

### Types, Vars, Arithmetic
**Declarations** - a statement that introduces an entity to a program and specifies its type
``int inch;``

![[Pasted image 20240508165033.png]]

`sizeof(x);` - use this operator to get the size of a datatype on a specific machine, helps with portability

```C++
0x34903 // hexidecimal
0343    // octal


3.1434'343'434343'34343 //single quotes can be used in literals for readability
```

In assignments and in arithmetic operations, C++ performs all meaningful conversions between the basic types so they can be mixed freely
```C++
void func() {
	double d = 2.2 //float
	int i = 7;     //integer
	d = d+i;       //assigned to float
	i = d+i;       //assinged to int
}
```

### Initialization
C++ offers a variety of notations for expressing initialization
```C++
int i1 = 7.8  //i1 becomes 7
int i2{7.8}   //error: floating point to integer conversion
```
In general, you should use the second way (**<u>delimited initializer lists</u>**).

**Auto**
You can use auto to have the type be deduced from the initializer
```C++
auto d = 1.2 //double
auto z = sqrt(y) //whatever sqrt returns
auto bb{true} //bool
```
With this, we tend to you = because there is no potentially troublesome type conversion.
We use auto when we don't have a specific reason to type specifically

### Scope and Lifetime




