- For conditional statements, 0 is false, anything else is true
# Bool Type
specified in `stdbool.h`
Though false is another name for 0 and true for 1, it's important to use these to emphasize that a value is interpreted as a condition

**Don't ever compare 0, false, or true. You don't need to

# Scalar Types
![[Pasted image 20240508144254.png]]

# Iterations
Do loop
```C
do {
	x *= 2.0;
} while (x < 45.0);
```

`break` - stops the loop without reevaluating the termination condition
`for(;;)` gives you an infinite loop, you can use the break statement inside

`continue` - skips the execution of the rest of the dependent block but continues the loop

# Multiple Selection
Switch statements
```C
if (arg) {
case 'm' : puts("this is a magpie");
           break;
case 'r' : puts("this is a raven");
	       break;
default: puts("this is an unknown corved");
}
```
*No break statement causes fall through, like multiple ifs*

Case values must be integer constant expressions





