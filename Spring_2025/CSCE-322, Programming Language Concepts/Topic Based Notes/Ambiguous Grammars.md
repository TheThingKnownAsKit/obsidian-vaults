If a sentence from a language has more than one parse tree, then the grammar for the language is <mark style="background: #ADCCFFA6;">ambiguous</mark>. Basically is there more than one way to parse it. Steps to prove a grammar is ambiguous:
1. generate an expression from the grammar and show the expression
2. give two parse trees using the grammar for that expression

Generally three things you can do about ambiguity
1. Revise your grammar
2. Introduce operator precedence into the grammar using intermediate non-terminals
This revised grammar always gives multiplication and division higher precedence over addition and subtraction
![[Pasted image 20250305154049.png]]
3. Introduce associativity into the grammar using intermediate non-terminals
<mark style="background: #ADCCFFA6;">Associativity</mark> is an issue when dealing with operators with the same precedence. You give preference for evaluating things from left to right or right to left
- Left associative: $6-3-2\leftrightarrow (6-3)-2$
- Right associative: $a=b=c\leftrightarrow a=(b=c)$
This revised grammar uses an intermediate non-terminal to give it right associativity
![[Pasted image 20250305154808.png]]

Steps 2 and 3 are known as <mark style="background: #ADCCFFA6;">Desideratum</mark>; when syntax implies semantics. I think.

