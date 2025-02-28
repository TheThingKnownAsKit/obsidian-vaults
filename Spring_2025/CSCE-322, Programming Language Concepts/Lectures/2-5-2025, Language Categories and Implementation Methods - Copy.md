![[Lecture2-Introduction to Concepts of PL_02.pdf]]

## Language Categories
- <mark style="background: #ADCCFFA6;">Imperative</mark>
	- Central features are variables, assignment statements, and iteration
	- Include languages that support object-oriented programming
	- Include scripting languages
	- Include the visual languages
	- Examples: C, Java, Perl, JavaScript, Visual BASIC .NET, C++
- <mark style="background: #ADCCFFA6;">Functional</mark>
	- Main means of making computations is by applying functions to given parameters
	- Examples: LISP, Scheme, ML, F#
- <mark style="background: #ADCCFFA6;">Logic</mark>
	- Rule-based (rules are specified in no particular order)
	- Example: Prolog
- <mark style="background: #ADCCFFA6;">Markup/programming hybrid</mark>
	- Markup languages extended to support some programming
	- Examples: JSTL, XSLT

<mark style="background: #BBFABBA6;">The imperative paradigms are:</mark>
- sequential execution
- variables representing memory
- use of assignment to change the values of variables
- Expressions are evaluated for <mark style="background: #BBFABBA6;">return values</mark>
- Statements are executed for <mark style="background: #BBFABBA6;">side-effect</mark> and the primary way to affect computation in an imperative language is through side-effect
<mark style="background: #BBFABBA6;">The imperative limitations are:</mark>
- von Neumann bottleneck
	- I/O between processor and memory is the biggest bottleneck. Time to load instructions is slower than time to execute them
- A sequence of instructions is not necessarily the best way to handle all programs. Such as parallel computation, nondeterministic computation, or recursion
- Side effects also mean computation effects external environment (such as global variables) and unexpected results might happen

<mark style="background: #BBFABBA6;">Functional paradgism are</mark>:
- Brings programming closer to mathematics by making functions first-class entities
	- A <mark style="background: #ADCCFFA6;">first-class entity</mark> is one that can be stored, passed as an argument, and returned as a value
	- (second-class can only be passed as an argument, third-class cannot even be passed as an argument)
- Based on lambda calculus: a theory of functions on which all functional languages are based
- Has no variables, assignment, and iteration
- No side effects even for I/O, no variables, no assignment statement

<mark style="background: #BBFABBA6;">Declarative/Logic paradigm</mark>
- Rule-based (rules are specified in no particular order)
	- Describe what you want, not how to get it
- Support for reasoning abut facts and rules
- Very high level languages or fifth generation languages. Efficiency mostly for AI systems

<mark style="background: #BBFABBA6;">Object-oriented paradigm</mark>
- Support for data modeling and abstraction
- Message passing since the system is one constructed as a collection of objects passing messages to each other
- Purity: everything is an object, even primitives

Multi-paradigm programming languages do exist. There are also other classifications for language paradigms

## Implementation Methods
<mark style="background: #ADCCFFA6;">Compilation</mark>
- Programs are translated into machine languages
- Slow translation, fast execution
<mark style="background: #ADCCFFA6;">Pure interpretation</mark>
- Programs are interpreted by another program known as an interpreter
- Easier implementation of programs. Slower execution (by 1o to 100 times slower). Requires more space
- Rare for high level languages, mostly used with web scripting languages
<mark style="background: #ADCCFFA6;">Hybrid implementation systems</mark>
- A compromise between compilers and pure interpreters
- A high level language program is translated to an intermediate language that allows easy interpretation to make it faster than pure interpretation but still easier than compilation
<mark style="background: #ADCCFFA6;">Just-in-Time (JIT) implementation systems:</mark>
- Initially translate programs to an intermediate language, then compile the intermediate into machine code when called. This machine code is kept for subsequent calls
- Essentially delayed compilers. Java and .NET