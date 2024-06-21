TARGET DECK
Home::A Tour of C++::02 - User Defined Types

# Structures #flashcard 

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
<!--ID: 1715968489569-->


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

## Data access  #flashcard 

- `.` is used for variables passed by name and references, `->` is used for pointers
<!--ID: 1715968489573-->



# Classes #flashcard 

Similar to structs
```C++
class Vector {
public:
	Vector(int s) :elem{new double[s]}, sz{s} {} //initializer list, sets dfault vars
	double& operator[](int i) { return elem[i]; }
	int size() { return sz; }
private:
	double* elem;
	int sz;
}
```
Given this, we can define a variable of our new type `Vector`
```C++
Vector v(6);
```
<!--ID: 1715968489577-->


## Constructors #flashcard 

- A member functions with the same name is called constructor, so `Vector()` replaces `vector_init()`
- You can use an *initializer list* to set default variables of a function
```C++
:elem{new double[s], sz[s]};
```
*This sets `elem` to be a new double array on the heap, and `sz` to the value of `s`*
<!--ID: 1715968489582-->


## Difference between Class and Structs #flashcard 

A class is simply a struct with members private by default, there's no other actual difference
<!--ID: 1715968489586-->



# Enumerations #flashcard 

Similar to C, but accessing the enumerators is different
```C++
enum class Color {red, blue, green };
Color col = Color::red;
```
Used to make code more readable
<!--ID: 1715968489590-->


## Enum Class Limitations #flashcard 

You cannot mix together different enumerator variables, and you can't set the values to `int`
To do this you need to do an explicit conversion
```C++
int x = int(Color::red);
```
<!--ID: 1715968489594-->



Since enumerations are user defined types, we can also define operations for it
```C++
Traffic_light& operator++(Traffic_light& t) // prefix increment: ++
{
	switch (t) {
	case Traffic_light::green: return t=Traffic_light::yellow;
	case Traffic_light::yellow: return t=Traffic_light::red;
	case Traffic_light::red: return t=Traffic_light::green;
	}
}
auto signal = Traffic_light::red;
Traffic_light next = ++signal; // next becomes Traffic_light::green
```

If you don't want to write traffic light all the time
```C++
Traffic_light& operator++(Traffic_light& t) // prefix increment: ++
{
	using enum Traffic_light; // here, we are using Traffic_light
	switch (t) {
	case green: return t=yellow;
	case yellow: return t=red;
	case red: return t=green;
	}
}
```

You could also just use a plain old C `enum` if you want
```C++
enum Color {red,green,blue};
int col = green;
```


# Unions #flashcard 

A unions is a struct in which all members are allocated at the same address so that the union occupies only as much space as the largest member. It can only hold one value at a time
```C++
enum class Type { ptr, num }; // a Type can hold values ptr and num (§2.4)
struct Entry {
	string name; // string is a standard-library type
	Type t;
	Node∗ p; // use p if t==Type::ptr
	int i; // use i if t==Type::num
};
//
void f(Entry∗ pe)
{
	if (pe->t == Type::num)
		cout << pe->i;
// ...
}
```
//
`p` and `i` are never used at the same time, so space is wasted. It can be recovered by specifying that both should be a member of a union
```C++
union Value {
	Node* p;
	int i;
}
```
`Value::p` and `Value::i` are placed at the same address of memory. The language doesn't keep track of what type it's currently set to, so you must keep track
<!--ID: 1715968489599-->



```C++
struct Entry {
	string name;
	Type t;
	Value v; // use v.p if t==Type::ptr; use v.i if t==Type::num
};

void f(Entry∗ pe)
{
	if (pe->t == Type::num)
		cout << pe->v.i;
	// ...
}
```
Keeping track of types with a tag like this (`t`) is error prone. Encapsulate the union and type field in a class and offer access only through member functions that use the unions correctly. This is called a

## Variant #flashcard 

A variant stores a value of one of a set of types, e.g.; `variant<Node*, int>` holds either.
```C++
struct Entry {
	string name;
	variant<Node∗,int> v;
};
void f(Entry∗ pe)
{
	if (holds_alternative<int>(pe->v)) // does *pe hold an int? (see §15.4.1)
		cout << get<int>(pe->v); // get the int
	// ...
}
```
Use these instead of unions to avoid errors
<!--ID: 1715968489604-->
