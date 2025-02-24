![[Lecture4-LanguageRecognition.pdf]]

## Review: Lecture 3 Language Generation
We can use grammars for language generation by applying the rules in a top-down fashion and constructing a derivation
![[Pasted image 20250224103713.png]]

A string in RHS containing terminals and non-terminals is called a sentential form

## Parsing aka Reverse Derivation
1. Scan the string from left-to-right and put on a stack
	1. . (dot) denotes the top of the stack
	2. The RHS of the dot is the remainder of the string to be parsed, called <mark style="background: #ADCCFFA6;">handle</mark>
2. Apply <mark style="background: #ADCCFFA6;">shift-reduce</mark> rule (or bottom-up) as follows:
	1. If the items at the top of the stack match the RHS of any production rule, replace those items with the non-terminal of LHS of the rule (REDUCE RULE)
	2. If there is not a match, shift to the next lexeme (SHIFT RULE)

Example: Parsing 1 + 3 * 2
![[Pasted image 20250224104052.png]]
$$\begin{matrix}
. & 1 & + & 3 & * & 2 &  & (shift) \\
1 & . & + & 3 & * & 2 &  & (reduce\ r7) \\
<number> & . & + & 3 & * & 2 &  & (reduce\ r6) \\
<expr> & . & + & 3 & * & 2 &  & (shift) \\
<expr> & + & . & 3 & * & 2 &  & (shift) \\
<expr> & + & 3 & . & * & 2 &  & (reduce\ r7) \\
<expr> & + & <number> & . & * & 2 &  & (reduce\ r6) \\
<expr> & + & <expr> & . & * & 2 &  & (reduce\ r1) \\
<expr> & . & * & 2 &  &  &  & (shift) \\
<expr> & * & . & 2 &  &  &  & (shift) \\
<expr> & * & 2 & . &  &  &  & (reduce\ r7) \\
<expr> & * & <number> & . &  &  &  & (reduce\ r6) \\
<expr> & * & <expr> & . &  &  &  & (reduce\ r3) \\
<expr> & . & (start\ symbol) \\
 \implies \text{this is a valid sentence}
\end{matrix}$$

This process can be represented using a parse tree
![[Pasted image 20250224105118.png]]

If there is a parsing conflict, it does not matter which parse should be used since they both should determine the same thing: if the sentence is valid or not
	Shift-reduce conflict happens when we have operator precedence or associativity in the grammar
	Reduce-reduce conflict

If a sentence from a language has more than one parse tree, then the grammar for the language is <mark style="background: #ADCCFFA6;">ambiguous</mark>. To prove it:
1. generate an expression from the grammar and show the expression
2. give two parse trees "using the grammar" for that expression