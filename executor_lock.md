Module 3: Advanced Thread Concepts

3.1 Concurrency Utilities (java.util.concurrent)
- Introduction to Concurrency API
- Executors Framework
- Executor, ExecutorService, ThreadPoolExecutor
- ScheduledExecutorService
- Callable and Future

3.2 Lock Framework
- ReentrantLock and ReentrantReadWriteLock
- Condition Variables
- StampedLock

3.3 Atomic Variables
- AtomicInteger, AtomicLong, and AtomicReference
- Compare-And-Swap (CAS) Mechanism
- Performance Considerations


```java
import java.util.concurrent.*;
import java.util.concurrent.locks.*;
import java.util.concurrent.atomic.*;

public class Main {
  public static void main(String[] args) throws InterruptedException, ExecutionException {
    // 3.1 Concurrency Utilities (java.util.concurrent)
    // Executors Framework
    ExecutorService executorService = Executors.newFixedThreadPool(2);

    // Callable and Future
    Callable<Integer> task = () -> {
      System.out.println(Thread.currentThread().getName() + " - Callable task started");
      TimeUnit.SECONDS.sleep(1);
      System.out.println(Thread.currentThread().getName() + " - Callable task completed");
      return 123;
    };
    Future<Integer> future = executorService.submit(task);
    System.out.println("Future result: " + future.get());

    // ScheduledExecutorService
    ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(1);
    scheduledExecutorService.schedule(() -> System.out.println(Thread.currentThread().getName() + " - Scheduled task executed"), 1, TimeUnit.SECONDS);

    // 3.2 Lock Framework
    // ReentrantLock and ReentrantReadWriteLock
    ReentrantLock lock = new ReentrantLock();
    Runnable lockTask = () -> {
      System.out.println(Thread.currentThread().getName() + " - Attempting to lock");
      lock.lock();
      try {
        System.out.println(Thread.currentThread().getName() + " - Locked section");
      } finally {
        lock.unlock();
        System.out.println(Thread.currentThread().getName() + " - Unlocked section");
      }
    };
    executorService.submit(lockTask);
    executorService.submit(lockTask);

    ReentrantReadWriteLock readWriteLock = new ReentrantReadWriteLock();
    ReentrantReadWriteLock.ReadLock readLock = readWriteLock.readLock();
    ReentrantReadWriteLock.WriteLock writeLock = readWriteLock.writeLock();

    Runnable readLockTask = () -> {
      System.out.println(Thread.currentThread().getName() + " - Attempting to read lock");
      readLock.lock();
      try {
        System.out.println(Thread.currentThread().getName() + " - Read lock section");
      } finally {
        readLock.unlock();
        System.out.println(Thread.currentThread().getName() + " - Read unlock section");
      }
    };

    Runnable writeLockTask = () -> {
      System.out.println(Thread.currentThread().getName() + " - Attempting to write lock");
      writeLock.lock();
      try {
        System.out.println(Thread.currentThread().getName() + " - Write lock section");
      } finally {
        writeLock.unlock();
        System.out.println(Thread.currentThread().getName() + " - Write unlock section");
      }
    };
    executorService.submit(readLockTask);
    executorService.submit(readLockTask);
    executorService.submit(writeLockTask);
    executorService.submit(writeLockTask);

    // Condition Variables
    Condition condition = lock.newCondition();
    Runnable conditionTask = () -> {
      System.out.println(Thread.currentThread().getName() + " - Attempting to lock for condition");
      lock.lock();
      try {
        System.out.println(Thread.currentThread().getName() + " - Waiting for condition");
        condition.await(1, TimeUnit.SECONDS);
        System.out.println(Thread.currentThread().getName() + " - Condition met");
        condition.signal();
      } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
      } finally {
        lock.unlock();
        System.out.println(Thread.currentThread().getName() + " - Unlocked after condition");
      }
    };
    executorService.submit(conditionTask);

    // StampedLock
    StampedLock stampedLock = new StampedLock();
    Runnable stampedLockTask = () -> {
      System.out.println(Thread.currentThread().getName() + " - Attempting to write lock with stamp");
      long stamp = stampedLock.writeLock();
      try {
        System.out.println(Thread.currentThread().getName() + " - Stamped lock write section");
      } finally {
        stampedLock.unlockWrite(stamp);
        System.out.println(Thread.currentThread().getName() + " - Stamped lock write unlock section");
      }
    };
    executorService.submit(stampedLockTask);

    // 3.3 Atomic Variables
    // AtomicInteger, AtomicLong, and AtomicReference
    AtomicInteger atomicInteger = new AtomicInteger(0);
    atomicInteger.incrementAndGet();
    System.out.println("AtomicInteger: " + atomicInteger.get());

    AtomicLong atomicLong = new AtomicLong(0L);
    atomicLong.incrementAndGet();
    System.out.println("AtomicLong: " + atomicLong.get());

    AtomicReference<String> atomicReference = new AtomicReference<>("initial");
    atomicReference.set("updated");
    System.out.println("AtomicReference: " + atomicReference.get());

    // Compare-And-Swap (CAS) Mechanism
    int expectedValue = 0;
    int newValue = 1;
    boolean wasUpdated = atomicInteger.compareAndSet(expectedValue, newValue);
    System.out.println("CAS was updated: " + wasUpdated);

    // Performance Considerations
    // Atomic variables and locks have different performance characteristics.
    // Use atomic variables for simple operations and locks for more complex scenarios.

    executorService.shutdown();
    scheduledExecutorService.shutdown();
  }
}
```

```bash
pool-1-thread-1 - Callable task started
pool-1-thread-1 - Callable task completed
Future result: 123
pool-1-thread-1 - Attempting to lock
pool-1-thread-2 - Attempting to lock
pool-1-thread-1 - Locked section
pool-1-thread-1 - Unlocked section
pool-1-thread-2 - Locked section
pool-1-thread-2 - Unlocked section
pool-1-thread-1 - Attempting to read lock
pool-1-thread-2 - Attempting to read lock
pool-1-thread-1 - Read lock section
pool-1-thread-2 - Read lock section
pool-1-thread-1 - Read unlock section
pool-1-thread-2 - Read unlock section
pool-1-thread-1 - Attempting to write lock
pool-1-thread-2 - Attempting to write lock
pool-1-thread-1 - Write lock section
pool-1-thread-2 - Write lock section
pool-1-thread-1 - Write unlock section
pool-1-thread-2 - Write unlock section
pool-1-thread-1 - Attempting to lock for condition
pool-1-thread-1 - Waiting for condition
pool-1-thread-2 - Attempting to write lock with stamp
pool-1-thread-2 - Stamped lock write section
pool-1-thread-2 - Stamped lock write unlock section
AtomicInteger: 1
AtomicLong: 1
AtomicReference: updated
CAS was updated: false
pool-1-thread-1 - Condition met
pool-2-thread-1 - Scheduled task executed
pool-1-thread-1 - Unlocked after condition
```
