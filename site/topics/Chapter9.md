# Chapter 9 (Collections)

## Factory methods

| Method                         | Description                                            |
|--------------------------------|--------------------------------------------------------|
| Arrays.asList(E ...items)      | Returns FIXED SIZE list                                |
| List.of(E ...items)            | Returns immutable list                                 |
| List.copyOf(Collection c)      | Returns immutable copy of c                            |
| ArrayList(int initialCapacity) | Creates an array list with a supplied initial capacity |
| Set.of(E ...items)             | Returns immutable set                                  |
| Set.copyOf(Collection c)       | Returns immutable copy of c                            |
| Map.of()                       | Returns immutable map                                  |
| Map.ofEntries(Map.Entry ...e)  | Returns immutable map                                  |
| Map.copyOf(Map m)              | Returns immutable copy of m                            |

## List methods

| Method                           | Description                                                                      |
|----------------------------------|----------------------------------------------------------------------------------|
| boolean add(E e)                 | Adds the element                                                                 |
| void add(int i, E e)             | Adds e at the supplied index and moves the rest of the array to the end          |
| E get(int i)                     | Gets the element at i                                                            |
| E remove(int i)                  | Removes the element at i                                                         |
| void replaceAll(UnaryOperator o) | Replaces each element in the list with a result of the operation                 |
| E set(int i, E e)                | Replaces the element at i with e. Returns the old value of i                     |
| void sort(Comparator c)          | Sorts the collection according to the comparator                                 |
| E[] toArray()                    | Converts the list to array                                                       |
| E[] toArray(E[] buffer)          | Adds the values of the list to the buffer if it fits. If not create a new array. |

## Queue (FIFO) methods

| Method             | Description                                             |
|--------------------|---------------------------------------------------------|
| boolean add(E e)   | Adds to back, throws exception on failure               |
| boolean offer(E e) | Adds to back                                            |
| E element()        | Read from front, throws exception on failure            |
| E peek()           | Read from front                                         |
| E remove()         | Read and remove from front, throws exception on failure |
| E poll()           | Read and remove from front                              |

## Deque (Double Ended) methods

| Method                  | Description                                             |
|-------------------------|---------------------------------------------------------|
| boolean addFirst(E e)   | Adds to front, throws exception on failure              |
| boolean offerFirst(E e) | Adds to front                                           |
| boolean addLast(E e)    | Adds to back, throws exception on failure               |
| boolean offerLast(E e)  | Adds to back                                            |
| E getFirst()            | Read from front, throws exception on failure            |
| E peekFirst()           | Read from front                                         |
| E getLast()             | Read from back, throws exception on failure             |
| E peekLast()            | Read from back                                          |
| E removeFirst()         | Read and remove from front, throws exception on failure |
| E pollFirst()           | Read and remove from front                              |
| E removeLast()          | Read and remove from front, throws exception on failure |
| E pollLast()            | Read and remove from front                              |

## Deque (Stack / LIFO) methods

| Method         | Description                                    |
|----------------|------------------------------------------------|
| void push(E e) | Add to front, throws exception on failure      |
| E pop()        | Remove from front, throws exception on failure |
| E peek()       | Get first element                              |

## Map methods

| Method                                   | Description                                                                           |
|------------------------------------------|---------------------------------------------------------------------------------------|
| void clear()                             | Removes all keys and values from the map                                              |
| boolean containsKey()                    | Returns whether key is in map                                                         |
| boolean containsValue()                  | Returns whether value is in map                                                       |
| Set<Map.Entry> entrySet()                | Returns a set of map entries                                                          |
| void forEach(BiConsumer c)               | Loop through each key value pair                                                      |
| V get(Object k)                          | Gets the value for the key, or null                                                   |
| V getOrDefault(Object k, V defaultValue) | Gets the value for the key, or defaultValue                                           |
| boolean isEmpty()                        | Checks if the map is empty                                                            |
| V merge(K k, V v, Function f)            | Sets value if not set, runs function if value is set. Removes if value is null        |
| V put(K k, V v)                          | Adds or replaces the key value pair. Returns the old value, or null                   |                                                          
| V putIfAbsent(K k, V v)                  | Adds the value if the key is not yet set. Returns null if absent, or the value if set |
| V remove(Object k)                       | Removes and returns the value mapped to key                                           |
| V replace(K k, V v)                      | Replaces the value if set, returns original value or null                             |
| void replaceAll(BiFunction f)            | Replace each value with the function result                                           |
| int size()                               | Size of the map                                                                       |
| Collection values()                      | Returns Collection of all values                                                      |

## Comparator (static)

| Method                              | Description                                           |
|-------------------------------------|-------------------------------------------------------|
| comparing(Function f)               | Compares the collection by the result of the function |
| comparingDouble(ToDoubleFunction f) | Compares the collection by the result of the function |
| comparingInt(ToIntFunction f)       | Compares the collection by the result of the function |
| comparingLong(ToLongFunction f)     | Compares the collection by the result of the function |
| naturalOrder()                      | Sorts by using the Comparable                         |
| reverseOrder()                      | Sorts in the reverse of naturalOrder()                |

## Comparator (non-static)

| Method                                  | Description                                                                    |
|-----------------------------------------|--------------------------------------------------------------------------------|
| thenComparing(Function f)               | If the previous comparator returns 0, returns the result of this comparator    |
| thenComparingDouble(ToDoubleFunction f) | If the previous comparator returns 0, returns the result of this comparator    |
| thenComparingInt(ToIntFunction f)       | If the previous comparator returns null, returns the result of this comparator |
| thenComparingLong(ToLongFunction f)     | Compares the collection by the result of the function                          |
| reversed()                              | Reverses the order of the sort                                                 |