## Concurrency Basics

### Thread vs Process
- Process: Independent program with its own memory space.

- Thread: Lightweight unit of execution within a process, shares memory with other threads.

- Multiple threads can run concurrently inside one process.
------
### ExecutorService Basics
- Provides a framework for managing threads.

- Simplifies thread creation and lifecycle management.

```
import java.util.concurrent.*;

ExecutorService executor = Executors.newFixedThreadPool(2);
executor.submit(() -> System.out.println("Task 1 running"));
executor.submit(() -> System.out.println("Task 2 running"));
executor.shutdown();
```

-----

### Race Condition Awareness
- Occurs when multiple threads access shared data simultaneously without proper synchronization.

- Can lead to inconsistent or unexpected results.

- Example: Two threads updating the same counter variable.
----------
### Synchronization Basics
- Ensures that only one thread accesses a critical section at a time.

- Achieved using synchronized keyword, locks, or concurrency utilities.

```
class Counter {
    private int count = 0;
    public synchronized void increment() {
        count++;
    }
    public int getCount() {
        return count;
    }
}
```

## Summary

- Concurrency requires understanding threads vs processes, using ExecutorService for thread management, and applying synchronization to avoid race conditions.