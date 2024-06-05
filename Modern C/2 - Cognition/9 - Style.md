TARGET DECK
Modern C::9 - Style

# Formatting <!--fc-->
Use consistent formatting throughout a project. You can use tools such as `astyle` to automatically ensure proper formatting in larger projects
<!--ID: 1717551823143-->


# Naming <!--fc-->
Choose a consistent naming policy for all identifiers
<!--ID: 1717551823151-->


## Conforming <!--fc--> 
Any identifier that is visible in a header file must be *conforming*
* Names starting with an underscore and a second underscore or capital letter are reserved for ==language extensions== and other internal use
* Names starting with an underscore are reserved for file scope identifiers and for `enum`, `struct`, and `union` tags.
* Macros have all caps names
* All identifiers that have predefined meaning are reserved and cannot be used in file scope (C library functions)
<!--ID: 1717551823156-->


### Avoiding accidentally using reserved names <!--fc--> 
- Expose only types and functions as interfaces that are part of the *application programming interface (API)* - those that are supposed to be used by users of your code
- Use naming prefixes to avoid conflicts: `p99_func`
- give prefixed to `struct` and `union` members
<!--ID: 1717603039214-->


# Type name Use <!--fc--> 
Identify concepts (`enum corvid`)
<!--ID: 1717603039220-->


# Global Constant Use <!--fc--> 
Identify artifacts (pi, `SIZE_MAX`)
<!--ID: 1717603039225-->


# Global Variable Use <!--fc--> 
Identifies state (`toto_intialized` to encode the fact that library `toto` has been initialized)
<!--ID: 1717603039229-->


