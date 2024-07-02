TARGET DECK
Home::Modern C::10 - Organization and Documentation

# Interface Documentation <!--fc-->
C has no 'built in' documentation standard like Java, but in recent years a cross platform tool called **doxygen** has become widely adopted.
*Example:*
![[Pasted image 20240701125641.png]]
![[Pasted image 20240701125701.png]]
<!--ID: 1719877534394-->


## Doxygen Syntax <!--fc-->
- @ - starts keywords
- features markup capacity
<!--ID: 1719877534409-->


## Structuring headers <!--fc-->
It's good practice to group all functions that treat a specific data type in one header file.
For example:
`brian.h` for `struct brian` would look like this
![[Pasted image 20240701153455.png]]
![[Pasted image 20240701153506.png]]
<!--ID: 1719877534419-->


# Implementation
It should be clear what a program is doing for the most part without the overuse of comments.

## Good control flow practice <!--fc-->
**Control flow must be obvious**
Avoid:
- *Buried Jumps*: `break`, `continue`, `return` and `goto` statements that are buried in a complicated nested structure of `if` or `switch` statements.
- *Flyspeck expressions*: Controlling expressions that combine a lot of operators in an unusual way, e.g.: `!!++*p--`
<!--ID: 1719877534427-->


## Macros
