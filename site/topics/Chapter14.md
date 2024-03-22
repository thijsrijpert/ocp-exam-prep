# Chapter 14 (I/O)

## File

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


## Path

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

## Files (All Static)

| Method                                                                                                                      | Description                                                                                                                                                                                                                                                                                       |
|-----------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| boolean deleteIfExists(Path p) throws IOException                                                                           | Deletes the file or directory if it exists, returns false if it does not exist                                                                                                                                                                                                                    |
| void delete(Path p) throws IOException                                                                                      | Same as above, but throws NoSuchFileException if file does not exist                                                                                                                                                                                                                              |
| boolean exists(Path p, LinkOption... o)                                                                                     | Checks if the file exists                                                                                                                                                                                                                                                                         |
| boolean isDirectory(Path p, LinkOption... o)                                                                                | Checks if the path points to a directory                                                                                                                                                                                                                                                          |
| boolean isRegularFile(Path p, LinkOption... o)                                                                              | Checks if the path points to a file                                                                                                                                                                                                                                                               |
| boolean isSymbolicLink(Path p)                                                                                              | Checks if the path is a symbolic link                                                                                                                                                                                                                                                             |
| boolean isHidden(Path p)                                                                                                    | Checks if the path has the attribute hidden                                                                                                                                                                                                                                                       |
| boolean isReadable(Path p)                                                                                                  | Checks if the path has the attribute readable                                                                                                                                                                                                                                                     |
| boolean isWritable(Path p)                                                                                                  | Checks if the path has the attribute writable                                                                                                                                                                                                                                                     |
| boolean isExecutable(Path p)                                                                                                | Checks if the path has the attribute executable                                                                                                                                                                                                                                                   |
| `A readAttributes(Path p, Class<A> type, LinkOption... o)`                                                                  | Gets a readonly view of the file or directory attributes. The type can be used to request Basic, Windows or Linux specific attributes                                                                                                                                                             |
| `A getFileAttributesView(Path p, Class<A> type, LinkOption... o)`                                                           | Gets a view of the file or directory attributes that can be used to update these attributes. The type can be used to request Basic, Windows or Linux specific attributes                                                                                                                          |
| FileTime getLastModifiedTime(Path p, LinkOption... o) throws IOException                                                    | Gets the time since it was last modified                                                                                                                                                                                                                                                          |
| long size(Path p) throws IOException                                                                                        | Gets the number of bytes in a file                                                                                                                                                                                                                                                                |
| `Steam<Path> list(Path p) throws IOException`                                                                               | Gets a stream of the content in the directory                                                                                                                                                                                                                                                     |
| `Steam<Path> walk(Path p, FileVisitOption... o) throws IOException`                                                         | Get a stream that contains a recursive depth-first list of all files in the directory. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException.                                                                                             |
| `Steam<Path> walk(Path p, int maxDepth, FileVisitOption... o) throws IOException`                                           | Get a stream that contains a recursive depth-first list of all files in the directory. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException. Only accesses files with depth of maxDepth                                                  |
| `Steam<Path> find(Path p, int maxDepth, BiPredicate<Path, BasicFileAttributes> p, FileVisitOption... o) throws IOException` | Get a stream that contains a recursive depth-first list of all files in the directory. Filters the contents of the stream by predicate. Does not follow symbolic links by default. If a loop exists on the walk method throws FileSystemLoopException. Only accesses files with depth of maxDepth |
| Path createDirectory(Path p, FileAttribute... a) throws IOException                                                         | Creates the directory                                                                                                                                                                                                                                                                             |
| Path createDirectories(Path p, FileAttribute... a) throws IOException                                                       | Creates the directory, recursively                                                                                                                                                                                                                                                                |
| Path move(Path src, Path dest, CopyOption... o) throws IOException                                                          | Renames the file                                                                                                                                                                                                                                                                                  |
| Path copy(Path src, Path dest, CopyOption... o) throws IOException                                                          | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| Path copy(InputStream src, Path dest, CopyOption... o) throws IOException                                                   | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| Path copy(Path src, OutputStream dest, CopyOption... o) throws IOException                                                  | Copies the file, not recursive                                                                                                                                                                                                                                                                    |
| boolean isSameFile(Path src, Path dest) throws IOException                                                                  | Checks if two files are physically the same. Throws exception if one of the two files do not exists, but always returns true if both paths are equal                                                                                                                                              |
| int mismatch(Path src, Path dest) throws IOException                                                                        | Returns -1 if the file contents are the same, returns the first index where the files differ if they mismatch                                                                                                                                                                                     |
| String readString(Path src) throws IOException                                                                              | Returns the entire file a string                                                                                                                                                                                                                                                                  |
| Path writeString(Path dest, CharSequence s, OpenOptions... o) throws IOException                                            | Writes the entire string to file                                                                                                                                                                                                                                                                  |
| Path write(Path dest, byte[] s, OpenOptions... o) throws IOException                                                        | Writes the entire byte array to file                                                                                                                                                                                                                                                              |
| `Path write(Path dest, List<String> s, OpenOptions... o) throws IOException`                                                | Writes the entire string line list to file                                                                                                                                                                                                                                                        |
| `byte[] readAllBytes(Path src) throws IOException`                                                                          | Returns the entire file a byte array                                                                                                                                                                                                                                                              |
| `List<String> readAllLines(Path src) throws IOException`                                                                    | Returns the entire file a list of lines                                                                                                                                                                                                                                                           |
| `Stream<String> lines(Path src) throws IOException`                                                                         | Returns the entire file a stream of lines (should be used in try with resources block)                                                                                                                                                                                                            |
| BufferedReader newBufferedReader(Path src) throws IOException                                                               | Creates a new buffered reader                                                                                                                                                                                                                                                                     |
| BufferedWriter newBufferedWriter(Path dest) throws IOException                                                              | Creates a new buffered writer                                                                                                                                                                                                                                                                     |


## Optional Parameters

### LinkOption

Interfaces: `CopyOption`, `OpenOption`  
`NOFOLLOW_LINKS`: Do not follow symbolic links

### StandardCopyOption

Interfaces: `CopyOption`  
`ATOMIC_MOVE`: Move file as atomic operation
`COPY_ATTRIBUTES`: Copy file attributes to new file
`REPLACE_EXISTING`: Overwrite file if it exists

### StandardOpenOption

Interfaces: `OpenOption`   
`APPEND`: If the file is open for write, append  
`CREATE`: Create new file if it does not exist  
`CREATE_NEW`: Create new file only if it does not exist; fail if the file exists  
`READ`: Open for read access  
`TRUNCATE_EXISTING`: If file is already open for write, truncate length to 0, append to the beginning  
`WRITE`: Open for write access

### FileVisitOption

Interfaces: None
`FOLLOW_LINKS`: Follow symbolic links


## File streams

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

## InputStream

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

## Reader

| Method                                     | Description                                                                                    |
|--------------------------------------------|------------------------------------------------------------------------------------------------|
| int read()                                 | Reads a byte, or returns -1 if no byte is available                                            |
| int read(char[] b)                         | Reads chars into buffer, returns number of chars read                                          |
| int read(char[] b, int offset, int length) | Reads chars into buffer, starting at offset and ending at length, returns number of chars read |
| void close()                               | Closes the resource, and flushes the data                                                      |

## OutputStream

| Method                                      | Description                                                           |
|---------------------------------------------|-----------------------------------------------------------------------|
| void write(int b)                           | Writes a byte                                                         |
| void write(byte[] b)                        | Writes byte array                                                     |
| void read(byte[] b, int offset, int length) | Writes bytes from byte array, starting at offset and ending at length |
| void flush()                                | Tells the OS to actually write data from RAM into the file            |
| void close()                                | Closes the resource, and flushes the data                             |

## Writer

| Method                                      | Description                                                           |
|---------------------------------------------|-----------------------------------------------------------------------|
| void write(int b)                           | Writes a byte                                                         |
| void write(char[] b)                        | Writes char array                                                     |
| void read(char[] b, int offset, int length) | Writes chars from byte array, starting at offset and ending at length |
| void flush()                                | Tells the OS to actually write data from RAM into the file            |
| void close()                                | Closes the resource, and flushes the data                             |


## Buffered

Buffered class extend the classes above, and thus have access to all of their methods

String readLine() for BufferedReader
void write(String line) for BufferedWriter
void newLine() for BufferedWriter

## ObjectStreams

The object streams have two important methods

Object readObject() throws IOException, ClassNotFoundException
void writeObject(Object o) throws IOException