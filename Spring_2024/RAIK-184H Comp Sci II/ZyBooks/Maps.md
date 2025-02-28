the **Map** interface within the Java Collections Framework defines a Collection that associates (or maps) keys to values. Returns null if no corresponding key is found

The **HashMap** is an ADT implemented as a generic class. Has the `put(K, V)` and `get(K)` method
`HashMap<K, V> hashMap = new HashMap<K, V>();` where K represents the key type and V represents the value type
	(like numbering strings 1-10 with ints)

| method | description |
| ---- | ---- |
| `put()` | `put(key, value)`<br>Associates key with specified value. If key already exists, replaces previous value with specified value |
| `putIfAbsent()` | `putIfAbsent(key, value)`<br>Associates key with specified value if the key does not already exist or is mapped to null |
| `get()` | Returns the value associated with key. If key does not exist, return null |
| `containsKey()` | Returns true if key exists, otherwise returns false |
| `containsValue()` | Returns true if at least one key is associated with the specified value, otherwise returns false |
| `remove()` | Removes the map entry for the specified key if the key exists |
| `clear()` | Removes all map entries |
| `keySet()` | Returns a Set containing all keys within the map |
| `values()` | Returns a Collection containing all values within the map |