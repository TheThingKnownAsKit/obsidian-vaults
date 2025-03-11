# Language Traits
## 1.1 Reasons for Studying Concepts of Programming Languages
You can bullshit this. More knowledge and blah blah
## 1.2 Programming Domains
A <mark style="background: #ADCCFFA6;">programming domain</mark> is an area of computer application and their associated languages. A specific situation in which you're trying to program

1. Scientific (1940s-1950s)
	1. Array and matrix math used for research purposes
	2. Control structures like counting loops and selections
	3. Fortran
2. Business (1950s)
	4. Produced elaborate reports
	5. Cobolt
3. AI (1950s)
	1. Symbolic computations rather than numeric
	2. Linked lists
	3. Lisp, prolog, python
4. Webdev (current)
	4. Dynamic web content
	5. Some computational capability
	6. WWW is supported by a lot of languages. HTML, Java, JavaScript, PHP
5. System programming
	1. Low level programming for writing to external devices
	2. C, C++
## 1.3 Language Evaluation Criteria
1. Readability
	1. Overall simplicity
	2. <mark style="background: #ADCCFFA6;">Orthogonality</mark>
		1. Small set of primitive constructs)
	3. Data types
		2. The way data types and structures are defined makes sense
	4. Syntax design
		3. Special words and compound statements
		4. Form and meaning - the statements should at least partially indicate their meaning
2. Writability
	1. Simplicity and Orthogonality
		1. Not enough orthogonality leads to too many data structures and programmers may not be familiar with all of them
		2. Too much can leads to errors if nearly any combination of primitives is legal (which having more types can fix)
		3. It is better to have a smaller set of primitives and consistent rules for combining them
	2. Expressivity
		4. A set of relatively convenient ways to do operations
		5. Strength and number of operators and predefined functions
	3. Support for abstraction
		1. Defining complex structures or operations in ways that details can be ignored
3. Reliability
	1. Type checking
		1. Testing for type errors while compiling because run-time type checking is expensive
	2. Exception handling
		2. Intercept run-time errors and take corrective measures
	3. Aliasing
		1. Aliasing is having two or more distinct names for accessing the same memory
		2. Dangerous feature
	4. Readability and writability
		1. A program written well is more reliable
	

![[Pasted image 20250305121527.png]]

Other factors include cost, portability, generality, and well-definedness (completeness and precision of the language's definition)

## 1.4 Influences on Language Design
1. Computer architecture
	1. The <mark style="background: #ADCCFFA6;">von Neumann architecture</mark> is when both data and programs are stored in the same memory, and the CPU is separate from the memory. Therefore, instructions have to be piped to the CPU
		1. Uses a fetch-execute cycle. Fetch instructions pointed to by the program counter, increment program counter, decode instruction, execute instruction
	2. Because of this architecture, most languages are imperative languages
		2. Variables model memory cells
		3. Assignment statements model piping operations
		4. Iteration is efficient
2. Program Design Methodologies
	1. New methodologies lead to new programming paradigms and by extension new programming languages
## 1.6 Language Design Trade-Offs
Generally, the two trade-offs are cost of execution and reliability. More reliability = greater cost (not money cost like computing cost)

Another is expressivity and readability. If you have a huge range of operations you can do to make things compact and precise, it can be very confusing to look at

Another is writability and reliability. The more complex things you can write, the less reliable the program is

## 1.5 Language Categories
- Imperative
	- Central features/Paradigms are: variables representing memory, assignment statements, and sequential execution
	- Expressions are evaluated for return values
	- Statements are executed for <mark style="background: #ADCCFFA6;">side-effects</mark> (aka modifications to a parameter, global variable, or I/O). This is the primary way to affect computation
	- Limitations:
		- <mark style="background: #ADCCFFA6;">von Neuman bottleneck</mark> of I/O between processor and memory being too slow
		- Sequential instructions are not useful for parallel computation, nondeterministic computation, or recursion
	- Includes: objected-oriented programming, scripting languages, and visual languages
	- Examples: C, Java, Perl, JavaScript, Visual BASIC .NET, C++
- Functional
	- Main means of making computations is by applying functions to given parameters
	- Central features/Paradigms are:
		- Making functions first-class entities (it can be stored, passed as an argument, and returned as a value)
		- It's based on $\lambda$-calculus
		- Mostly without variables, assignment, iteration, or I/O
		- No side-effects
	- Examples: LISP, Scheme, ML, F#
- Logic/Declarative
	- Rule-based (rules are specified in no particular order)
	- Sometimes called very-high-level languages or fifth-generation languages
	- Paradigm: efficiency mostly for AI systes 
	- Example: Prolog, SQL 
- Markup/programming hybrid
	- Markup languages extended to support some programming
	- Examples: JSTL, XSLT

I don't know why it's its own thing instead of with imperative, but here are object-oriented paradigms:
1. Support for data modeling and abstraction
2. Message passing between objects
3. Everything is an object, even primitives

Some programming languages are multi-paradigm

The boundaries of traditional paradigms are becoming blurry. Other classifications include scripting languages, parallel languages, markup/programming hybrid languages

![[Pasted image 20250305135233.png]]

If we need to know, second-class entities can only be passed as an argument and third-class cannot even be passed as an argument

## 1.7 Implementation Methods
- Compilation
	- Programs are translated into machine language; includes JIT systems
		- JIT is just in time where an intermediate language is used. Kind of like a delayed compiler
	- Slow translation, fast execution
	- Has several phases:
		- Lexical analysis: converts characters in the source program into lexical units
		- Syntax analysis transforms lexical units into parse trees which represent the syntactic structure of program
		- Semantics analysis: generate intermediate code
		- Code generation: machine code is generated
		- (we're learning all the above right now)
	- Used in large commercial applications
- Pure interpretation
	- Programs are interpreted by another program known as an interpreter
	- Easier to implement
	- 10 to 100 times slower on execution and requires more space
	- Used in small programs or when efficiency is not an issue. Also some scripting languages like JavaScript and PHP
- Hybrid implementation systems
	- Use a compromise between compilers and pure interpreters
	- Used in small and medium systems when efficiency is not the first concern
# 3.2 Describing Syntax and Semantics
<mark style="background: #ADCCFFA6;">Syntax</mark>: the form or structure of the expressions, statements, and program units
- Use grammar to define a formal language
- A formal language is a set of sentences (strings) over some "alphabet" (basically just a key that defines valid strings)
<mark style="background: #ADCCFFA6;">Semantics</mark>: The meaning of the expressions, statements, and program units

## 3.2 The General Problem of Describing Syntax

A <mark style="background: #ADCCFFA6;">sentence</mark> is a string of characters over some "alphabet"

A <mark style="background: #ADCCFFA6;">language</mark> is a set of sentences

A <mark style="background: #ADCCFFA6;">lexeme</mark> is the lowest level syntactic unit of a language (a single operator or word)
Lexemes are divided into categories called <mark style="background: #ADCCFFA6;">tokens</mark>. Standard categories include:
- Reserved words
- Literals or constants
- Special symbols (operators)
- Identifiers (variable names)

![[Pasted image 20250305141017.png]]

<mark style="background: #ADCCFFA6;">Recognizers</mark> are a language device that reads input strings over the alphabet of the language and decides whether the input strings are valid sentences
	i.e. syntax analysis during compilation

<mark style="background: #ADCCFFA6;">Generators</mark> are a language device that generates sentences of a language

Three levels of sentence validity
1. Lexically valid
	1. All the words of the sentence are valid aka they are real words defined in the "alphabet"
2. Syntactically valid
	2. Lexically valid and the order of the words is valid
3. Semantically valid
	1. Syntactically valid and has a valid meaning
## Binding
<mark style="background: #ADCCFFA6;">Binding</mark> is mapping from representation -> intended mean. For example, keyword int -> integer. int x binds the identifier to a type. x = 1 binds a value to a variable

A <mark style="background: #ADCCFFA6;">static binding</mark> happens prior to execution (usually during compile-time). This is safe, reliable, predictable, and efficient
A <mark style="background: #ADCCFFA6;">dynamic binding</mark> happens and is changeable during run-time. It is flexible

## Standard Grammar Categories
<mark style="background: #ADCCFFA6;">Declarations</mark> or definitions: defining the type
<mark style="background: #ADCCFFA6;">Statements</mark>
<mark style="background: #ADCCFFA6;">Expressions</mark>, such as the running expression of grammar example we have covered so far
<mark style="background: #ADCCFFA6;">Sequences</mark> of things (expressions, statements, declarations)
