# Structures
```C++
struct Vector {
	double* elem; //pointer to elements
	int sz;       //number of elements
}
```
A variable of type vector can be defined like this
```C++
Vector v;
```

This isn't useful on it's own, the element pointer doesn't point to anything, so
```C++
void vector_init(Vector& v, int s)
{
	v.elem = new double[s];
	v.sz = s;
}
```
- The & in `Vector&` indicates we pass `v` by non-`const` reference, so the function can modify the struct passed in
- The `new` operator allocates mem from the heap

## Data access
- `.` is used for variables passed by name and references, `->` is used for pointers


# Classes
