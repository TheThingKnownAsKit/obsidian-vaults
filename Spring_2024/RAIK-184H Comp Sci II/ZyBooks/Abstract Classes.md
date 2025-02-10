An **abstract class** is a class that guides the design of subclasses but cannot itself be instantiated as an object.
	An Abstract Shape class might also specify that any subclass might define a computeArea() method
	Blueprint
	Emphasis on inherited BEHAVIOR, not traits
![[Pasted image 20240123200328.png]]

An **abstract method** is a method that is not implemented in the base class, thus all derived classes must override the function. An abstract method is denoted by the keyword `abstract` in front of the method signature
`abstract double computeArea();`
NOTE: these are weird, you don't actually do anything in the method body. There's no {}, it just declares it's supposed to exist. Like C++ kinda

An **abstract class** is a class that cannot be instantiated as an object, but id the superclass for a subclass and specifies how the subclass must be implemented. Any class with one or more abstract methods but be abstract
`public abstract class Shape {}`

A **concrete class** is a class that is not abstract and can be instantiated

The **Unified Modeling Language (UML)** is a language for software design that uses different types of diagrams to visualize the structure and behavior of programs
A **structure diagram** visualizes static elements of software, such as attributes (variables) and methods
A **behavioral diagram** visualizes dynamic behavior of software, such as flow of an algorithm
A UML **class diagram** is a structural diagram that can be used to visually model the classes of a computer program, including member variables and methods
![[Pasted image 20240123201248.png]]
Italics is used for abstract classes and methods
Inheritance is shown with an arrow
