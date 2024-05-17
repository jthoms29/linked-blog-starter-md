TARGET DECK
A Tour of C++::1 - The Basics

# Writing To #flashcard 

`<<` - put to: writes second argument onto it's first
```C++
std::cout << "Hello, world\n";
```
*The string literal is written onto the standard output stream
<!--ID: 1715968024249-->


# Importing #flashcard

There are two different ways to import libraries
```C++
import std; //new, presents all of the stanard lib as module std
//
//
#include <iostream> //works everwhere, includes code directly
```
<!--ID: 1715968024253-->


# Namespace Trick #flashcard 

`using namespace std;` allows you to not have to write std::whatever
<!--ID: 1715968024257-->


# Functions #flashcard 

Work basically the same as in C
<!--ID: 1715968024261-->


## **Member Functions** #flashcard 

- functions that are the member of a class
	For these, the name of the class is also part of the function type
```C++
char& String::operator[](int index)
```
<!--ID: 1715968024265-->



# Types, Vars, Arithmetic

## **Declarations** #flashcard

- a statement that introduces an entity to a program and specifies its type
``int inch;``
<!--ID: 1715968024269-->



![[Pasted image 20240508165033.png]]

`sizeof(x);` #flashcard

- use this operator to get the size of a datatype on a specific machine, helps with portability
<!--ID: 1715968024273-->


## Hex and Octal #flashcard 

```C++
0x34903 // hexidecimal
0343    // octal
//
3.1434'343'434343'34343 //single quotes can be used in literals for readability
```
<!--ID: 1715968024277-->



## Auto Conversions #flashcard 

In assignments and in arithmetic operations, C++ performs all meaningful conversions between the basic types so they can be mixed freely
```C++
void func() {
	double d = 2.2 //float
	int i = 7;     //integer
	d = d+i;       //assigned to float
	i = d+i;       //assinged to int
}
```
<!--ID: 1715968024281-->


# Initialization #flashcard 

C++ offers a variety of notations for expressing initialization
```C++
int i1 = 7.8  //i1 becomes 7
int i2{7.8}   //error: floating point to integer conversion
```
In general, you should use the second way (**<u>delimited initializer lists</u>**).
<!--ID: 1715968024285-->



## **Auto** #flashcard 

You can use auto to have the type be deduced from the initializer
```C++
auto d = 1.2 //double
auto z = sqrt(y) //whatever sqrt returns
auto bb{true} //bool
```
With this, we tend to you = because there is no potentially troublesome type conversion.
We use auto when we don't have a specific reason to type specifically
<!--ID: 1715968024289-->



# Scope and Lifetime

## - Local scope #flashcard

- exists only in functions
<!--ID: 1715968024293-->


## - Class scope #flashcard

- called *member name* if defined in class, exists in class
<!--ID: 1715968024302-->


## `new` #flashcard 

Any object created by `new` lives until destroyed by `delete`
<!--ID: 1715968024309-->



# Constants (what)
C++ supports two notions of immutability

## `const` #flashcard 

- I promise I will never ever ever ever ever ever ever change this
<!--ID: 1715968024315-->


## `constexpr` #flashcard 

- to be evaluated at compile time. Places data in read only memory
<!--ID: 1715968024321-->


## `consteval` #flashcard 

- used for when a function should only be evaluated at compile time
<!--ID: 1715968024325-->



# Pointers, Arrays, and References
Pointers work much the same way they do in C

## Range For Statement #flashcard 

To print the values of an array, you can use this form of loop, a **range-for-statement**
```C++
int v[] = {0,1,2,3,4};
//
for (auto x: v)
	cout << x << '\n';
//
for(auto x : {343,4305,3433,343})
	cout << x << 'n';
```
This places a copy from v into x and prints it. If we don't want to copy and just to refer to, use a reference
```C++
for (auto& x: v)
	++x:
```
<!--ID: 1715968024330-->


## References #flashcard 

**<u>References</u>** are similar to pointers, but you don't need * to access the value
- Reference cannot be used to refer to a different object after initialization
- They are useful for arguments
If we don't want to modify an argument but also don't want to eat the cost of copying, do this
```C++
double sum(const vector<double>&)
```
<!--ID: 1715968024334-->



# The Null Pointer #flashcard 

We want to ensure a pointer always points to an object so that dereferencing is valid. Use `nullptr`
```C++
double* pd = nullptr;
```
Use nullptr instead of NULL to eliminate potential confusion between integers (like 0 or NULL).
nullptr will be read as false in logic statements
<!--ID: 1715968024338-->



# Tests
Has ifs, switches, whiles, and fors

## `cin` #flashcard 

input stream
<!--ID: 1715968024347-->


## `cout` #flashcard 

output stream
<!--ID: 1715968024354-->


# For Statement Declarations #flashcard 

for statements can declare variables and test it
```
if (auto n = v.size(); n!=0)
//
if(auto n = v.size()) // n!=0 is done automatically
```
<!--ID: 1715968024360-->




# Mapping to Hardware
Like C, C++ has direct mapping to hardware operations, making it very fast
###### Assignment #flashcard 

An assignment of a built in type is a simple machine copy operation
```C++
int x = 2;
int y = 3;
x = y
```
x and y are independent from each other
<!--ID: 1715968024365-->


## Pointer Assignment #flashcard 

```C++
int* p = &x
int* q = &y
p = q
```
p now refers to q's location in memory
<!--ID: 1715968024370-->


## Reference Assignment #flashcard 

 *** **Assignment to a reference does not change what the reference refers to, but assigns the referenced object**
```C++
int& r = x;
int& r2 = y;
r = r2
```
The actual value of y becomes the value of x in this case
<!--ID: 1715968024374-->


##### Reference Initialization #flashcard

For assignment to work properly, the assigned to object must have a value
You cannot have unutilized references.
Assigning a variable to a reference type doesn't copy it, it binds to it's location in memory
<!--ID: 1715968024380-->


