A **LinkedList** supports insertion of elements at the end or specified indexes.
`LinkedList<T> list = new LinkedList<T>();`
`list.add(2, "Butler");` inserts at index 2

| method | use |
| ---- | ---- |
| `get()` | `get(index)` <br>Returns element at specified index. |
| `set()` | `set(index, newElement)`<br>Replaces element at specified index with newElement. Returns element previously at specified index |
| `add()` | `add(newElement)`<br>Adds newElement to the end of the list. Size increases by one<br><br>`add(index, newElement)`<br>Adds newElement to the specified index. Indices of the element previously at that specified index and higher are increased by one. Size increased by one |
| `size()` | `size()`<br>Returns the number of elements in the List. |
| `remove()` | `remove(index)`<br>Removes element at specified index. Indices at higher position decreased by one. List size decreased by one. Returns reference to element removed from List<br><br>`remove(existingElement)`<br>Removes the first occurrence of an element which is equal to existingElement. Returns true if specified element was found and removed |

Efficient iteration through a LinkedList necessitates keeping track of the current position in the loop without using an index. A **ListIterator** is an object that points to a location in a List and provides methods to access an element and advance the ListIterator to the next position in the list
A LinkedList's listIterator() method returns a ListIterator object for traversing a list. Need to important it to use

```Java
LinkedList<String> authorsList = new LinkedList<String>();
String authorName;
ListIterator<String> listIterator;

authorsList.add("Gamow");
authorsList.add("Greene");
authorsList.add("Penrose");

listIterator = authorsList.listIterator();

while (listIterator.hasNext()) {
	authorName = listIterator.next();
	System.out.println(authorName);
}
```
`listIterator.hasNext()` returns true if a list has more elements. Otherwise, return false
`listIterator.next()` returns the next element in the list and moves the iterator to the next location
ALWAYS CALL HASNEXT FIRST OTHERWISE THERE WILL BE AN ERROR

| method | use |
| ---- | ---- |
| `next()` | Returns the next element in the List and moves the ListIterator after that element |
| `nextIndex()` | Returns the index of the next element |
| `previous()` | Returns the previous element in the List and moves the ListIterator before that element |
| `previousIndex()` | Returns the index of the previous element |
| `hasNext()` | Returns true if ListIterator has a next element. Otherwise, returns false |
| `hasPrevious()` | Returns true if ListIterator has a previous element. Otherwise, returns false |
| `add()` | Adds the new element between the next and previous elements and moves the ListIterator after newElement |
| `remove()` | Removes the element returned by the prior call to next() or previous().<br><br>Fails if used more than once per call to next() or previous().<br>Fails if add() has already been called since the last call to next() or previous() |
| `set()` | Replaces the element returned by the prior call next() or previous() with newElement |