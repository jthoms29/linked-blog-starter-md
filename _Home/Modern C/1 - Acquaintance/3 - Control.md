TARGET DECK
Home::Modern C::03 - Control

**What is true/false** #flashcard 
- For conditional statements, 0 is false, anything else is true
<!--ID: 1715966183359-->


# Bool Type #flashcard 
specified in `stdbool.h`
Though false is another name for 0 and true for 1, it's important to use these to emphasize that a value is interpreted as a condition.
**Don't ever compare 0, false, or true. You don't need to
<!--ID: 1715966183364-->


# Scalar Types
![[Pasted image 20240508144254.png]]

# Iterations

Do loop #flashcard 

```C
do {
	x *= 2.0;
} while (x < 45.0);
```
<!--ID: 1715966183368-->


## `break` #flashcard 

- stops the loop without reevaluating the termination condition
<!--ID: 1715966183372-->


## `for(;;)` #flashcard 

gives you an infinite loop, you can use the break statement inside
<!--ID: 1715966183377-->


## `continue` #flashcard 

- skips the execution of the rest of the dependent block but continues the loop
<!--ID: 1715966183382-->


# Multiple Selection

## Switch statements #flashcard 

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
**Case values must be integer constant expressions**
<!--ID: 1715966183386-->






