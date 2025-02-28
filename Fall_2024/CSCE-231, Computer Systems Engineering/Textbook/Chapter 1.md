<mark style="background: #ADCCFFA6;">Leaky abstraction</mark> is used to describe the phenomenon of the hardware's physical limitations intruding into software's behavior

## Boolean Algebra
<mark style="background: #ADCCFFA6;">Boolean algebra</mark>, the same thing as Boolean logic.

Propositions are functions that map <mark style="background: #ADCCFFA6;">literals</mark> (Boolean variables' values or their complements) to another value. The literal operands are the input and the value of the function is the output
Truth tables will happen

### Operations
The NOT operation is depicted with a tailed dash in propositional logic. In Boolean algebra, use either a overscore or a tick mark after the p.
The OR operation is depicted with V in logic and + in algebra. Remember that 1 dominates 0 (yes dominates no)
AND in logic is ^ and in Boolean algebra it's a dot between them, or with no symbol and they're just right next to each other when no ambiguity is possible. 0 dominates 1
XOR also exists. In propositional logic it's a circle inscribed with a + and sometimes an underscored V, in algebra it's always the circled plus sign
![[Pasted image 20240829111554.png]]

### Normal Forms
A <mark style="background: #ADCCFFA6;">sum of products</mark> (also known as a disjunctive normal form) is a series of <mark style="background: #ADCCFFA6;">minterms</mark> (Boolean literals joined by ANDs) , and all of the minterms are joined by ORs
	(a & b) + (t & s)

A <mark style="background: #ADCCFFA6;">product of sums</mark> (conjunctive normal form) is a series of <mark style="background: #ADCCFFA6;">maxterms</mark> (Boolean literals joined by ORs) which are joined by ANDs

A <mark style="background: #ADCCFFA6;">Karnaugh Map</mark> is a two-dimensional view of a truth table. Each input gets its own axis. Basically a Punnett Square. Below is the map of p + q
![[Pasted image 20240829113259.png]]
The map for the below truth table as well:
![[Pasted image 20240829113410.png]]
![[Pasted image 20240829113422.png]]

When there is more than one input on an axis in a map, you have to map out the combinations using a <mark style="background: #ADCCFFA6;">Gray code</mark>, which is an arrangement in which adjacent combinations differ in exactly one bit (Table 1.8). Notice that the first two columns both have the q literal; they differ only in p vs overscore p
![[Pasted image 20240829113742.png]]
The cells must contain only a power of two number of cells

<mark style="background: #BBFABBA6;">Note that when an x is in a Karnaugh map, it mean's you don't care. The value could be 0 or 1 and it would change nothing</mark>

## C In a Hexnut Shell
### Compiler
We will be using gcc
![[Pasted image 20240829114505.png]]

When debugging, fix only the first problem reported, ignore the rest, and recompile
![[Pasted image 20240829114744.png]]

###  Coding Basics
`#include <file>` will include a header file in the standard header files location (usually usr/include directory)
`#include "file"` will look for a header file in the current directory

### Compiler Optimizations
![[Pasted image 20240829115111.png]]

### Basic Types
```C
enum days {
    MONDAY,
    TUESDAY,
    WEDNESDAY,
    THURSDAY,
    FRIDAY,
    SATURDAY,
    SUNDAY
};

enum days day = WEDNESDAY;
```
Enum values are also mapped to an integer value

Booleans don't really exist for our purposes. 0 is false and 1 is true, use an int

### Pointers
A <mark style="background: #ADCCFFA6;">pointer</mark> is a variable that contains a memory address. When declaring a pointer, you use an asterisk to indicate that you are declaring a pointer and not some other type
`int *p;` makes a point

To <mark style="background: #ADCCFFA6;">dereference</mark> a pointer (to use the value it points to), you put an asterisk before an operation you're using it in
`*p = ...;` changes the value of a pointer and
`p = ...;` changes the address it points to
	NOTE: you can use `if (p == 0)` to check to see if something is a <mark style="background: #ADCCFFA6;">null pointer</mark>

<mark style="background: #BBFABBA6;">The key difference is that declaring pointers happens around variable declaration and dereferencing happens everywhere else</mark>. Remember white space doesn't exist so don't get confused by it being on the int* or something

You can use ampersand to obtain a memory address from a pointer. It will return where it's stored
`a = &b` will assign the address of b to the pointer a (assuming it was declared a pointer earlier)

Function return or declaration types can also be pointers. For example, `void*` indicates a pointer to an arbitrary type (any pointer); this can be any return type or any parameter
	NOTE: If it's a return type, you must explicitly <mark style="background: #ADCCFFA6;">cast</mark> the returned pointer to the type of the pointer variable you're assigning the memory address too

<mark style="background: #ADCCFFA6;">Pointer arithmetic</mark> is how arithmetic operations affect the memory addresses stored in pointers. For example, adding + 1 to a pointer will NOT change the address by one byte as you might expect, but <mark style="background: #BBFABBA6;">it will change the address by the number of bytes of the type it points to.</mark>
	For example, floats occupy 4 bytes. If you do + 1 to a float, its memory address will increase by 4. If you did + 2, it would increase by 2 * 4, so 8

### Derived Types
<mark style="background: #ADCCFFA6;">Arrays</mark> in C function very similar to arrays in Java, there just isn't a length property. Initialized the same way as Java, both with size and with direct initialization. An array is a pointer inherently; each point in an array is a memory address

A <mark style="background: #ADCCFFA6;">string</mark> is an array of characters that ends with \0 (ASCII NUL character)

C does not have classes, but they do have <mark style="background: #ADCCFFA6;">structures</mark>, which is just like a class but it can only have public fields and no methods
```C
struct hat {
	int size;
	char *color;
};

struct hat h1, h2;
```
You can also use typedef so you don't have to put struct in front
```C
typedef struct {
	int pips;
	char suit;
} card;

card c1,c2;
```
<mark style="background: #BBFABBA6;">If it is a non-pointer, you use .'s to access struct members. If it is a pointer, you use -> to access a struct's members</mark>

It is very common to create pointers to structures. If you just kept making structures, you'd be copying the same code over and over again which gets inefficient

The <mark style="background: #ADCCFFA6;">union</mark> is very similar to a structure. The difference is that all of a union's members share the same memory address. If you change the union coin's year, it will also change value (more in Chapt 3 and 4)
```C
union coin {
	long year;
	double value;
};
```

### Defined Types
<mark style="background: #ADCCFFA6;">typedef</mark> is kinda like var in C# mixed with creating an object type in Java. You define a type (usually of an enum or struct base type) and than you can just use that type word to make the same struct/enum
```C
typedef enum {CLUBS, DIAMONDS, HEARTS, SPADES} suits;
typedef struct {
    int value;
    suits suit;
} card;
card c = {.value=3, .suit=DIAMONDS};
```

### # define
With the <mark style="background: #ADCCFFA6;">#define</mark> preprocessing directive, you can introduce text substitution. You can create macros by including arguments. It is not recommended as it makes it difficult to debug mistakes. <mark style="background: #BBFABBA6;">You should use define to declare constants instead</mark>
`#define PI 3.14159`

### Memory
If you don't know how much memory you need for an array or other until run time, or for any other reason, the <mark style="background: #ADCCFFA6;">malloc()</mark> function will work. It takes a single argument, the number of bytes you need allocated, and it returns a pointer to the allocated memory
`char *foo = (char *)malloc(256);` allocates 256 bytes

If you're using a linked list, you could have code that looks like:
`this_node->next = (struct node *)malloc(sizeof(struct node));`

If you're using an array, the <mark style="background: #ADCCFFA6;">calloc()</mark> function is available as a convenience. The first parameter is the number of elements in the array, and the second is the size of an element
`int *bar = (int *)calloc(32, sizeof(int))`
	NOTE: malloc but just 32 * sizeof(int) would not initialize memory

To use either of these you need to use stdlib.h

NOTE: C does NOT have a garbage collector. Careful of memory leaks

### Function Pointers
A <mark style="background: #ADCCFFA6;">function pointer</mark> contains the address of a function. More in chapt 9. It is used to provide flexible behavior. Declared with an asterisk and parentheses to bind the asterick to the function and not to the return type
`int (*func1)(...)`

### Printing
Works the same way as printf in Java

fprintf() function has the first paremeter as a <mark style="background: #ADCCFFA6;">file pointer</mark>, the second as the control string, and the remaining arguments as variables being substituted.

stdin gets input from the keyboard
stdout displays to console
stderr priority displays to console

### Structured Programming
C's conditional expression is `x = condition ? IfValue : ElseValue;`

Switch cases work the exact same way

Don't use GOTO statements