TARGET DECK
Modern C::2 - The Principle Structure of a Program


## **Identifiers** #flashcard

- names the C standard gives to certain entities in the program. These refer to data objects, types, functions, constants
<!--ID: 1715966652844-->



### **Type aliases** #flashcard 

- *e.g. size_t* , underscore naming convention used for type identifiers
<!--ID: 1715966570696-->


# Declarations #flashcard 

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
<!--ID: 1715966570701-->


## *EXIT_SUCCESS #flashcard 

comes from standardlib, it allows you to clearly return 0*
<!--ID: 1715966570705-->


## Linux function help #flashcard 

```Terminal
> apropos printf
> man printf
> man 3 printf
```
*These can help with looking up function definitions*
<!--ID: 1715966570709-->


# Definitions #flashcard 

Declarations with initializations defines objects with corresponding names
```C
size_t i = 0;
```
*An object is defined at the same time it is initialized*
<!--ID: 1715966570713-->



