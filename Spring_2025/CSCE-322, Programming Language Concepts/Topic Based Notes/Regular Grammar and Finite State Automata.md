Scanners are the recognizers of regular expressions. They are implemented as <mark style="background: #ADCCFFA6;">finite state machines aka finite automata</mark>. All it does is scan tokens by looping through each character and build tokens
1. Accepts a string as input and outputs yes if it can run the entire string or no if it gets interrupted by invalid input
![[Pasted image 20250305142406.png]]

All it does is graphically represent REGEX (<mark style="background: #ADCCFFA6;">regular grammar</mark>). Regular grammars <mark style="background: #BBFABBA6;">(basically just REGEX)</mark> are generative devices for regular languages
- They define them regular languages
- Sentences from regular languages are recognized using a finite state automata (FSA)
- Lexemes are described by regular grammars
![[Pasted image 20250305142304.png]]
[[REGEX Cheatsheet.pdf]]
