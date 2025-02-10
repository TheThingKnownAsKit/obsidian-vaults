An **interface** can specify a set of abstract methods that an implementation class must override and define.
In interfaces, an abstract method does not need the `abstract` keyword in the method signature
Instead, use the keyword `interface` in the class signature
```Java
public interface DrawableASCII {
	public void drawASCII(char drawChar);
}
```

Any class that implements an interface must:
* List the interface name after the keyword `implements`
* Override and implement the interface's abstract methods

The advance of interfaces is that using superclass's and polymorphism, a class can only inherit from a single superclass. However, **a class can implement multiple interfaces using a comma separated list**
```Java
public class Square implements Drawable, DrawableASCII {
stuff
}
```

Interfaces vs abstract classes best use cases:
* Provides only static final fields: *Interface* since it won't restrict the class's inheritance
* Provides variables/fields: Only *abstract* classes can provide variables/fields to the subclasses
* Provides an API that must be implemented and no other code: *Interfaces* because no inheritance restriction

NOTE: A class can both EXTEND a class and IMPLEMENT an interface

Interfaces in UML:
![[Pasted image 20240128173638.png]]
![[Pasted image 20240128173653.png]]

## Sorting an ArrayList
Each primitive wrapper class implements the `Comparable` interface which declares the `compareTo()` method

`Collections.sort(arrayList)`

## Generic Methods
A **generic method** is a method definition having a special type parameter that may be used in place of types in the method
	Think ArrayLists
```Java
public class ItemMinimum {
	public static <TheType extends Comparable<TheType>>
	TheType tripleMin (TheType item1, TheType item2, TheType item3) {
		TheType minVal = item1; // Holds min item value, init to first item

	  if (item2.compareTo(minVal) < 0) {
		 minVal = item2;
	  }
	  if (item3.compareTo(minVal) < 0) {
		 minVal = item3;
	  }
	  return minVal;
	}
}
```

IMPORTANT TAKEAWAY:
```Java
<TheType extends Comparable<TheType>>
```

TheType is known as a **type parameter**. It may be associated with a **type bound** to specify the class types for which a type parameter is valid

You can have multiple generics
```Java
<Type1 extends BoundType1, Type2 extends BoundType2>
```

## Generic Class's
A **generic class** is a class definition having a special type parameter that may be used in place of types in the class. A variable declared of that generic class type must indicate a specific type

```Java
public class TripleItem <TheType extends Comparable<TheType>> {}
```

```Java
TripleItem<Integer> triInts = new TripleItem<Integer>;
```