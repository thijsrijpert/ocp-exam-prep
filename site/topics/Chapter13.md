# Chapter 13 (Concurrency)

new Thread(runnable).start() ->  executes task on.
new thread(runnable).run() ->  executes task on this thread.

## Runnable

```
@FunctionalInterface
public interface Runnable {
    void run();
}
```
## Callable

```
@FunctionalInterface
public interface Callable<V> {
     V call() throws Exception;
}
```


## Table 13.1 (Executor Service)

| Method                                                          | Description                                                                                                             |
|-----------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| void execute(Runnable r)                                        | Executes Runnable task at some point in the future                                                                      |
| `Future<?> submit(Runnable r)`                                  | Executes Runnable task at some point in the future, returns a Future representing the task. future.get() is always null |
| `Future<T> submit(Callable<T> r)`                               | Executes Callable task at some point in the future, returns a Future representing the task                              |
| `List<Future<T> invokeAll(Collection<? extends Callable<T>> c)` | Executes Callable tasks and waits for them to complete, returns a list of Futures representing the tasks                |
| `T invokeAny(Collection<? extends Callable<T>> c)`              | Executes Callable tasks and waits for at least one to complete                                                          |
| void shutdown()                                                 | Don´t accept any new tasks, execute all accepted tasks before terminating                                               |
| void shutdownNow()                                              | Don´t accept any new tasks, try to terminate all accepted and running tasks                                             |
| void awaitTermination(long timeout, TimeUnit u)                 | Wait for the specified timeout till all tasks are executed before terminating, terminates sooner if all tasks are done  |

## Table 13.2 (Future)

| Method                                        | Description                                                                                   |
|-----------------------------------------------|-----------------------------------------------------------------------------------------------|
| boolean isDone()                              | True if completed, threw exception or was canceled                                            |
| boolean isCancelled                           | True if the task was canceled                                                                 |
| boolean cancel(boolean mayInterruptIfRunning) | Tries to cancel the task, true if successful, false if not cancelable or already completed    |
| V get()                                       | Returns the tasks result, waiting endlessly till a value is returned                          |
| V get(long timeout, TimeUnit u)               | Returns the tasks result, or a checked TimeoutException if it is not available before timeout |

## Table 13.3 (TimeUnit)

| Enum name    |
|--------------|
| NANOSECONDS  |
| MICROSECONDS |
| MILLISECONDS |
| SECONDS      |
| MINUTES      |
| HOURS        |
| DAYS         |

## Table 13.4 (ScheduledExecutorService)

| Method                                                                        | Description                                                                                         |
|-------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| `schedule(Callable<V> c, long delay, TimeUnit u)`                             | Creates and Executes task after delay                                                               |
| schedule(Runnable c, long delay, TimeUnit u)                                  | Creates and Executes task after delay                                                               |
| scheduleAtFixedRate(Runnable c, long initialDelay, long delay, TimeUnit u)    | Creates and Executes task at a fixed rate, after the initial delay is over                          |
| scheduleWithFixedDelay(Runnable c, long initialDelay, long delay, TimeUnit u) | Creates and Executes task at a fixed rate, only creating a new task after the previous task is over |

## Table 13.5 (Executors)

| Type                       | Method                             | Description                                                                                   |
|----------------------------|------------------------------------|-----------------------------------------------------------------------------------------------|
| ExecutorService            | newSingleThreadExecutor()          | Creates a single thread executor. Tasks are processed sequentially                            |
| ScheduledExecutorService   | newSingleThreadScheduledExecutor() | Creates a single thread executor. Tasks can be scheduled to run after a delay or periodically |
| ExecutorService            | newCachedThreadPool()              | Creates a thread pool that creates threads as needed. Reuses existing threads when available  |
| ExecutorService            | newFixedThreadPool(int x)          | Creates a thread pool with x amount of threads                                                |
| ScheduledExecutorService   | newScheduledThreadPool(int x)      | Creates a thread pool that can schedule tasks                                                 |

## Table 13.7 (Atomic)

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

## Table 13.8 (Locking)

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

## Table 13.9 (ConcurrentCollections)

| Class                 | Interface                                                           | Sorted | Blocking |
|-----------------------|---------------------------------------------------------------------|--------|----------|
| ConcurrentHashMap     | Map, ConcurrentMap                                                  | No     | No       |
| ConcurrentLinkedQueue | Queue                                                               | No     | No       |
| ConcurrentSkipListMap | Map, SortedMap, NavigableMap, ConcurrentMap, ConcurrentNavigableMap | Yes    | No       |
| ConcurrentSkipListSet | Set, SortedSet, NavigableSet                                        | Yes    | No       |
| CopyOnWriteArrayList  | List                                                                | No     | No       |
| CopyOnWriteArraySet   | Set                                                                 | No     | No       |
| LinkedBlockingQueue   | Queue, BlockingQueue                                                | No     | Yes      |

## Table 13.10 (Collections)

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
