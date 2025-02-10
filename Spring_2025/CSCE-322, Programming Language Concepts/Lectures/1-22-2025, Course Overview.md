![[Lecture1-CourseOverview.pdf]]

## Programming Domain
A <mark style="background: #ADCCFFA6;">Programming Domain</mark> is just a specific situation in which you're trying to program. A business context, web context, etc. Languages tend to focus on one programming domain

- Scientific applications of programming domains:
	- First digital computers were invented and used for scientific applications
	- Simple data structures: arrays and matrices
	- Control structures: counting loops and selections
		- For example, Fortran
- Business applications:
	- 1950s
	- Facilities for producing elaborate reports
	- Cobolt
- AI Applications
	- Late 1950s
	- Symbolic computations rather than numeric computation. Linked lists rather than array
	- Lisp, prolog, python
- Web software applications
	- Dynamic web content. Some computation capability is often included in the technology of content presentation
	- WWW is supported by an eclectic collection of languages. Markup language (HTML), general-purpose programming language (Java), scripting language (JavaScript or PHP)
- System programming
	- Efficiency and reliability because of continuous use. Low level features that allows the software interfaces to external devices to be written
	- C, C++

## Language Evaluation Criteria
<mark style="background: #BBFABBA6;">Evaluate on readability, writability, reliability, cost</mark>

Readability criteria:
1. <mark style="background: #ADCCFFA6;">Overall simplicity</mark> is a manageable set of features and constructs.
	1. Programmers often learn and use a subset of a large language and ignore its other features
	2. Minimal feature multiplicity (having more than one way to accomplish a particular operation)
	3. Minimal operator overloading
	4. <mark style="background: #ADCCFFA6;">Orthogonality</mark> is few constructs, a small number of primitives, a small set of rules for combining them. Every possible combination of primitives is legal and meaningful
	5. Need adequate and predefined data types
	6. Needs good syntax design
		1. Program appearance is influenced by the forms of a language's special world.
		2. Methods to form compound statements, or statement grounds.
		3. Form and meaning is designed statements so that their appearance at least partially indicates their purpose