The **Queue** interface defined within the Java Collections Framework defines a Collection of ordered elements that supports element insertion at the tail and element retrieval from the head
`Queue<T> queue = new LinkedList<T>();`
Literally just a queue

| method | use |
| ---- | ---- |
| `add()` | Adds newElement to the tail of the queue. The queue's size increases by one |
| `remove()` | Removes and returns the element at the head of the queue. Throws an exception if the queue is empty |
| `poll()` | Removes and returns the element at the head of the queue if the queue is not empty. Otherwise, returns null |
| `element()` | Returns, but does not remove, the element at the head of the queue. Throws an exception if the queue is empty |
| `peek()` | Returns, but does not remove, the element at the head of the queue if the queue is not empty. Otherwise, returns null |

The **Deque** interface defined within the Java Collections Framework defines a Collection of ordered elements that supports element insertion and removal at both ends (head and tail)
`Deque<T> deque = new LinkedList<T>();`
The ability to remove/add at the head and tail allows Deque to be used as a stack. A **stack** is an ADT in which elements are only added or removed from the top of a stack

| method | use |
| ---- | ---- |
| `addFirst()` | Adds newElement at the head of the deque. Size increases by one |
| `addLast()` | Adds newElement to the tail of the deque. Size increases by one |
| `removeFirst()` | Removes and returns the element at the head of the deque. Throws an exception if empty |
| `removeLast()` | Removes and returns the element at the tail of the deque. Throws an exception if the deque is empty |
| `pollFirst()` | Removes and returns the element at the head of the deque if the deque is not empty. Otherwise, returns null |
| `pollLast()` | Removes and returns the element at the tail of the deque if the deque is not empty. Otherwise, returns null |
| `getFirst()` | Returns, but does not remove, the element at the head of the deque. Throws an exception if the deque is empty |
| `getLast()` | Returns, but does not remove, the element at the tail of the deque. Throws an exception if the deque is empty |
| `peekFirst()` | Returns, but does not remove, the element at the head of the deque if the deque is not empty. Otherwise, returns null |
| `peekLast()` | Returns, but does not remove, the element at the tail of the deque if the deque is not empty. Otherwise, returns null |
