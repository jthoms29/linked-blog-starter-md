*`size_t` represents values in the range [0, SIZE_MAX]*
The value of `SIZE_MAX` changes depending on platform
It is provided by `stdint.h`

Arithmetic on `size_t` implicitly does the computation %(`SIZE_MAX`+1)
- Wraparound, happens with overflow in unsigned arithmetic
## Ternary/Conditional Operator
Similar to an `if` statement, returns the value of the chosen branch
```C
size_t size_min(size_t a, size_t b) {
	return (a < b) ? a : b;
}
```
