# Oracle Certified Professional Java SE 17 Developer Tables

Overview of the tables you should know for the OCP Java exam

<!-- TOC -->
* [Oracle Certified Professional Java SE 17 Developer Tables](#oracle-certified-professional-java-se-17-developer-tables)
  * [Chapter 4](#chapter-4)
    * [String](#string)
    * [Format characters](#format-characters)
    * [StringBuilder](#stringbuilder)
  * [Chapter 10](#chapter-10)
    * [Table 10.1](#table-101)
    * [Table 10.3](#table-103)
    * [Table 10.4](#table-104)
    * [Table 10.5](#table-105)
    * [Table 10.6 / 10.7](#table-106--107)
    * [Table 10.9](#table-109)
    * [Table 10.10](#table-1010)
  * [Chapter 13](#chapter-13)
    * [Runnable](#runnable)
    * [Callable](#callable)
    * [Table 13.1 (Executor Service)](#table-131-executor-service)
    * [Table 13.2 (Future)](#table-132-future)
    * [Table 13.3 (TimeUnit)](#table-133-timeunit)
    * [Table 13.4 (ScheduledExecutorService)](#table-134-scheduledexecutorservice)
    * [Table 13.5 (Executors)](#table-135-executors)
    * [Table 13.7 (Atomic)](#table-137-atomic)
    * [Table 13.8 (Locking)](#table-138-locking)
    * [Table 13.9 (ConcurrentCollections)](#table-139-concurrentcollections)
    * [Table 13.10 (Collections)](#table-1310-collections)
  * [Chapter 14 (I/O)](#chapter-14-io)
    * [File](#file)
    * [Path](#path)
    * [Files (All Static)](#files-all-static)
    * [Optional Parameters](#optional-parameters)
      * [LinkOption](#linkoption)
      * [StandardCopyOption](#standardcopyoption)
      * [StandardOpenOption](#standardopenoption)
      * [FileVisitOption](#filevisitoption)
    * [File streams](#file-streams)
    * [InputStream](#inputstream)
    * [Reader](#reader)
    * [OutputStream](#outputstream)
    * [Writer](#writer)
    * [Buffered](#buffered)
    * [ObjectStreams](#objectstreams)
<!-- TOC -->

## Chapter 4

### String

| Method                                                        | Description                                                                                                                                                                                                               |
|---------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| int length()                                                  | Gets the length of the string                                                                                                                                                                                             |
| char charAt(int i)                                            | Gets the char at a specific position                                                                                                                                                                                      |
| int indexOf(int ch)                                           | Gets the first index of the char                                                                                                                                                                                          |
| int indexOf(int ch, int fromIndex)                            | Gets the first index of the char, starting at fromIndex                                                                                                                                                                   |
| int indexOf(String str)                                       | Gets the first index of the string. Returns the first index of the matching string. So test.indexOf("es") returns 1                                                                                                       |
| int indexOf(String str, int fromIndex)                        | Gets the first index of the string,  starting at fromIndex. Returns the first index of the matching string. So test.indexOf("es") returns 1                                                                               |
| String substring(int beginIndex)                              | Gets a substring, starting at the beginIndex (inclusive)                                                                                                                                                                  |
| String substring(int beginIndex, int endIndex)                | Gets a substring, starting at the beginIndex (inclusive), ending at endIndex (exclusive)                                                                                                                                  |
| String toUpperCase()                                          | Converts the string to uppercase letters                                                                                                                                                                                  |
| String toLowerCase()                                          | Converts the string to lowercase letters                                                                                                                                                                                  |
| boolean equalsIgnoreCase(String str)                          | Checks if the strings are equal ignoring the case                                                                                                                                                                         |
| boolean startsWith(String prefix)                             | Checks if the string starts with prefix                                                                                                                                                                                   |
| boolean endsWith(String suffix)                               | Checks if the string ends with suffix                                                                                                                                                                                     |
| boolean contains(CharSequence charSeq)                        | Checks if the string contains the supplied sequence                                                                                                                                                                       |
| String replace(char old, char new)                            | Replaces all occurrences of a char with another char                                                                                                                                                                      |
| String replace(CharSequence old, CharSequence new)            | Replaces all occurrences of a sequence with another sequence                                                                                                                                                              |
| String trim()                                                 | Removes whitespace from the start and end of string ( \t, \n and \r are also included)                                                                                                                                    |
| String strip()                                                | Same as trim() but with unicode support                                                                                                                                                                                   |
| String stripLeading()                                         | Same as strip(), but only removes from the beginning                                                                                                                                                                      |
| String stripTrailing()                                        | Same as strip(), but only removes from the end                                                                                                                                                                            |
| String indent(int i)                                          | Adds i amount of spaces to the beginning of each line. Negative values mean i amount of spaces are removed from the beginning of each line. It also changes all line breaks to \n and adds an \n to the end of the string |
| String stripIndent()                                          | Removes all incidental whitespace, so the same amount of whitespace characters are removed from the string. It also changes all line breaks to \n.                                                                        |
| String translateEscapes()                                     | Removes the extra backslash from escaped escape characters so that the escape character is actually used.                                                                                                                 |
| boolean isEmpty()                                             | Checks if the string is truly empty, no whitespace allowed                                                                                                                                                                |
| boolean isBlank()                                             | Checks if the string is empty or only contains whitespace characters                                                                                                                                                      |
| static String format(String format, Object... args)           | Replaces format characters with the supplied arguments                                                                                                                                                                    |
| static String format(Locale l, String format, Object... args) | Replaces format characters with the supplied arguments                                                                                                                                                                    |
| String formatted(Object... args)                              | Replaces format characters with the supplied arguments                                                                                                                                                                    |
| String intern()                                               | Pull a string with the same value from the string pool so it can be used with == and literals                                                                                                                             |                                                      

### Format characters

| Format char | Description                                            |
|-------------|--------------------------------------------------------|
| %s          | Any type, commonly String                              |
| %d          | Any integer like value, such as int or long            |
| %f          | Any floating point like value, such as float or double |
| %n          | Adds linebreak                                         |

Using the wrong format char results in a IllegalFormatConversionException

### StringBuilder

The StringBuilder has four constructors empty, with supplied String / CharSequence or with an initial capacity.

| Method                                                     | Description                                                                                                                                                    |
|------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SB append(String s)                                        | StringBuilder has a large amount of append methods for all sorts of data types. It uses String.valueOf() if it cannot be appended directly                     |
| SB insert(int offset, String str)                          | Inserts a string (or another object like append) into the specified offset                                                                                     |
| SB delete(int startIndex, int endIndex)                    | Deletes the chars starting at startIndex (inclusive) and ending at endIndex (exclusive). Does not throw an exception if the endIndex is larger than the length |
| SB deleteCharAt(int index)                                 | Deletes the char at the specified position                                                                                                                     |
| SB replace(int startIndex, int endIndex, String newString) | This method first executes a delete and then inserts the newString at the old position                                                                         |
| SB reverse()                                               | Reverses the string                                                                                                                                            |
| int length()                                               | Gets the length of the string                                                                                                                                  |
| char charAt(int i)                                         | Gets the char at a specific position                                                                                                                           | 
| int indexOf(String str)                                    | Gets the first index of the string. Returns the first index of the matching string. So test.indexOf("es") returns 1                                            |
| int indexOf(String str, int fromIndex)                     | Gets the first index of the string,  starting at fromIndex. Returns the first index of the matching string. So test.indexOf("es") returns 1                    |
| String substring(int beginIndex)                           | Gets a substring, starting at the beginIndex (inclusive)                                                                                                       |
| String substring(int beginIndex, int endIndex)             | Gets a substring, starting at the beginIndex (inclusive), ending at endIndex (exclusive)                                                                       |

### Arrays (All static)

All of these methods have primitive variations

| Method                           | Description                                                                                                                                                                                                                             |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| toString(Object[] o)             | Creates a pretty string representation of the array                                                                                                                                                                                     |
| sort(Object[] o)                 | Sorts the object to its natural order                                                                                                                                                                                                   |
| binarySearch(Object[] o, Object) | Searches for an element on a sorted element, returns undefined result if array is not sorted. Returns the index of the match or the where it needs to be inserted index * 1 -1                                                          |
| compare(Object[] o, Object[] o)  | Both arrays are equal if they have the same values and length. Array is smaller if they have the same values, but the other has extra elements. If the value of an index is different, the one with the smaller index value is smaller. |
| mismatch(Object[] o, Object[] o) | Returns -1 if the arrays are the same. Returns the index that is different if the arrays are different.                                                                                                                                 |


### Math API (All static)

| Method                                   | Description                                                |
|------------------------------------------|------------------------------------------------------------|
| double min(double a, double b)           | Gets the lowest value                                      |
| float min(float a, float b)              | Gets the lowest value                                      |
| int min(int a, int b)                    | Gets the lowest value                                      |
| long min(long a, long b)                 | Gets the lowest value                                      |
| double max(double a, double b)           | Gets the highest value                                     |
| float max(float a, float b)              | Gets the highest value                                     |
| int max(int a, int b)                    | Gets the highest value                                     |
| long max(long a, long b)                 | Gets the highest value                                     |
| long round(double a, double b)           | Rounds to the closest whole value  0.5 results in 1        |
| int round(float a, float b)              | Rounds to the closest whole value. 0.5 results in 1        |
| double ceil(double a, double b)          | Rounds up to the closest whole value. 0.1 results in 1.0   |
| double floor(double a, double b)         | Rounds down to the closest whole value. 0.9 results in 0.0 |
| double pow(double base, double exponent) | Does base ^ exponent. Gets the power of base.              |
| double random()                          | Gets a random number greater than 0 and smaller than 1     |

### Date & Time API

The modification methods are called plusXXXX() and minusXXXX().

#### LocalDate

toString format: `yyyy-MM-dd`

| Method                                       | Description                                                               |
|----------------------------------------------|---------------------------------------------------------------------------|
| static LocalDate now()                       | Gets the current date                                                     |
| static LocalDate of(int y, int M, int d)     | Builds the date                                                           |
| static LocalDate of(int y, Month M, int d)   | Builds the date                                                           |
| boolean isBefore(LocalDate d)                | True if the value is earlier than the parameter                           |
| boolean isAfter(LocalDate d)                 | True if the value is later than the parameter                             |
| LocalDate plus(long amount, TemporalUnit u)  | Returns the new value, throws exception if units lower than a day is used |
| LocalDate minus(long amount, TemporalUnit u) | Returns the new value, throws exception if units lower than a day is used |
| LocalDate plus(TemporalAmount amount)        | Returns the new value, throws exception if duration is supplied           |
| LocalDate minus(long amount, TemporalUnit u) | Returns the new value, throws exception if duration is supplied           |

#### LocalTime

toString format: `HH:mm:ss.SSS`

| Method                                             | Description                                                                    |
|----------------------------------------------------|--------------------------------------------------------------------------------|
| static LocalTime now()                             | Gets the current time                                                          |
| static LocalTime of(int h, int m)                  | Builds the time                                                                |
| static LocalTime of(int h, int m, int s)           | Builds the time                                                                |
| static LocalTime of(int h, int m, int s, int nano) | Builds the time                                                                |
| boolean isBefore(LocalTime d)                      | True if the value is earlier than the parameter                                |
| boolean isAfter(LocalTime d)                       | True if the value is later than the parameter                                  |
| LocalDate plus(long amount, TemporalUnit u)        | Returns the new value, throws exception if units larger than half days is used |
| LocalDate minus(long amount, TemporalUnit u)       | Returns the new value, throws exception if units larger than half days is used |
| LocalDate plus(TemporalAmount amount)              | Returns the new value, throws exception if period is supplied                  |
| LocalDate minus(long amount, TemporalUnit u)       | Returns the new value, throws exception if period is supplied                  |

#### LocalDateTime

toString format: `yyyy-MM-ddTHH:mm:ss.SSS`

| Method                                                                         | Description                                     |
|--------------------------------------------------------------------------------|-------------------------------------------------|
| static LocalDateTime now()                                                     | Gets the current date & time                    |
| static LocalDateTime of(int y, Month M, int d, int h, int m)                   | Builds the datetime                             |
| static LocalDateTime of(int y, Month M, int d, int h, int m, int s)            | Builds the datetime                             |
| static LocalDateTime of(int y, Month M, int d, int h, int m, int s, int nanos) | Builds the datetime                             |
| static LocalDateTime of(int y, int M, int d, int h, int m)                     | Builds the datetime                             |
| static LocalDateTime of(int y, int M, int d, int h, int m, int s)              | Builds the datetime                             |
| static LocalDateTime of(int y, int M, int d, int h, int m, int s, int nanos)   | Builds the datetime                             |
| static LocalDateTime of(LocalDate d, LocalTime t)                              | Builds the datetime                             |
| boolean isBefore(LocalDateTime d)                                              | True if the value is earlier than the parameter |
| boolean isAfter(LocalDateTime d)                                               | True if the value is later than the parameter   |
| LocalDate plus(long amount, TemporalUnit u)                                    | Returns the new value                           |
| LocalDate minus(long amount, TemporalUnit u)                                   | Returns the new value                           |
| LocalDate plus(TemporalAmount amount)                                          | Returns the new value                           |
| LocalDate minus(long amount, TemporalUnit u)                                   | Returns the new value                           |

#### ZonedDateTime

toString format: `yyyy-MM-ddTHH:mm:ss.SSS xxx[VV]`

| Method                                                                                  | Description                                     |
|-----------------------------------------------------------------------------------------|-------------------------------------------------|
| static ZonedDateTime now()                                                              | Gets the current date & time                    |
| static ZonedDateTime of(int y, int M, int d, int h, int m, int s, int nanos, ZoneId id) | Builds the zoned datetime                       |
| static ZonedDateTime of(LocalDate d, LocalTime t, ZoneId id)                            | Builds the zoned datetime                       |
| static ZonedDateTime of(LocalDateTime dt, ZoneId id)                                    | Builds the zoned datetime                       |
| boolean isBefore(ZonedDateTime d)                                                       | True if the value is earlier than the parameter |
| boolean isAfter(ZonedDateTime d)                                                        | True if the value is later than the parameter   |
| LocalDate plus(long amount, TemporalUnit u)                                             | Returns the new value                           |
| LocalDate minus(long amount, TemporalUnit u)                                            | Returns the new value                           |
| LocalDate plus(TemporalAmount amount)                                                   | Returns the new value                           |
| LocalDate minus(long amount, TemporalUnit u)                                            | Returns the new value                           |
| ZoneOffset getOffset()                                                                  | Returns the timezone                            |



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

### Table 10.9

| Method                               | Notes                                                                                                                                                               |
|--------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Spliterator<T> trySplit()            | Returns a spliterator containing ideally half the data, which is removed from the current spliterator. Will return null when the spliterator is no longer splitable |
| void forEachRemaining(Consumer<T> c) | Process each remaining element                                                                                                                                      |
| boolean tryAdvance(Consumer<T> c)    | Process a single element if any remain. Returns true if it processed any element                                                                                    |

### Table 10.10

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

## Chapter 13

new Thread(runnable).start() ->  executes task on new thread
new Thread(runnable).run() ->  executes task on this thread

### Runnable

```
@FunctionalInterface
public interface Runnable {
    void run();
}
```
### Callable

```
@FunctionalInterface
public interface Callable<V> {
     V call() throws Exception;
}
```


### Table 13.1 (Executor Service)

| Method                                                        | Description                                                                                                             |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| void execute(Runnable r)                                      | Executes Runnable task at some point in the future                                                                      |
| Future<?> submit(Runnable r)                                  | Executes Runnable task at some point in the future, returns a Future representing the task. future.get() is always null |
| Future<T> submit(Callable<T> r)                               | Executes Callable task at some point in the future, returns a Future representing the task                              |
| List<Future<T> invokeAll(Collection<? extends Callable<T>> c) | Executes Callable tasks and waits for them to complete, returns a list of Futures representing the tasks                |
| T invokeAny(Collection<? extends Callable<T>> c)              | Executes Callable tasks and waits for at least one to complete                                                          |
| void shutdown()                                               | Don´t accept any new tasks, execute all accepted tasks before terminating                                               |
| void shutdownNow()                                            | Don´t accept any new tasks, try to terminate all accepted and running tasks                                             |
| void awaitTermination(long timeout, TimeUnit u)               | Wait for the specified timeout till all tasks are executed before terminating, terminates sooner if all tasks are done  |

### Table 13.2 (Future)

| Method                                        | Description                                                                                   |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------|
| boolean isDone()                              | True if completed, threw exception or was canceled                                            |
| boolean isCancelled                           | True if the task was canceled                                                                 |
| boolean cancel(boolean mayInterruptIfRunning) | Tries to cancel the task, true if successful, false if not cancelable or already completed    |
| V get()                                       | Returns the tasks result, waiting endlessly till a value is returned                          |
| V get(long timeout, TimeUnit u)               | Returns the tasks result, or a checked TimeoutException if it is not available before timeout |

### Table 13.3 (TimeUnit)

| Enum name    |
|--------------|
| NANOSECONDS  |
| MICROSECONDS |
| MILLISECONDS |
| SECONDS      |
| MINUTES      |
| HOURS        |
| DAYS         |

### Table 13.4 (ScheduledExecutorService)

| Method                                                                        | Description                                                                                         |
|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| schedule(Callable<V> c, long delay, TimeUnit u)                               | Creates and Executes task after delay                                                               |
| schedule(Runnable c, long delay, TimeUnit u)                                  | Creates and Executes task after delay                                                               |
| scheduleAtFixedRate(Runnable c, long initialDelay, long delay, TimeUnit u)    | Creates and Executes task at a fixed rate, after the initial delay is over                          |
| scheduleWithFixedDelay(Runnable c, long initialDelay, long delay, TimeUnit u) | Creates and Executes task at a fixed rate, only creating a new task after the previous task is over |

### Table 13.5 (Executors)

| Type                       | Method                             | Description                                                                                   |
|----------------------------|------------------------------------|-----------------------------------------------------------------------------------------------|
| ExecutorService            | newSingleThreadExecutor()          | Creates a single thread executor. Tasks are processed sequentially                            |
| ScheduledExecutorService   | newSingleThreadScheduledExecutor() | Creates a single thread executor. Tasks can be scheduled to run after a delay or periodically |
| ExecutorService            | newCachedThreadPool()              | Creates a thread pool that creates threads as needed. Reuses existing threads when available  |
| ExecutorService            | newFixedThreadPool(int x)          | Creates a thread pool with x amount of threads                                                |
| ScheduledExecutorService   | newScheduledThreadPool(int x)      | Creates a thread pool that can schedule tasks                                                 |

### Table 13.7 (Atomic)

There are three Atomic classes AtomicBoolean, AtomicInteger and AtomicLong.

| Method                              | Equivalent       | Description                               |
|-------------------------------------|------------------|-------------------------------------------|
| get()                               | property         | Retrieves the current values              |
| set(int\|long\|boolean value)       | property = value |                                           |
| getAndSet(int\|long\|boolean value) |                  | Sets the new value, returns the old value |
| incrementAndGet()                   | ++property       |                                           |
| getAndIncrement()                   | property++       |                                           |
| decrementAndGet()                   | --property       |                                           |
| getAndDecrement                     | property++       |                                           |

### Table 13.8 (Locking)

| Method                                    | Description                                                                                                         |
|-------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| void lock()                               | Requests lock, and blocks until it gets a lock                                                                      |
| void unlock()                             | Releases lock                                                                                                       |
| boolean tryLock()                         | Requests lock, returns boolean indicating if it got a lock                                                          |
| boolean tryLock(long timeout, TimeUnit u) | Requests lock, blocks unit it gets a lock or until the timeout expired. Returns boolean indicating if it got a lock |

Cyclic barrier has the following constructors

```
CyclicBarrier(int limit)
CyclicBarrier(int limit, Runnable r)
```

It triggers a barrier with the `await()` method.

### Table 13.9 (ConcurrentCollections)

| Class                 | Interface                                                           | Sorted | Blocking |
|-----------------------|---------------------------------------------------------------------|--------|----------|
| ConcurrentHashMap     | Map, ConcurrentMap                                                  | No     | No       |
| ConcurrentLinkedQueue | Queue                                                               | No     | No       |
| ConcurrentSkipListMap | Map, SortedMap, NavigableMap, ConcurrentMap, ConcurrentNavigableMap | Yes    | No       |
| ConcurrentSkipListSet | Set, SortedSet, NavigableSet                                        | Yes    | No       |
| CopyOnWriteArrayList  | List                                                                | No     | No       |
| CopyOnWriteArraySet   | Set                                                                 | No     | No       |
| LinkedBlockingQueue   | Queue, BlockingQueue                                                | No     | Yes      |

### Table 13.10 (Collections)

| Method                                   |
|------------------------------------------|
| synchronizedCollection(Collection c)     |
| synchronizedList(List l)                 |
| synchronizedMap(Map m)                   |
| synchronizedNavigableMap(NavigableMap m) |
| synchronizedNavigableSet(NavigableSet s) |
| synchronizedSet(Set s)                   |
| synchronizedSortedSet(SortedSet s)       |
| synchronizedSortedMap(SortedMap m)       |


## Chapter 14 (I/O)

### File

| Method                            | Description                                                 |
|-----------------------------------|-------------------------------------------------------------|
| File(String path)                 | Constructor, does not create file only a reference          |
| File(String parent, String child) | Constructor, does not create file only a reference          |
| File(File parent, String child)   | Constructor, does not create file only a reference          |
| String getName()                  | Gets the name of the file or directory, without the parent  |
| String getParent()                | Gets the parent directory or null if there is none          |
| boolean isAbsolute()              | Checks if the path is absolute                              |
| String getAbsolutePath()          | Converts the relative path to absolute path if not already  |
| boolean delete()                  | Deletes file or directory                                   |
| boolean exists()                  | Checks if the file exists                                   |
| boolean isDirectory()             | Checks if the file is a directory                           |
| boolean isFile()                  | Checks if the file is a file                                |
| long lastModified()               | Gets the last modified date in milliseconds since the epoch |
| long length()                     | Retrieves the number of bytes in a file                     |
| File[] listFiles()                | Lists the contents of a directory                           |
| boolean mkdir()                   | Creates directory                                           |
| boolean mkdirs()                  | Creates directories recursively                             |
| boolean renameTo(File f)          | Creates directories recursively                             |
| Path toPath()                     | Converts the file object to a path                          |


### Path

| Method                                            | Description                                                              |
|---------------------------------------------------|--------------------------------------------------------------------------|
| static Path Path.of(String first, String... more) | Constructor, does not create file only a reference                       |
| static Path Path.of(URI uri)                      | Constructor, does not create file only a reference                       |
| File Path.toFile()                                | Converts the path object to a (legacy) file                              |
| Path getFileName()                                | Gets the name of the file or directory, without the parent               |
| Path getParent()                                  | Gets the parent directory or null if there is none                       |
| boolean isAbsolute()                              | Checks if the path is absolute                                           |
| Path toAbsolutePath()                             | Converts the relative path to absolute path if not already               |
| String toString()                                 | Converts the path to string                                              |
| Path getName(int index)                           | Get a single segment                                                     |
| int getNameCount()                                | Get the number of segments                                               |
| Path subpath(int beginIndex, int endIndex)        | Get the segments between beginIndex (inclusive) and endIndex (exclusive) |
| Path getRoot()                                    | Get the top level segment (c:/ on Windows) (/ on linux)                  |
| Path resolve(String p)                            | Concat the parameter to the path                                         |
| Path resolve(Path p)                              | Concat the parameter to the path                                         |
| Path relativize(Path p)                           | Create a relative path from the path to the parameter                    |
| Path normalize()                                  | Remove redundant parts of the path                                       |
| Path toRealPath()                                 | Resolves symbolic links to find the actual path object                   |

### Files (All Static)

| Method                                                                                                                    | Description                                                                                                                                                                                                                                                                                       |
|---------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| boolean deleteIfExists(Path p) throws IOException                                                                         | Deletes the file or directory if it exists, returns false if it does not exist                                                                                                                                                                                                                    |
| void delete(Path p) throws IOException                                                                                    | Same as above, but throws NoSuchFileException if file does not exist                                                                                                                                                                                                                              |
| boolean exists(Path p, LinkOption... o)                                                                                   | Checks if the file exists                                                                                                                                                                                                                                                                         |
| boolean isDirectory(Path p, LinkOption... o)                                                                              | Checks if the path points to a directory                                                                                                                                                                                                                                                          |
| boolean isRegularFile(Path p, LinkOption... o)                                                                            | Checks if the path points to a file                                                                                                                                                                                                                                                               |
| boolean isSymbolicLink(Path p)                                                                                            | Checks if the path is a symbolic link                                                                                                                                                                                                                                                             |
| boolean isHidden(Path p)                                                                                                  | Checks if the path has the attribute hidden                                                                                                                                                                                                                                                       |
| boolean isReadable(Path p)                                                                                                | Checks if the path has the attribute readable                                                                                                                                                                                                                                                     |
| boolean isWritable(Path p)                                                                                                | Checks if the path has the attribute writable                                                                                                                                                                                                                                                     |
| boolean isExecutable(Path p)                                                                                              | Checks if the path has the attribute executable                                                                                                                                                                                                                                                   |
| A readAttributes(Path p, Class<A> type, LinkOption... o)                                                                  | Gets a readonly view of the file or directory attributes. The type can be used to request Basic, Windows or Linux specific attributes                                                                                                                                                             |
| A getFileAttributesView(Path p, Class<A> type, LinkOption... o)                                                           | Gets a view of the file or directory attributes that can be used to update these attributes. The type can be used to request Basic, Windows or Linux specific attributes                                                                                                                          |
| FileTime getLastModifiedTime(Path p, LinkOption... o) throws IOException                                                  | Gets the time since it was last modified                                                                                                                                                                                                                                                          |
| long size(Path p) throws IOException                                                                                      | Gets the number of bytes in a file                                                                                                                                                                                                                                                                |
| Steam<Path> list(Path p) throws IOException                                                                               | Gets a stream of the content in the directory                                                                                                                                                                                                                                                     |
| Steam<Path> walk(Path p, FileVisitOption... o) throws IOException                                                         | Get a stream that contains a recursive depth-first list of all files in the directory. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException.                                                                                             |
| Steam<Path> walk(Path p, int maxDepth, FileVisitOption... o) throws IOException                                           | Get a stream that contains a recursive depth-first list of all files in the directory. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException. Only accesses files with depth of maxDepth                                                  |
| Steam<Path> find(Path p, int maxDepth, BiPredicate<Path, BasicFileAttributes> p, FileVisitOption... o) throws IOException | Get a stream that contains a recursive depth-first list of all files in the directory. Filters the contents of the stream by predicate. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException. Only accesses files with depth of maxDepth |
| Path createDirectory(Path p, FileAttribute... a) throws IOException                                                       | Creates the directory                                                                                                                                                                                                                                                                             |
| Path createDirectories(Path p, FileAttribute... a) throws IOException                                                     | Creates the directory, recursively                                                                                                                                                                                                                                                                |
| Path move(Path src, Path dest, CopyOption... o) throws IOException                                                        | Renames the file                                                                                                                                                                                                                                                                                  |
| Path copy(Path src, Path dest, CopyOption... o) throws IOException                                                        | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| Path copy(InputStream src, Path dest, CopyOption... o) throws IOException                                                 | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| Path copy(Path src, OutputStream dest, CopyOption... o) throws IOException                                                | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| boolean isSameFile(Path src, Path dest) throws IOException                                                                | Checks if two files are physically the same. Throws exception if one of the two files do not exists, but always returns true if both paths are equal                                                                                                                                              |
| int mismatch(Path src, Path dest) throws IOException                                                                      | Returns -1 if the file contents are the same, returns the first index where the files differ if they mismatch                                                                                                                                                                                     |
| String readString(Path src) throws IOException                                                                            | Returns the entire file a string                                                                                                                                                                                                                                                                  |
| Path writeString(Path dest, CharSequence s, OpenOptions... o) throws IOException                                          | Writes the entire string to file                                                                                                                                                                                                                                                                  |
| Path write(Path dest, byte[] s, OpenOptions... o) throws IOException                                                      | Writes the entire byte array to file                                                                                                                                                                                                                                                              |
| Path write(Path dest, List<String> s, OpenOptions... o) throws IOException                                                | Writes the entire string line list to file                                                                                                                                                                                                                                                        |
| byte[] readAllBytes(Path src) throws IOException                                                                          | Returns the entire file a byte array                                                                                                                                                                                                                                                              |
| List<String> readAllLines(Path src) throws IOException                                                                    | Returns the entire file a list of lines                                                                                                                                                                                                                                                           |
| Stream<String> lines(Path src) throws IOException                                                                         | Returns the entire file a stream of lines (should be used in try with resources block)                                                                                                                                                                                                            |
| BufferedReader newBufferedReader(Path src) throws IOException                                                             | Creates a new buffered reader                                                                                                                                                                                                                                                                     |
| BufferedWriter newBufferedWriter(Path dest) throws IOException                                                            | Creates a new buffered writer                                                                                                                                                                                                                                                                     |



### Optional Parameters

#### LinkOption

Interfaces: `CopyOption`, `OpenOption`  
`NOFOLLOW_LINKS`: Do not follow symbolic links  

#### StandardCopyOption

Interfaces: `CopyOption`  
`ATOMIC_MOVE`: Move file as atomic operation
`COPY_ATTRIBUTES`: Copy file attributes to new file
`REPLACE_EXISTING`: Overwrite file if it exists

#### StandardOpenOption

Interfaces: `OpenOption`   
`APPEND`: If the file is open for write, append  
`CREATE`: Create new file if it does not exist  
`CREATE_NEW`: Create new file only if it does not exist; fail if the file exists  
`READ`: Open for read access  
`TRUNCATE_EXISTING`: If file is already open for write, truncate length to 0, append to the beginning  
`WRITE`: Open for write access

#### FileVisitOption

Interfaces: None
`FOLLOW_LINKS`: Follow symbolic links


### File streams

| Class                | Level  | Description                                                          |
|----------------------|--------|----------------------------------------------------------------------|
| FileInputStream      | Low    | Reads bytes from file                                                |
| FileOutputStream     | Low    | Writes bytes to file                                                 |
| FileReader           | Low    | Reads chars from file                                                |
| FileWriter           | Low    | Writes chars to file                                                 |
| BufferedInputStream  | High   | Reads bytes from file, buffers input to increase efficiency          |
| BufferedOutputStream | High   | Writes bytes to file, buffers output to increase efficiency          |
| BufferedReader       | High   | Reads chars from file, buffers input to increase efficiency          |
| BufferedWriter       | High   | Writes chars to file, buffers output to increase efficiency          |
| ObjectInputStream    | High   | Deserializes Java primitives and object types from input stream      |
| ObjectOutputStream   | High   | Serializes Java primitives and object types to output stream         |
| PrintStream          | High   | Writes formatted representations of Java objects to binary stream    |
| PrintWriter          | High   | Writes formatted representations of Java objects to character stream |

### InputStream

| Method                                     | Description                                                                                                                                            |
|--------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| int read()                                 | Reads a byte, or returns -1 if no byte is available                                                                                                    |
| int read(byte[] b)                         | Reads bytes into buffer, returns number of bytes read                                                                                                  |
| int read(byte[] b, int offset, int length) | Reads bytes into buffer, starting at offset and ending at length, returns number of bytes read                                                         |
| byte[] readAllBytes()                      | Reads all bytes into byte array                                                                                                                        |
| void close()                               | Closes the resource, and flushes the data                                                                                                              |
| boolean markSupported()                    | Checks if the mark feature is supported                                                                                                                |
| void mark(int readLimit)                   | Sets the point for the stream to be reset to                                                                                                           |
| void reset()                               | Resets the stream to the marked points, might throw exception if the amount of bytes that have been processed since mark is larger than the read limit |
| long skip(long n)                          | Skips n amount of bytes                                                                                                                                |

### Reader

| Method                                     | Description                                                                                    |
|--------------------------------------------|------------------------------------------------------------------------------------------------|
| int read()                                 | Reads a byte, or returns -1 if no byte is available                                            |
| int read(char[] b)                         | Reads chars into buffer, returns number of chars read                                          |
| int read(char[] b, int offset, int length) | Reads chars into buffer, starting at offset and ending at length, returns number of chars read |
| void close()                               | Closes the resource, and flushes the data                                                      |

### OutputStream

| Method                                      | Description                                                           |
|---------------------------------------------|-----------------------------------------------------------------------|
| void write(int b)                           | Writes a byte                                                         |
| void write(byte[] b)                        | Writes byte array                                                     |
| void read(byte[] b, int offset, int length) | Writes bytes from byte array, starting at offset and ending at length |
| void flush()                                | Tells the OS to actually write data from RAM into the file            |
| void close()                                | Closes the resource, and flushes the data                             |

### Writer

| Method                                      | Description                                                           |
|---------------------------------------------|-----------------------------------------------------------------------|
| void write(int b)                           | Writes a byte                                                         |
| void write(char[] b)                        | Writes char array                                                     |
| void read(char[] b, int offset, int length) | Writes chars from byte array, starting at offset and ending at length |
| void flush()                                | Tells the OS to actually write data from RAM into the file            |
| void close()                                | Closes the resource, and flushes the data                             |


### Buffered

Buffered class extend the classes above, and thus have access to all of their methods

String readLine() for BufferedReader
void write(String line) for BufferedWriter
void newLine() for BufferedWriter

### ObjectStreams

The object streams have two important methods

Object readObject() throws IOException, ClassNotFoundException
void writeObject(Object o) throws IOException


