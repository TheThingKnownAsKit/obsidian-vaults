## Mathematical Functions in Functional Programming
A mathematical function is a mapping of members of one set, called the domain set, to another set, called the range set
A lambda expression is a method to specify the parameters(s) and the mapping of a function in the following form:
$\lambda(x)=x*x*x$ for the function cube

Functional programming hallmarks
- Functions are first-class and can be set to an identifier (var)
- Can be passed to a function
- Can be returned from a function
- Functions have types
- Easy to test in isolation of the rest of the program with interactive or incremental testing

Lambda expressions describe nameless functions

Primitive arithmetic functions in Racket:
`+,-,*,/,abs,sqrt,remainder,min,max`
So `(+ 5 2)` evaluates to 7

```Racket
(lambda (x) (* x x))
(lambda (x) (* x x x) 2) // One parameter
((lambda (a b x) (+ (* a x x))) (* b x)) // Many parameters. Parenthesis wrong
```
Note: it can have any number of parameters
Where the first parenthesis are the parameters, the second is the expression, and the third is the input
## Quiz Questions
In Scheme `((lambda (n) (+ n 2)) (+ 1 4))` = 7