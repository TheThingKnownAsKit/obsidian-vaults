It automatically generates declarations, scanner, parser, and stream scanner parser for you if given CFG or regular grammar as inputs

sllgen:make-define-datatypes -> generates declarations
sllgen:make-string-scanner     -> generates a scanner
sllgen:make-string-parser       -> generates a parser and maybe also a scanner
sllgen:make-stream-something idk makes the stream scanner

Grammar for a scanner specification in SLLGEN
```
Scanner-spec      ::= ({Regexp-and-action}*)
Regexp-and-action ::= (Name ({Regexp}*) Action)
Name              ::= Symbol
Regexp            ::= String | letter | dii=git | whitespace | any
                  ::= (not Character) | (or {Regexp}*)
                  ::= (arbno Regexp) | (concat {Regexp}*)
                  ::= skip | symbol | number | string
```

As compared to the current concrete syntax we're using
```
<program> ::= <expr>
<expr>    ::= <number>
          ::= <identifier>
          ::= (<primitive> <exp> <expr>)
primitive ::= + | -
```

Code to implement sllgen
```Racket
(define the-lexical-spec
  '((whitespace (whitespace) skip)
	(comment (";" (arbno (not #\newline))) skip) ; Equiv. regex is ";[^newline]*"
	(identifier
	  (letter (arbno (or letter digit "_" "-" "?"))) symbol) ; equiv. regex is "letter[letter|digit|_-?]*"
	(number (diit (arbno digit)) number) equiv. regex is "digit[digit]*" or "[digit]+"
   )
)
```

Note that the name for the token will be used in the BNF grammar. String patterns in regular expression defined in list form. arbon = * as in repeating 0 or more times and letter and digit are predefined in eopl

Actions available for the scanner:
- skip, ignore the input
- symbol, make an identifier in symbol? type
- number, make a number in number? type
- string, make a string 

BNF for a grammar in SLLGEN
$$\begin{matrix}
Grammar & ::= & ({Production}*) \\
Production & ::= & (Lhs\ ({Rhs-item}*)\ Prod-name) \\
Lhs & ::= & Symbol \\
Rhs-item & ::= & Symbol | String \\
 & ::= & (arbno\ {Rhs-item}*) \\
 & ::= & (separated-list\ {Rhs-item}*\ String) \\
Prod-name & ::= & Symbol
\end{matrix}$$
BNF in code for sllgen
```Racket
(define the-grammar
  '((program (myexpression) a-program)
   (myexpression (number) lit-exp)
   (myexpression (identifier) id-exp)
   (myexpression
     ("(" primitive myexpression myexpression ")")
     primapp-exp)
   (primitive ("+")    add-prim)
   (primitive ("-")    subtract-prim)
  )
)
```