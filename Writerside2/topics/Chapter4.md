# Chapter 4 (Core APIs)

## String

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

## Format characters

| Format char | Description                                            |
|-------------|--------------------------------------------------------|
| %s          | Any type, commonly String                              |
| %d          | Any integer like value, such as int or long            |
| %f          | Any floating point like value, such as float or double |
| %n          | Adds linebreak                                         |

Using the wrong format char results in a IllegalFormatConversionException

## StringBuilder

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

## Arrays (All static)

All of these methods have primitive variations

| Method                           | Description                                                                                                                                                                                                                             |
|----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| toString(Object[] o)             | Creates a pretty string representation of the array                                                                                                                                                                                     |
| sort(Object[] o)                 | Sorts the object to its natural order                                                                                                                                                                                                   |
| binarySearch(Object[] o, Object) | Searches for an element on a sorted element, returns undefined result if array is not sorted. Returns the index of the match or the where it needs to be inserted index * 1 -1                                                          |
| compare(Object[] o, Object[] o)  | Both arrays are equal if they have the same values and length. Array is smaller if they have the same values, but the other has extra elements. If the value of an index is different, the one with the smaller index value is smaller. |
| mismatch(Object[] o, Object[] o) | Returns -1 if the arrays are the same. Returns the index that is different if the arrays are different.                                                                                                                                 |


## Math API (All static)

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

## Date & Time API

The modification methods are called plusXXXX() and minusXXXX().

### LocalDate

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

### LocalTime

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

### LocalDateTime

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

### ZonedDateTime

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
