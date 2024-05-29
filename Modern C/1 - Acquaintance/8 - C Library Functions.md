TARGET DECK
Modern C::8 - C Library Functions

# Headers <!--fc-->
Bundles interface descriptions for a number of features, mostly functions
<!--ID: 1716351500290-->


# Error Checking <!--fc-->
C Library functions usually indicate value through a special return value. Generally, you have to look up the specific convention in the manual page for the functions
![[Pasted image 20240519213045.png]]
<!--ID: 1716351500306-->


## `perror` <!--fc-->
A function from `stdio.h`. Used to provide reasoning for error before exiting
<!--ID: 1716351500322-->


# Bounds Checking Interfaces <!--fc-->
Many C lib functions are vulnerable to buffer overflow if called with an inconsistent set of parameters. This is what **bounds checking interfaces** are for
`__STDC_LIB_EXT!__` tells whether this optional interface is supported, and `___STDC_WANT_LIB_EXT1__` switches it on
```C
#if !__STDC_LIB_EXT1__
# error ”This code needs bounds checking interface Annex K”
#endif
#define __STDC_WANT_LIB_EXT1__ 1
//
//
//
#include <stdio.h>
/* Use printf_s from here on. */
```
This must be set before any header files are included
- Bounds checking functions usually use the suffix `_s`, e.g.; `printf_s`
<!--ID: 1716351500340-->


# Platform Preconditions <!--fc-->
Sometimes we need to make assumptions the C compiler may not be able to take care of, for this, we use **preprocessor conditionals**
```C
#if !__STDC_LIB_EXT1__
# error ”This code needs bounds checking interface Annex K”
#endif
```
Missed preconditions for the execution platform abort compilation
- Identifiers that are unknown evaluate to 0
<!--ID: 1716351500357-->


## `static_assert` <!--fc-->
`_Static_assert` (keyword) and `static_assert` (macro from `assert.h`) have a similar effect for preprocessor conditions
```C
#include <assert.h>
static_assert(sizeof(double) == sizeof(long double),
"Extra precision needed for convergence.");
```
<!--ID: 1716351500376-->


# Mathematics <!--fc-->
Mathematical functions come with the `math.h` header, but it is much simpler to use the type generic macros that come with `tgmath.h`. For all functions, it has a macro that dispatches an invocation such as `sin(x)` or `pow(x, n)` to the function that inspects the type of x in its argument and for which the return value is for the same type
<!--ID: 1716429307381-->


## Mathematical functions
*Type generic macros in red, regular functions in green*
![[Pasted image 20240522195220.png]]
![[Pasted image 20240522195304.png]]
![[Pasted image 20240522195344.png]]


# Input, Output, and File Manipulation (`stdio.h`)
From `stdio.h`
`puts` - very basic, outputs a string and an end of line char
`printf` - allows you to format output easily

## Unformatted Text output
There is a function even more basic than `puts`; `putchar`, which outputs a single character
*interfaces*
```C
int putchar(int c);
int puts(char const s[static l]);
```
type `int` as a parameter for `putchar` is a historical accident. 
Having a return type `int` allows the function to return errors to the caller. It returns the argument `c` if successful and a specific negative value `EOF`(end of file) that is guaranteed not to correspond to any character on failure

## Writing to Files <!--fc-->
The type `FILE*` for streams provides an abstraction for writing to permanent storage
`fputs` and `fputc` generalize the idea of unformatted output to streams
```C
int fputc(int c, FILE* stream);
int fputs(char const s[static l], FILE* stream);
```
`FILE*` is a pointer, and you should check if it is null
<!--ID: 1716591573680-->


### Output streams <!--fc-->
Two streams are available for output
- `stdout` - standard output stream, what `putchar` and `puts` use under the hood, linked to terminal
- `stderr` - also linked to terminal, exists to separate 'urgent' output
<!--ID: 1716591573688-->


### Files and Streams

#### Opening files <!--fc-->
If we want to write output to real files, we have to attach the files to our program execution by means of the function `fopen`
```C
FILE* fopen(char const path[static 1], char const mode[static 1]);
FILE* freopen(char const path[static 1], char const mode[static 1],
		FILE *stream);
```
e.g.;
```C
int main(int argc, char* argv[argc+1]) {
	FILE* logfile = fopen(”mylog.txt”, ”a”);
	if (!logfile) {
		perror(”fopen failed”);
		return EXIT_FAILURE;
	}
	fputs(”feeling fine today\n”, logfile);
	return EXIT_SUCCESS;
}
```
This opens a file called `mylog.txt` in the file system and provides access to it through the variable `logfile`.
You should always check for errors when opening files
<!--ID: 1716591573692-->


#### `fopen` modes
![[Pasted image 20240524165654.png]]

### Other interfaces for streams
`freopen` - associate a given stream to a different file and eventually change it's mode
`fclose` - closes the file


## Text IO

#### Buffering <!--fc-->
Output to text stream is usually *buffered*: to make more efficient use of it's resources, to IO system can delay  the physical write to a stream.
If we close the stream with `fclose`, all buffers are guaranteed to be flushed.
<!--ID: 1716669767132-->


### `fflush` <!--fc-->
A function needed in places where we want output immediately to terminal, or where we don't want to close the file but want to ensure all content has been properly written
<!--ID: 1716669767138-->


## Manipulating Files in System <!--fc-->
The C library has limited support for manipulating files within the file system. They do what their names indicate
```C
int remove(char const pathname[static 1]);
int rename(char const oldpath[static 1], char const newpath[static 1]);
```
<!--ID: 1716669767143-->


## Formatted Output
You can use `printf` for formatted output.
`fprintf` is very similar, but it has an additional parameter that allows us to specify the stream to which the output is written
```C
int printf(char const format[static 1], ...);
int fprintf(FILE* stream, char const format[static 1], ...);
```
The syntax with the three dots indicates that these functions may receive an arbitrary number of items that are to be printed. These must correspond exactly to the `%` specifiers, or the behavior is undefined

### `printf` specifiers
![[Pasted image 20240526134256.png]]
![[Pasted image 20240526134340.png]]


## Unformatted Text Input <!--fc-->
Unformatted input is best done with `fgetc` for a single character and `fgets` for a string
```C
int fgetc(FILE* stream);
char* fgets(char s[restrict], int n, FILE* restrict stream);
int getchar(void);
```
<!--ID: 1716828452109-->



## End of File <!--fc-->
`fgetc` returns an int signifying  `EOF`. In order to conclude we are at the end of a stream, we have to call `feof`
<!--ID: 1716828452118-->


# String Processing and Conversion

## `ctype.h`
This library provides functions and macros that deal with the most commonly used glasses. These work on characters, and for historical reason take and return `int`
![[Pasted image 20240527105552.png]]

## Conversion of strings to numerical values <!--fc-->
### `stdlib.h`
 `strtod` - to double
 `strtoul` - unsinged long
 `strtol` - long
 `stroumax` - uintmax_t
 `strtoimax`- intmax_t
 `strtoull` - unsigned long long
 `strtoll` - long long
 `strtold` - long double
 `strtof` - float
<!--ID: 1716829837015-->



# Time <!--fc-->
Functional interfaces that deal with time are provided by the `time_t` header
<!--ID: 1716834989125-->


```C
time_t time(time_t *t); // <!--fc-->
```
provides a timestamp of type `time_t` of the current time
<!--ID: 1716834989141-->


```C
double difftime(time_t time1, time_t time0); // <!--fc-->
```
gets the difference between two times
<!--ID: 1716834989146-->


## `struct tm` <!--fc-->
`struct tm` structures a calendar time
`tm_mon` - set to 0 = January
`tm_wday` - set to 0 = Sunday
`tm_mday` - starts counting days of the month at 1
`tm_year` - must add 1900 to get the year in the Gregorian calendar
`tm_sec` - range from 0 to 60 inclusive. The latter is for leap seconds whatever that is
<!--ID: 1716846026456-->


Three supplemental date members are used to supply add additional info
`tm_wday` for the weekday
`tm_yday` for the day in the year
`tm_isdst` a flag that informs us whether a date is considered to be in DST for the local time zone

### `mktime` <!--fc-->
A function used to enforce consistency of `struct tm` members
It works in three steps:
- The hierarchical date members are normalized to their respective ranges
- `tm_wday` and `tm_yday` are set to the corresponding values
- If `tm_isday` has a negative value, the value is modified to 1 if the date falls into DST for the local value, or to 0 otherwise
- It also returns the time as `time_t`
<!--ID: 1716846026472-->


### other tm operations
`localtime_s` stores the broken-down local time
`gmtime_s` stores the broken time, expressed as universal time UTC

### Textual representation of calendar time <!--fc-->
`asctime_s` stores the date in a fixed format in English
	"Www Mmm DD HH:MM:SS YYYY\n"
`strftime` is more flexible and allows us to compose a textual representation with specifiers
<!--ID: 1716846026476-->


![[Pasted image 20240527153621.png]]
![[Pasted image 20240527153653.png]]


## More Precise Time <!--fc-->
`time_t` only has a granularity of seconds. If we need more than that, `struct timespec` and the `timespec_get` function can be used. With that, we have an additional member `tv_nsec` that provides nanosecond precision
<!--ID: 1716846026481-->


## CPU time <!--fc-->
`clock_t clock(void)` gives the processer time in `CLOCKS_PER_SEC` units per second
<!--ID: 1716846026485-->



# Runtime Environment Settings <!--fc-->
A C program can access an environment list: a list of name-value pairs of strings (often called environment variables) that can transmit specific information form the runtime environment 
<!--ID: 1716955192733-->


## `getenv()` <!--fc-->
A function that allows to transmit specific info from the runtime environment
```C
char* getenv(char const name[static l]);
```
Which environment variables are available depends heavily on the operating systems. Common ones are
`"HOME"` - user's home directory
`"PATH` - the collection of standard paths to executables
`"LANG"` or `"LC_ALL"` - language setting
<!--ID: 1716955192738-->


## Locale <!--fc-->
The language or locale setting is another important part of the execution environment that a program execution inherits. A startup, C forces the value to be the "C" locale. It has American English choices for numbers or times or dates
<!--ID: 1716955192743-->


### `setlocale` <!--fc-->
A function form `locale.h`, can be used to set or inspect the current locale value
```C
char* setlocale(int category, char const locale[static 1]);
```
In addition to the "C" locale, you can also use "", an empty string which sets the locale to the systems default.
The `category` argument can be used to address all or only parts of the language environment
![[Pasted image 20240528214811.png]]
<!--ID: 1716955192747-->


# Program Termination and Assertions
Using the `exit` function in main is really stupid, so don't do that.

## Cleanup at termination <!--fc-->
There is a mechanism called *handlers* that will do things like flush and close files that are written or free resources used by the programs
```C
int atexit(void func(void));
int at_quick_exit(void func(void));
```
These take function parameters
e.g.:
```C
void sayGoodBye(void) {
	if (errno) perror(”terminating with error condition”);
	fputs(”Good Bye\n”, stderr);
}
//
int main(int argc, char* argv[argc+1]) {
	atexit(sayGoodBye);
	...
}
```
This uses `atexit` to establish the exit handler `sayGoodBye`
<!--ID: 1716955192751-->


## Other Exit functions <!--fc-->
The C library has three other functions that terminate program execution, in order of severity
```C
_Noreturn void quick_exit(int status);
_Noreturn void _Exit(int status);
_Noreturn void abort(void);
```
`quick_exit` can be used to establish alternate termination handlers
`_Exit` inhibits these application specific handlers, only doing platform specific cleanups like file closures.
<!--ID: 1716955192755-->


## Runtime Assertions <!--fc-->
From `assert.h`
While `_Static_assert` and `static_assert` can make compiler time assertions, 
`assert` and `NDEBUG` can be used for runtime assertions
`assert` - used to test for an expression that must hold at a specific moment
`NDEBUG` - if not defined during compilation, every time it's called the expression is evaluated
<!--ID: 1716955192759-->
