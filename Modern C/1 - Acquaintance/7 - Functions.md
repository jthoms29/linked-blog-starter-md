TARGET DECK
Modern C::7 - Functions

# Main Function
## Two ways of implementing main() <!--fc-->

```C
int main(void);
int main(int argc, char* argv[argc+1]);
```
The second allows command line arguments
<!--ID: 1716144476186-->


## Returning from main <!--fc-->

You should always use the macros
`EXIT_SUCCESS` or `EXIT_FAILURE` defined in `stdlib.h`
<!--ID: 1716144476194-->


## The exit() function <!--fc-->

The library function `exit` terminates the program
```C
_Noreturn void exit (int status);
```
It terminates the program exactly as a `return` from `main` would. The `status` parameter has the role the return expression of main will have
<!--ID: 1716152586931-->



