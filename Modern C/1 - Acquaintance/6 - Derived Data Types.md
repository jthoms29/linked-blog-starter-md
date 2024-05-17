TARGET DECK
Modern C::6 - Derived Data Types

# Arrays 
*Arrays are not pointers*


**Array declaration:** #flashcard
```C
double a[4];
signed b[N];
```
The type that composes an array may itself be an array, forming a *multidimensional array*
```C
double C[M][N];
double (D[M]) [N];
```
<!--ID: 1715965219895-->

## Array operations #flashcard

- An array in a condition evaluates to `true`
- There are array objects but no array values
		Arrays cannot be operands for operators themselves, and there's no arithmetic declared on arrays themselves
- Arrays can't be compared
- Arrays can't be assigned to
<!--ID: 1715965219900-->

## Array length #flashcard
There are two categories of arrays
- *fixed length arrays*
- *variable length arrays*
VLAs can't have initializers and can't be declared outside of functions
- Any array with a length that is not an integer constant expression is a VLA
<!--ID: 1715965219905-->


**You can compute an array's length with** #flashcard

```C
size_t ar_size = sizeof(A) / sizeof(*A)
```
<!--ID: 1715965219909-->

## Arrays as parameters #flashcard 

- The innermost dimension of an array parameter to a function is lost
- Don't use the `sizeof` operator an array parameters in functions
Array parameters behave as if the array is passed by reference, so an array parameter will modify the array
```C
void swap_double(double a[static 2]) {
	double tmp = a[0];
	a[0] = a[1];
	a[1] = tmp;
}
```
<!--ID: 1715965219913-->

## Strings #flashcard 

An array of character terminated by `'\0'`
<!--ID: 1715965219917-->


To deal with strings, use functions from the header `string.h`.
- those that just require an array arg start with `mem`
- those require additional args start with `str`

### Functions that operate on `char` arrays #flashcard 

- `memcpy(target, source, len)` - can be used to copy one array to another
- `memcmp(s0, s1, len)` - compares two arrays in lexicographic order. If there's not difference, 0 is returned
- `memchr(s, c, len)` - searches array `s` for appearance of character 'c'
<!--ID: 1715965219922-->

### Functions that operated on strings #flashcard 

- `strlen(s)` - returns the length of string 's'
- `strcpy(target, source)` - target must be big enough to hold copy
- `strcmp(s0, s1)`- compares two strings in lexicographic order
- `strcoll(s0, s1)` - compares two strings in lexicographic order while respecting specific environment settings
- `strchr(s, c)` - similar to `memchr`, but only the string `s` must be null terminated
- `strspn(s0, s1)` - returns the length of the initial segment in `s0` that consists of characters that also appear in `s1`
- `strcspn(s0, s1)` - returns the length of the initial segment ins `s0` that consists of characters that do not appear in `s1`
<!--ID: 1715965219926-->


When to use mem or str functions #flashcard 

If a character array is not known to be null terminated, it's better to use `mem` functions
<!--ID: 1715965219930-->

## Pointers #flashcard 

![[Pasted image 20240515180309.png]]
Pointers are opaque types, the binary representation of them is up to the platform and not our business
<!--ID: 1715965219935-->


**Initializing pointers** #flashcard 

initialization or assignment with 0 makes pointers null/`false`
```C
char const*const p2nothing = 0;
```
Always initialize pointers. Uninitialized pointers can lead to undefined behavior
<!--ID: 1715965219939-->

# Structures #flashcard 

A struct can hold data of differing types
```C
struct birdStruct { //declaration of a new type
	char const* jay; 
	char const* magpie; 
	char const* raven; 
	char const* chough; 
};
struct birdStruct const aName = { //variable of new type
	.chough = ”Henry”,
	.raven = ”Lissy”,
	.magpie = ”Frau”,
	.jay = ”Joe”,
}
```
Since these are pointers, the struct doesn't contain the strings themselves
<!--ID: 1715965219943-->

## Example: Calendar Time
```C
typedef int calArray[9];

struct tm {
	int tm_sec; // Seconds after the minute [0, 60]
	int tm_min; // Minutes after the hour [0, 59]
	int tm_hour; // Hours since midnight [0, 23]
	int tm_mday; // Day of the month [1, 31]
	int tm_mon; // Months since January [0, 11]
	int tm_year; // Years since 1900
	int tm_wday; // Days since Sunday [0, 6]
	int tm_yday; // Days since January [0, 365]
	int tm_isdst;// Daylight Saving Time flag
};

struct tm today = {
	.tm_year = 2019-1900,
	.tm_mon = 4-1,
	.tm_mday = 3,
	.tm_hour = 10,
	.tm_min = 0,
	.tm_sec = 47,
}; //the actual tm is a part of time.h
```

![[Pasted image 20240516110757.png]]

**Initializing structs** #flashcard 

- Omitted struct initializers force the corresponding member to 0, and a struct initializer must initialize at least one member
<!--ID: 1715965219948-->

# Type Aliases #flashcard 


There's a general tool you can use for structs to make them cleaner, using `typedef`
```C
typedef struct birdStruct Birdstructure;
```
then you can just use birdstructure
<!--ID: 1715965219952-->



