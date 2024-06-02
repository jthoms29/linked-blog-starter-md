TARGET DECK
A Tour of C++::4 - Error Handling

# Exceptions <!--fc-->
If there is some kind of foreseeable error that we want to be able to recover from, we should detect the error and throw an *exception*
```C++
double& Vector::operator[](int i)
{
	if(!(0<i && i<size()))
		throw out_of_range{"Vector::operator[]"};
	return elem[i];
}
```
The `throw` transfers control to a handler of exceptions of type `out_of_range` in some function that calls `Vector::operator[]()`
<!--ID: 1717345050011-->


## Try Block <!--fc-->
```C++
void f(Vector& v)
{
	// ...
	try { // out_of_range exceptions thrown in this block are handled by the handler defined below
		compute1(v); // might try to access beyond the end of v
		Vector v2 = compute2(v); // might try to access beyond the end of v
		compute3(v2); // might try to access beyond the end of v2
	}
	catch (const out_of_range& err) { // oops: out_of_range error
		// ... handle range error ...
		cerr << err.what() << '\n';
	}
	// ...
}
```
We put code for which we are interested in handling exceptions into a try block
The catch clause is provided to handle the exceptions of type `out_of_range`
<!--ID: 1717345050015-->


## Exception Definitions <!--fc-->
found in `<stdexcept>`
<!--ID: 1717345050020-->


# Invariants <!--fc-->
A statement of what is assumed to be true for a class is called a *class invariant* or simply an *invariant*. It is the job of a constructor to establish the invariant for its class and for the member functions to make sure the invariant holds when they exit using exceptions
```C++
Vector::Vector(int s)
{
	if (s<0)
		throw length_error{"Vector constructor: negative size"};
	elem = new double[s];
	sz = s;
}
```
<!--ID: 1717345050025-->


# Error Handling Alternatives

## returning a value indicating failure <!--fc-->
We do this when failure is normal and expected, like opening a file. Exception should be called when failure is more rare
<!--ID: 1717345050029-->


## terminating the program by invoking a function like `exit()` <!--fc-->
We do this when error is so bad we can not recover from it. One way to ensure this happens is to add `noexcept` to a function so that any `throw` will turn into a `terminate`
<!--ID: 1717345050033-->


# Assertions <!--fc-->
A mechanism for debugging that is ignored during standard use
<!--ID: 1717356873401-->


## `assert()` <!--fc-->
The standard library offers the debug macro `assert()`, to assert that a condition must hold at runtime
```C++
void f(const char* p)
{
	assert(p!=nullptr);
}
```
If the condition of the assert fails in debug mode, the program terminates. If not in debug mode, the `assert` is not checked
<!--ID: 1717356873407-->


## Static Assertions <!--fc-->
A way to perform simple checks on most properties during compile time and report failures as compiler error messages
```C++
static_assert(4<=sizeof(int), "integers are too small");
```
will write `integers are too small` if `4<=sizeof(int)` doesn't hold
This can be used for anything that can be expressed in terms of constant expressions
<!--ID: 1717356873412-->


## `noexcept` <!--fc-->
A function that should never throw an exception can be declared `noexcept`
```C++
void user(int sz) noexcept
{
	Vector v(sz);
	iota(&v[0],&v[sz],1); // fill v with 1,2,3,4... (see §17.3)
	// ...
	}
```
<!--ID: 1717356873416-->
