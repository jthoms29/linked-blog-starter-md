TARGET DECK
Modern C::4 - Expressing Computations

**Size_t** #flashcard 

*`size_t` represents values in the range [0, SIZE_MAX]*
The value of `SIZE_MAX` changes depending on platform
It is provided by `stdint.h`
<!--ID: 1715965923480-->


**Wraparound** #flashcard 

Arithmetic on `size_t` implicitly does the computation %(`SIZE_MAX`+1)
- Wraparound, happens with overflow in unsigned arithmetic
<!--ID: 1715965923485-->


# Ternary/Conditional Operator #flashcard 

Similar to an `if` statement, returns the value of the chosen branch
```C
size_t size_min(size_t a, size_t b) {
	return (a < b) ? a : b;
}
```
<!--ID: 1715965923489-->

