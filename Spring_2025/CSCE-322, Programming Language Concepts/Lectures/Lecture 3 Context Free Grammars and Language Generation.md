![[Lecture3-ContexFree-Grammars.pdf]]

## Grammar and BNF
<mark style="background: #ADCCFFA6;">Context-Free Grammars</mark>
- Language generators, meant to describe the syntax of natural languages
- Define a class of languages called context-free languages
- Developed by Noam Chomsky
<mark style="background: #ADCCFFA6;">Bsckus-Naur Form - BNF</mark>
- Invented by John Backus to describe the syntax of Algol in 58
- BNF is equivalent to context-free grammars
- Example: `<article> <noun> <verb> <adverb>`

Elements of BNF Notation
- grammar = set of production rules
- start symbol, eg `<`
- non-terminals as in actual words, the noun and verb part
- terminals,

Grammar rule: LHS ::=RHS
LHS is nonterminal and the RHS is terminal

BNF uses abstractions to represent classes of syntactic structure. They act like syntactic variables (also called nonterminal symbols or just terminals)
<mark style="background: #BBFABBA6;">Terminals are lexemes</mark>

A rule has a left-hand side (LHS), which is a nonterminal, and a right-hand side (RHS), which is a string of terminals and/or nonterminals

Nonterminals are often enclosed in angle brackets
Example:
`<list> -> identifier | identifier, <list>`
`<if_stmt> -> if <logic> then <stmt>`
<mark style="background: #ADCCFFA6;">Grammar</mark> is a finite non-empty set of rules. A <mark style="background: #ADCCFFA6;">start symbol</mark> is a special element of the non-terminals of a grammar

<mark style="background: #ADCCFFA6;">Tokens are non-terminals in BNF</mark>. They're a syntactic category that forms a class of lexemes

A string in RHS containing terminals and non-terminals is called in <mark style="background: #ADCCFFA6;">sentential form</mark>

<mark style="background: #ADCCFFA6;">Extended BNF</mark> is when an abstraction or nonterminal symbol can have more than one RHS separated by |

## Derivation
A <mark style="background: #ADCCFFA6;">derivation</mark> is a repeated application of rules, starting with the start symbol and ending with a sentence (all terminal symbols)
There are leftmost and rightmost derivations. Some derivations are neither
Any derivation method will have the same result

![[Pasted image 20250224103103.png]]
![[Pasted image 20250224103114.png]]

![[Pasted image 20250224103144.png]]
Grammars can be used for both language generation and recogntion
	Generation: start symbol -> sentence
	Recognition: sentence -> start symbol

## Language Recognition
Given an input string and grammar, we can construct a <mark style="background: #ADCCFFA6;">reverse derivation</mark> to determine if the string is a sentence. This process is called <mark style="background: #ADCCFFA6;">parsing</mark>. A computer program implementing parsing is called a <mark style="background: #ADCCFFA6;">parser</mark>

![[Pasted image 20250224103341.png]]
