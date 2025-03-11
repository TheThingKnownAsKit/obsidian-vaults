<mark style="background: #ADCCFFA6;">Context-free grammars</mark> are language generators meant to describe the syntax of natural languages. It defines context-free languages
	Developed by Noam Chomsky

<mark style="background: #ADCCFFA6;">Backus-Naur Form (BNF)</mark> was invented by John Backus i 1959 to describe something related and <mark style="background: #BBFABBA6;">it is equivalent to context-free grammars</mark>. In it, abstractions are used to represent classes of syntactic structures/syntactic variables (nonterminals and terminals)
![[Pasted image 20250305143842.png]]
<mark style="background: #BBFABBA6;">Elements include (THIS IS IMPORTANT:</mark>
- grammar : a set of production rules
- start symbol : where it starts evaluating, <> in the above example
- non-terminals : anything on the left-hand side. always includes start symbols or <>
- terminals : anything on the right-hand side. String of terminals and non-terminals. They are lexemes and do NOT have start symbols aka <>

A grammar rule is structure as:
$$LHS::=RHS$$
Where the RHS can be evaluated to equal the LHS

Applying these rules in a to-down fashion is language generation

A string in RHS containing terminals and non-terminals is in <mark style="background: #ADCCFFA6;">sentential form</mark>

<mark style="background: #ADCCFFA6;">Extended BNF</mark> can have more abstractions (or nonterminal symbols) than one RHS. Each abstraction is separated by |. It has extended ability to describe vocabulary by implementing REGEX-like instructions
![[Pasted image 20250305144636.png]]
EBNF adds more ways pf production rules:
- | means alternation
- [] means enclosed is optional
- {} means 1 of enclosed
- {}+ means 1 or more of enclosed
- {}* means 0 or more of enclosed
- `{<expr>}*(c) means 0 or more <expr> separated by c`

![[Pasted image 20250305154950.png]]
![[Pasted image 20250305155051.png]]
In general, to convert to EBNF, you just try to only have one of each non-terminal type equation (seen in image 1) and try to reduce redundant non-terminals (seen in image 2)