![[Lecture2-Introduction to Concepts of PL_03_Syntax and Semantics_Biding.pdf]]
## Syntax and Semantics
<mark style="background: #ADCCFFA6;">Syntax</mark> is the form or structure of the expressions, statements, and program units
- Grammar, set of sentences, legal strings
- A sentence is a string of characters over some alphabet, a language is a set of sentences, a lexeme is the lowest level syntactic unit of a language (like one word), a token is a category of lexemes
<mark style="background: #ADCCFFA6;">Semantics</mark> are the meaning of the expressions, statements, and program units
These two things provide the language's definition

Reserved words and all that, single characters, special characters

A <mark style="background: #ADCCFFA6;">recognizer</mark> is a device that reads input strings over the alphabet of the language and decides whether the input strings belong to the language. Syntax analysis part of a compiler
A <mark style="background: #ADCCFFA6;">Generator</mark> is a device that generates sentences of a language

Three levels of sentence validity
1. <mark style="background: #ADCCFFA6;">Lexically validity</mark> when all the words of the sentence are valid
2. <mark style="background: #ADCCFFA6;">Syntactically validity</mark> is when lexically valid and the order of the words is valid
3. <mark style="background: #ADCCFFA6;">Semantically validity</mark> is when syntactically valid and has valid meaning

Tokens are recognized by the first phrase of a translator, the scanner, which is the only part of the translator that deals directly with the input. They can be defined using either grammar rules or regular expressions

<mark style="background: #ADCCFFA6;">Scanners</mark> are recognizers of regular expressions. Implemented as finite automata, aka finite state machines

<mark style="background: #ADCCFFA6;">Regular Grammars</mark> also called linear grammars, are generative devices for regular languages. It defines regular languages. Any finite language is regular. Sentences from regular languages are recognized using finite state automata (FSA)
- Lexemes can be formally described by regular grammars. Regular grammars have their own syntax with some special characters (meta-characters)
- Example: `[0-9][0-9][0-9]-[0-9][0-9]-[0-9][0-9][0-9][0-9]` defines a SSN
