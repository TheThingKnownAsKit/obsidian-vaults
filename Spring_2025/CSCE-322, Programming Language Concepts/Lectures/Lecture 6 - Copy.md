![[Lecture6-Lexical and Syntax Analysis_01.pdf]]

Language implementation systems must analyze source code, regardless of the specific implementation approach. Nearly all syntax analysis is based on a formal description of the syntax of the source language (BNF)

---

![[Lecture6-Lexical and Syntax Analysis_02.pdf]]

Goals of the parser, given an input program:
- Find all syntax errors; for each, produce an appropriate diagnostic message and recover quickly
- Produce the parse tree, or at least a trace of the parse tree, for the program

Two categories of parsers:
- Top down - produce the parse tree, beginning at the root
	- Key Problem: Identify which production of a non-terminal must be chosen such that the terminals in the production body match the terminals in the input string
	- Backtracking is computationally expensive
- Bottom up (or shift-reduce) - produce the parse tree, beginning at the leaves
	- Read input string from the left to the right
	- Build parse tree from the right to the left, ie we use the grammar in the opposite way (reverse parsing), from the right to the left
	- Two rules in bottom up parsing:
		- Reduction rule: if the first few symbols (tokens) (of the input string) at the top of the stack match the RHS of some rule, we pop out these symbols from the stack and push the LHS of the rule
		- Shift rule: shift the current input token in the stack and read the next token
	- Key problem: figuring out when to reduce in ambiguous languages. when to apply rules if youre going left to right?
Useful parsers look only one token ahead in the input

Making the tree is just starting at S -> each letter makes another input and then if one of those continues down continue down

Put top-down parsing algorithms diagram here

LL(1)
LL(3)
Whatever the number in the parenthesis determines how far ahead a LL parser will look for a null terminal

Recursive descent parsing:
- Has a set of sub-procedures
- One sub-procedure is for one non-terminal in the grammar
- The parsing starts with the execution of the sub-procedure for the starting symbol
- EBNF () is ideally suited for being the basis for a recursive-descent parser because complexity is determined by non-terminals, so the more non-terminals the more complex, and EBNF will minimize the number of non-terminals

```
void A() {
	for (i = 1 to k) {
		if (Xi is a nonterminal)
			call procedure Xi();
		else if (Xi = current input symbol a)
			advance the input to the next symbol;
		else an error has occurred
	}
}
```

EBNF grammar for a program picture here

![[Pasted image 20250226192313.png]]
![[Pasted image 20250226192328.png]]

## Quiz
![[Pasted image 20250226192343.png]]
![[Pasted image 20250226192357.png]]
