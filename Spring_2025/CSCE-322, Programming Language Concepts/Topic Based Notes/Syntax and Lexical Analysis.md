Lectures 6.1 and 6.3

The syntax analysis portion of a language processor nearly always consists of two parts:
- A low-level part called a lexical analyzer
	- (mathematically, a finite automaton based on a regular grammar)
- A high-level part called a syntax analyzer, or parser
	- (mathematically, a push-down automaton based on a context-free grammar, or BNF)
	- Pattern matcher for strings (REGEX) that matches lexemes to tokens
	- Usually a function called by the parser when it needs the next token

Basically lexical analyzers define lexeme tokens and the syntax analyzer looks to see if these tokens are valid as per the CFG/BNF

We describe syntax with BNF because:
- Provides a clear and concise syntax description
- The parser can be based directly on the BNF
- Parsers based on BNF are easy to maintain

We separate lexical and syntax analysis because:
- Simplicity - less complex approaches can be used for lexical analysis; separating them simplifies the parser
- Efficiency - separation allows optimization of the lexical analyzer
- Portability - parts of the lexical analyzer may not be portable, but the parser always is portable

Use flex for lexical analysis. C code for lexical analyzing
Use Bison for syntax analysis. Converts CFG to a C program using bottom-up parsing

