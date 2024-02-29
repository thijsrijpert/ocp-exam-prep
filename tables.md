# Oracle Certified Professional Java SE 17 Developer Tables

Overview of the tables you should know for the OCP Java exam

## Chapter 10

### Table 10.1
| Method                  | OptionalDouble              | OptionalInt              | OptionalLong              | When Optional is empty        | When Optional contains value |
|-------------------------|-----------------------------|--------------------------|---------------------------|-------------------------------|------------------------------|
| get()                   | getAsDouble()               | getAsInt()               | getAsLong()               | Throws exception              | Returns value                |
| ifPresent(Consumer c)   | ifPresent(DoubleConsumer c) | ifPresent(IntCustomer c) | ifPresent(LongCustomer c) | Does nothing                  | Calls Consumer with value    |
| isPresent()             | isPresent()                 | isPresent()              | isPresent()               | Returns false                 | Returns true                 |
| orElse(T other)         | orElse(double other)        | orElse(int other)        | orElse(long other)        | Returns other                 | Returns value                |
| orElseGet(Supplier s)   | orElseGet(DoubleSupplier s) | orElseGet(IntSupplier s) | orElseGet(LongSupplier s) | Returns result of supplier    | Returns value                |
| orElseThrow()           | orElseThrow()               | orElseThrow()            | orElseThrow()             | Throws NoSuchElementException | Returns value                |
| orElseThrow(Supplier s) | orElseThrow(Supplier s)     | orElseThrow(Supplier s)  | orElseThrow(Supplier s)   | Throws result of supplier     | Returns value                |

### Table 10.3

| Method                                                      | Finite             | Notes                                                                                                                                         |
|-------------------------------------------------------------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------|
| static Stream.empty()                                       | Finite             | Creates Stream with zero elements                                                                                                             |
| static Stream.of(varargs)                                   | Finite             | Creates Stream with listed elements                                                                                                           |
| collection.stream()                                         | Finite             | Creates Stream from collection                                                                                                                |
| collection.parallelStream()                                 | Finite             | Creates Stream from collection that can be run in parallel                                                                                    |
| static Stream.generate(Supplier s)                          | Infinite           | Creates Stream by calling the supplier for each element                                                                                       |
| static Stream.iterate(T seed, UnaryOperator o)              | Infinite           | Creates Stream by using the seed for the first element, and then calling o for each subsequent element upon request.                          |
| static Stream.iterate(T seed, UnaryOperator o, Predicate p) | Infinite or Finite | Creates Stream by using the seed for the first element, and then calling o for each subsequent element upon request. Stops if p returns false |

### Table 10.4

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

### Table 10.5

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

### Table 10.6 / 10.7

| Source       | Create Stream<T>              | Create DoubleStream                 | Create IntStream                | Create LongStream                 |
|--------------|-------------------------------|-------------------------------------|---------------------------------|-----------------------------------|
| Stream<T>    | map(Function<T, R> f)         | mapToDouble(ToDoubleFunction<T> f)  | mapToInt(ToIntFunction<T> f)    | mapToLong(ToLongFunction<T> f)    |
| DoubleStream | mapToObj(DoubleFunction<R> f) | map(DoubleUnaryOperator f)          | mapToInt(DoubleToIntFunction f) | mapToLong(DoubleToLongFunction f) |
| IntStream    | mapToObj(IntFunction<R> f)    | mapToDouble(IntToDoubleFunction f)  | map(IntUnaryOperator f)         | mapToLong(IntToLongFunction f)    |
| LongStream   | mapToObj(LongFunction<R> f)   | mapToDouble(LongToDoubleFunction f) | mapToInt(LongToIntFunction f)   | map(LongUnaryOperator f)          |

