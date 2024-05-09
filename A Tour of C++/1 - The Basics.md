`<<` - put to: writes second argument onto it's first
```C++
std::cout << "Hello, world\n";
```
*The string literal is written onto the standard output stream

## Importing
There are two different ways to import libraries
```C++
import std; //new, presents all of the stanard lib as module std

#include <iostream> //works everwhere, includes code directly
```

`using namespace std;` allows you to not have to write std::whatever

## Functions
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
