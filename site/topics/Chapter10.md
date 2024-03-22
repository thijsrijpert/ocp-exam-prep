# Chapter 10 (Streams)

## Table 10.1
| Method                  | OptionalDouble              | OptionalInt              | OptionalLong              | When Optional is empty        | When Optional contains value |
|-------------------------|-----------------------------|--------------------------|---------------------------|-------------------------------|------------------------------|
| get()                   | getAsDouble()               | getAsInt()               | getAsLong()               | Throws exception              | Returns value                |
| ifPresent(Consumer c)   | ifPresent(DoubleConsumer c) | ifPresent(IntCustomer c) | ifPresent(LongCustomer c) | Does nothing                  | Calls Consumer with value    |
| isPresent()             | isPresent()                 | isPresent()              | isPresent()               | Returns false                 | Returns true                 |
| orElse(T other)         | orElse(double other)        | orElse(int other)        | orElse(long other)        | Returns other                 | Returns value                |
| orElseGet(Supplier s)   | orElseGet(DoubleSupplier s) | orElseGet(IntSupplier s) | orElseGet(LongSupplier s) | Returns result of supplier    | Returns value                |
| orElseThrow()           | orElseThrow()               | orElseThrow()            | orElseThrow()             | Throws NoSuchElementException | Returns value                |
| orElseThrow(Supplier s) | orElseThrow(Supplier s)     | orElseThrow(Supplier s)  | orElseThrow(Supplier s)   | Throws result of supplier     | Returns value                |

## Table 10.3

| Method                                                      | Finite             | Notes                                                                                                                                         |
|-------------------------------------------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| static Stream.empty()                                       | Finite             | Creates Stream with zero elements                                                                                                             |
| static Stream.of(varargs)                                   | Finite             | Creates Stream with listed elements                                                                                                           |
| collection.stream()                                         | Finite             | Creates Stream from collection                                                                                                                |
| collection.parallelStream()                                 | Finite             | Creates Stream from collection that can be run in parallel                                                                                    |
| static Stream.generate(Supplier s)                          | Infinite           | Creates Stream by calling the supplier for each element                                                                                       |
| static Stream.iterate(T seed, UnaryOperator o)              | Infinite           | Creates Stream by using the seed for the first element, and then calling o for each subsequent element upon request.                          |
| static Stream.iterate(T seed, UnaryOperator o, Predicate p) | Infinite or Finite | Creates Stream by using the seed for the first element, and then calling o for each subsequent element upon request. Stops if p returns false |

## Table 10.4

| Method                                                                  | What happens for infinite streams | Return value | Reduction | Notes                                       |
|-------------------------------------------------------------------------|-----------------------------------|--------------|-----------|---------------------------------------------|
| count()                                                                 | Does not terminate                | long         | Yes       |                                             |
| min(Comparator c)                                                       | Does not terminate                | Optional     | Yes       |                                             |
| max(Comparator c)                                                       | Does not terminate                | Optional     | Yes       |                                             |
| findAny()                                                               | Terminates                        | Optional     | No        |                                             |
| findFirst()                                                             | Terminates                        | Optional     | No        |                                             |
| allMatch(Predicate p)                                                   | Sometimes terminates              | boolean      | No        |                                             |
| anyMatch(Predicate p)                                                   | Sometimes terminates              | boolean      | No        |                                             |
| noneMatch(Predicate p)                                                  | Sometimes terminates              | boolean      | No        |                                             |
| forEach(Consumer c)                                                     | Does not terminate                | void         | No        |                                             |
| reduce(BinaryOperator o)                                                | Does not terminate                | Optional     | Yes       |                                             |
| reduce(T identity, BinaryOperator o)                                    | Does not terminate                | T            | Yes       |                                             |
| reduce(T identity, BinaryOperator accumulator, BinaryOperator combiner) | Does not terminate                | T            | Yes       | For reducing to a different type / parallel |
| collect(Supplier<T> s, BiConsumer accumulator, BiConsumer combiner)     | Does not terminate                | T            | Yes       |                                             |
| collect(Collector c)                                                    | Does not terminate                | T            | Yes       |                                             |

## Table 10.5

| Method                                        | Primitive Stream | Description                                                  |
|-----------------------------------------------|------------------|--------------------------------------------------------------|
| OptionalDouble average()                      | IntStream        | Arithmetic mean                                              |
| OptionalDouble average()                      | LongStream       | Arithmetic mean                                              |
| OptionalDouble average()                      | DoubleStream     | Arithmetic mean                                              |
| Stream<T> boxed()                             | IntStream        | Convert to Object Stream                                     |
| Stream<T> boxed()                             | LongStream       | Convert to Object Stream                                     |
| Stream<T> boxed()                             | DoubleStream     | Convert to Object Stream                                     |
| OptionalInt max()                             | IntStream        | Max element of the stream (No Comparator required)           |
| OptionalLong max()                            | LongStream       | Max element of the stream (No Comparator required)           |
| OptionalDouble max()                          | DoubleStream     | Max element of the stream (No Comparator required)           |
| OptionalInt min()                             | IntStream        | Min element of the stream (No Comparator required)           |
| OptionalLong min()                            | LongStream       | Min element of the stream (No Comparator required)           |
| OptionalDouble min()                          | DoubleStream     | Min element of the stream (No Comparator required)           |
| int sum()                                     | IntStream        | Sum of the stream                                            |
| long sum()                                    | LongStream       | Sum of the stream                                            |
| double sum()                                  | DoubleStream     | Sum of the stream                                            |
| IntSummaryStatistics summaryStatistics()      | IntStream        | Returns an object containing: average, min, max, sum & count |
| LongSummaryStatistics summaryStatistics()     | LongStream       | Returns an object containing: average, min, max, sum & count |
| DoubleSummaryStatistics summaryStatistics()   | DoubleStream     | Returns an object containing: average, min, max, sum & count |
| static IntStream range(int a, int b)          | IntStream        | Returns primitive stream from a (inclusive) to b (exclusive) |
| static LongStream range(int a, int b)         | LongStream       | Returns primitive stream from a (inclusive) to b (exclusive) |
| static DoubleStream range(int a, int b)       | DoubleStream     | Returns primitive stream from a (inclusive) to b (exclusive) |
| static IntStream rangeClosed(int a, int b)    | IntStream        | Returns primitive stream from a (inclusive) to b (inclusive) |
| static LongStream rangeClosed(int a, int b)   | LongStream       | Returns primitive stream from a (inclusive) to b (inclusive) |
| static DoubleStream rangeClosed(int a, int b) | DoubleStream     | Returns primitive stream from a (inclusive) to b (inclusive) |

## Table 10.6 / 10.7

| Source       | Create Stream<T>              | Create DoubleStream                 | Create IntStream                | Create LongStream                 |
|--------------|-------------------------------|-------------------------------------|---------------------------------|-----------------------------------|
| Stream<T>    | map(Function<T, R> f)         | mapToDouble(ToDoubleFunction<T> f)  | mapToInt(ToIntFunction<T> f)    | mapToLong(ToLongFunction<T> f)    |
| DoubleStream | mapToObj(DoubleFunction<R> f) | map(DoubleUnaryOperator f)          | mapToInt(DoubleToIntFunction f) | mapToLong(DoubleToLongFunction f) |
| IntStream    | mapToObj(IntFunction<R> f)    | mapToDouble(IntToDoubleFunction f)  | map(IntUnaryOperator f)         | mapToLong(IntToLongFunction f)    |
| LongStream   | mapToObj(LongFunction<R> f)   | mapToDouble(LongToDoubleFunction f) | mapToInt(LongToIntFunction f)   | map(LongUnaryOperator f)          |

## Table 10.9

| Method                               | Notes                                                                                                                                                               |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Spliterator<T> trySplit()            | Returns a spliterator containing ideally half the data, which is removed from the current spliterator. Will return null when the spliterator is no longer splitable |
| void forEachRemaining(Consumer<T> c) | Process each remaining element                                                                                                                                      |
| boolean tryAdvance(Consumer<T> c)    | Process a single element if any remain. Returns true if it processed any element                                                                                    |

## Table 10.10

| Collector                                                   | Notes                                                                                                                                                             | Return value when passed to collect |
|-------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------|
| averagingDouble(ToDoubleFunction f)                         | Calculate average                                                                                                                                                 | Double                              |
| averagingInt(TIntFunction f)                                | Calculate average                                                                                                                                                 | Double                              |
| averagingLong(ToLongFunction f)                             | Calculate average                                                                                                                                                 | Double                              |
| counting()                                                  | Counts number of elements                                                                                                                                         | Long                                |
| filtering(Predicate p, Collector c)                         | Filters before running the downstream collector                                                                                                                   | R                                   |
| groupingBy(Function f)                                      | Creates a Map with List as value grouping the values by the result of the function                                                                                | Map<K, List<T>>                     |
| groupingBy(Function f, Collector dc)                        | Creates a Map grouping the values by the result of the function. Uses the dc to determine the value (eg. use set vs list vs concat)                               | Map<K, T>                           |
| groupingBy(Function f, Supplier s, Collector dc)            | Creates a Map grouping the values by the result of the function. Use s to set the type of map. Uses the dc to determine the value (eg. use set vs list vs concat) | Map<K, T>                           |
| joining(CharSequence cs)                                    | Creates a single string using a delimiter specified in cs.                                                                                                        | String                              |
| maxBy(Comparator c)                                         | Find the largest element                                                                                                                                          | Optional                            |
| minBy(Comparator c)                                         | Find the smallest element                                                                                                                                         | Optional                            |
| mapping(Function f, Collector dc)                           | Adds another level of collectors                                                                                                                                  | Collector                           |
| partitioningBy(Predicate p)                                 | Creates map grouping by specified predicate                                                                                                                       | Map<Boolean, List<T>>               |
| partitioningBy(Predicate p, Collector dc)                   | Creates map grouping by specified predicate. Uses the dc to determine the value (eg. use set vs list vs concat)                                                   | Map<Boolean, T>                     |
| summarizingDouble(ToDoubleFunction f)                       | Calculate the statistics of this stream (eg. min, max, sum, count)                                                                                                | DoubleSummaryStatistics             |
| summarizingInt(ToIntFunction f)                             | Calculate the statistics of this stream (eg. min, max, sum, count)                                                                                                | IntSummaryStatistics                |
| summarizingLong(ToLongFunction f)                           | Calculate the statistics of this stream (eg. min, max, sum, count)                                                                                                | LongSummaryStatistics               |
| summingDouble(ToDoubleFunction f)                           | Calculate the sum of the contents of this stream                                                                                                                  | Double                              |
| summingInt(ToIntFunction f)                                 | Calculate the sum of the contents of this stream                                                                                                                  | Integer                             |
| summingLong(ToLongFunction f)                               | Calculate the sum of the contents of this stream                                                                                                                  | Long                                |
| teeing(Collector c1, Collector c2, BiFunction f)            | Both Collectors are executed for all stream values, after the BiFunction is called to merge the two results                                                       | R                                   |
| toList()                                                    | Creates a List                                                                                                                                                    | List                                |
| toSet()                                                     | Creates a Set                                                                                                                                                     | Set                                 |
| toCollection(Supplier s)                                    | Creates a Collection of specified type                                                                                                                            | Collection                          |
| toMap(Function k, Function v)                               | Use function k to determine the key, and function v to determine the value                                                                                        | Map<K, V>                           |
| toMap(Function k, Function v, BinaryOperator m)             | Use function k to determine the key, and function v to determine the value. Use operator m to resolve duplicates                                                  | Map<K, V>                           |
| toMap(Function k, Function v, BinaryOperator m, Supplier s) | Use function k to determine the key, and function v to determine the value. Use operator m to resolve duplicates. Use supplier s to set the type of map used.     | Map<K, V>                           |
