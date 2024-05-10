
- **Identifiers** - names the C standard gives to certain entities in the program. These refer to data objects, types, functions, constants
	- **Type aliases** - *e.g. size_t* , underscore naming convention used for type identifiers

# Declarations
Specifies what an identifier is supposed to represent. All identifiers must be declared, this is how they differ from keywords

```C
int main(void){
	size_t i;
	double A[5];
}
```
i is of type size_t
main is a function of type int
A declares an array

*EXIT_SUCCESS comes from standardlib, it allows you to clearly return 0*

```Terminal
> apropos printf
> man printf
> man 3 printf
```
*These can help with looking up function definitions*

# Definitions
Declarations with initializations defines objects with corresponding names

```C
size_t i = 0;
```
*An object is defined at the same time it is initialized*


