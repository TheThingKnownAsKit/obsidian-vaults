Lecture 7

## Lisp
Lisp stands for (List Processing)
- Functional programming language based on lambda calculus
- Designed by John McCarthy in 1959, first implemented by Steve Russell in 1960. First lisp interpreter in 1960 and first complete lisp compiler written in lisp in 1962.
- Favored for AI research because it's convenient for symbolic reasoning
- Extremely simple, uniform, and consistent syntax: atoms and lists and that's it
- Blurred distinctions between program and data (they have the same syntax ad representation in memory)
- Pioneered many ideas in computer science
	- Tree data structures, automatic memory management, dynamic typing, conditionals, high-order functions, recursion, self-hosting compiler, etc
- Linked lists is Lisp's major data structure. The list part
- All program code is written as s-expressions, or parenthesized lists

Lisp dialects are common lisp, scheme, racket, clojure

## Scheme
- Like lisp, uniform representation of programs and data using a single general structure: the list
- Definition of the language using an interpreter written in the same language (meta-circular interpreter)
- Cleaner, more modern, and simpler than other versions of lisp
- Uses only static scoping
- Functions are first-class entities
The Scheme Interpreter:
- In interactive mode, the Scheme interpreter is an infinite read-evaluate-print loop (REPL)
	- Similar to Python and Ruby
- Expressions are interpreted by the function eval

## Racket
- Started as a scheme implementation and evolved into a general-purpose programming language as well as the world's first language-oriented programming
- "Racket is a programming language for creating new programming languages"
- Best of Scheme and Lisp
- DrRacket is the interpreter of Racket
- No variables and assignments to avoid side-effects
- Functional programming language
