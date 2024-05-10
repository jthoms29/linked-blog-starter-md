`<<` - put to: writes second argument onto it's first
```C++
std::cout << "Hello, world\n";
```
*The string literal is written onto the standard output stream

# Importing
There are two different ways to import libraries
```C++
import std; //new, presents all of the stanard lib as module std

#include <iostream> //works everwhere, includes code directly
```

`using namespace std;` allows you to not have to write std::whatever

# Functions
Work basically the same as in C
**Member Functions** - functions that are the member of a class
	For these, the name of the class is also part of the function type
```C++
char& String::operator[](int index)
```

# Types, Vars, Arithmetic
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

# Initialization
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


# Scope and Lifetime
- Local scope - exists only in functions
- Class scope - called *member name* if defined in class, exists in class

Any object created by `new` lives until destroyed by `delete`


# Constants (what)
C++ supports tow notions of immutability
`const`- I promise I will never ever ever ever ever ever ever change this
`constexpr` - to be evaluated at compile time. Places data in read only memory
`consteval` - used for when a function should only be evaluated at compile time


# Pointers, Arrays, and References
Pointers work much the same way they do in C

To print the values of an array, you can use this form of loop, a **range-for-statement**
```C++
int v[] = {0,1,2,3,4};

for (auto x: v)
	cout << x << '\n';

for(auto x : {343,4305,3433,343})
	cout << x << 'n';
```
This places a copy from v into x and prints it. If we don't want to copy and just to refer to, use a reference
```C++
for (auto& x: v)
	++x:
```

**<u>References</u>** are similar to pointers, but you don't need * to access the value
- Reference cannot be used to refer to a different object after initialization
They are useful for arguments

If we don't want to modify an argument but also don't want to eat the cost of copying, do this
```C++
double sum(const vector<double>&)
```


# The Null Pointer
We want to ensure a pointer always points to an object so that dereferencing is valid. Use `nullptr`
```C++
double* pd = nullptr;
```
Use nullptr instead of NULL to eliminate potential confusion between integers (like 0 or NULL).

nullptr will be read as false in logic statements


# Tests
Has ifs, switches, whiles, and fors

`cin` input stream
`cout` output stream

for statements can declare variables and test it
```
if (auto n = v.size(); n!=0)

if(auto n = v.size()) // n!=0 is done automatically
```



# Mapping to Hardware
Like C, C++ has direct mapping to hardware operations, making it very fast
###### Assignment
An assignment of a built in type is a simple machine copy operation
```C++
int x = 2;
int y = 3;
x = y
```
x and y are independent from each other

```C++
int* p = &x
int* q = &y
p = q
```
p now refers to q's location in memory


 *** **Assignment to a reference does not change what the reference refers to, but assigns the referenced object**
```C++
int& r = x;
int& r2 = y;
r = r2
```
The actual value of y becomes the value of x in this case

##### Initialization
For assignment to work properly, the assigned to object must have a value
You cannot have unitialized references.
Assigning a variable to a reference type doesn't copy it, it binds to it's location in memory
