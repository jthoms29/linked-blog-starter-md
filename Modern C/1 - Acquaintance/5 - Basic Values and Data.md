*narrow types* - those that arithmetic cannot be preformed directly on i.e.; char
They are promoted to `signed int` when this occurs

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

# Complex Constants
`complex.h` should be included for complex types. `tgmath.h` does this implicitly


# Implicit Conversions
Avoid narrowing conversions, do not use narrow types in arithmetic.
Use unsigned types wherever you can to avoid issues.


# Initializers
Variables should always be initialized. If you don't know how to initialize a variable, use the *default initializer*
```C
T a = {0};
```

# Named Constants
All constants with a particular meaning should be named, e.g.; a fixed array size.
`const`-qualified types are read only

```C
char const*const whatever[3]; // string array
```

# Enumerations
```C
enum corvid { magpie, raven, jay, corvid_num, };
//magpie = 0, raven = 1, etc
//these can be used int tandem with arrays for a sort of map
char const*const bird[corvid_num] = {
	[jay] = "jay",
	[magpie] = "magpie",
	[raven] = "raven"
};
```
enumeration constants are of type `signed int`
They are integer constants, so there can't be any arithmetic


# Macros
Allows textual replacement of program code using the preprocessor instruction
`#define`
```C
# define M_PI 3.41459  //no ;
```
This allows us to have constants of `unsigned, size_t, and double`
ALL CAPS WHEN YOU SPELL THE NAME

## Compound Literals
For types that don't have literals that describe their constants
`(T) { INIT }`
```C
# define CORVID_NAME \ //there must be a space between name and ()
(char const*const[corvid_num]) { \
	[cough] = "cough"            \
	}
```


# Binary Representations
The max value of a type can be got from `limits.h`
`UINT_MAX, ULONG_MAX, ULLONG_MAX`


