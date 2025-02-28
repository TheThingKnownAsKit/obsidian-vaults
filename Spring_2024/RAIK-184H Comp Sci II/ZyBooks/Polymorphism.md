An **annotation** is an optional command beginning with @ that can provide the compiler with information that helps the compiler detect errors better
	Without @Override, the compiler will not know to throw errors when parameters do not match the original function

In @Override, the first method found is used even without @Override present

The Object class's toString() method returns the Object instance's type followed by an unsigned hexadecimal representation of the object's hash code

**Polymorphism** refers to determining which program behavior to execute depending on data types
**Compile-time polymorphism** determines which of several identically-named methods to call based on the method's arguments. Method overloading is a form of this
**Runtime polymorphism** is a form where the compiler cannot make the determination so it is made while the program is running. Derived classes are an example of this

A **derived/base class reference conversion** is a feature wherein a reference to a derived class can be converted to a reference to the bass class (without explicit casting)

*An ArrayList of an object type may only reference methods/fields of the list type, even if the items are objects derived from the overall object type*
For example, if you have an ArrayList of type Object and it's full of Double objects, you CANNOT use .doubleValue() on any list index since it is not a method native to the Object class

Programmers commonly draw class inheritance relationships using **Unified Modeling Language UML**
![[Pasted image 20240123195802.png]]
