# Macros defined in stdlib.h
`EXIT_SUCCESS`/`EXIT_FAILURE

# Switch
```C
switch (arg) {
case 'm' : puts("this is a magpie");
           break;
case 'r' : puts("this is a raven");
	       break;
default: puts("this is an unknown corved");
}
```
*No break statement causes fall through, like multiple ifs*

# Ternary/Conditional Operator
Similar to an `if` statement, returns the value of the chosen branch
```C
size_t size_min(size_t a, size_t b) {
	return (a < b) ? a : b;
}
```

# Datatypes
- Use `size_t` for sizes, cardinalities, so you don't have to worry about unsigned issues on different systems
- use `unsigned` for small quantities that can't be negative
- use `signed` for small quantities that bear a sign
- use `ptrdiff_t` for large differences that bear a sign
- use `double` for floating point calculations
- use `double complex` for complex calculations

# Time
`time_t` and `clock_t` are used to handle times
`difftime()` - compares difference in timestamps, can be used in arithmetic
`CLOCKS_PER_SEC` can convert `clock_t` values to seconds