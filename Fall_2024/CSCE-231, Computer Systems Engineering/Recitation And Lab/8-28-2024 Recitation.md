CodeRunner plugin as well

Structures are defined with `struct`. Class with only public fields
```C
struct card {
	int pips;
	char suit;
};

struct card c1,c2;
```

You can also use typedef with the type at the bottom so you don’t have to write struct
```C
typedef struct {
	int pips;
	char suit;
} card;

card c1,c2;
```

Declare a pointer variable with * after the variable type
`int* num` is a pointer. You can also use `void*` to make a pointer with no type and this is generally more useful

You can dereference num with * as well, just do `*num = 3`. It won’t work without the * because a pointer does not have the actual value in it. If you want to change the value you need the actual memory address

Use & to get the memory address of something. `&num`

If you don’t know how much memory you need until runtime, you need to manually allocate memory using malloc. Remember C does NOT have a garbage collector
Be careful that pointers can still point to memory that does not exist anymore