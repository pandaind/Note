```java
import java.util.concurrent.*;

public class Test {
  public static void main(String[] args) throws InterruptedException {
    // ConcurrentHashMap example
    // ConcurrentHashMap is a thread-safe implementation of a hash map.
    // It allows concurrent read and write operations without locking the entire map.
    ConcurrentHashMap<String, Integer> concurrentMap = new ConcurrentHashMap<>();
    concurrentMap.put("A", 1);
    concurrentMap.put("B", 2);
    System.out.println("ConcurrentHashMap: " + concurrentMap);

    Runnable mapTask = () -> {
      for (int i = 0; i < 5; i++) {
        concurrentMap.put(Thread.currentThread().getName() + i, i);
      }
    };

    Thread mapThread1 = new Thread(mapTask);
    Thread mapThread2 = new Thread(mapTask);
    mapThread1.start();
    mapThread2.start();
    mapThread1.join();
    mapThread2.join();
    System.out.println("ConcurrentHashMap after threads: " + concurrentMap);

    // CopyOnWriteArrayList example
    // CopyOnWriteArrayList is a thread-safe variant of ArrayList.
    // It creates a new copy of the underlying array on every write operation.
    // This makes it suitable for scenarios where read operations are more frequent than write operations.
    CopyOnWriteArrayList<String> cowList = new CopyOnWriteArrayList<>();
    cowList.add("A");
    cowList.add("B");
    System.out.println("CopyOnWriteArrayList: " + cowList);

    Runnable listTask = () -> {
      for (int i = 0; i < 5; i++) {
        cowList.add(Thread.currentThread().getName() + i);
      }
    };

    Thread listThread1 = new Thread(listTask);
    Thread listThread2 = new Thread(listTask);
    listThread1.start();
    listThread2.start();
    listThread1.join();
    listThread2.join();
    System.out.println("CopyOnWriteArrayList after threads: " + cowList);

    // ConcurrentLinkedQueue example
    // ConcurrentLinkedQueue is a thread-safe implementation of a queue based on linked nodes.
    // It is an unbounded, thread-safe, and non-blocking queue.
    // It is best suited for scenarios where multiple threads produce and consume elements concurrently.
    ConcurrentLinkedQueue<String> concurrentQueue = new ConcurrentLinkedQueue<>();
    concurrentQueue.add("A");
    concurrentQueue.add("B");
    System.out.println("ConcurrentLinkedQueue: " + concurrentQueue);

    Runnable queueTask = () -> {
      for (int i = 0; i < 5; i++) {
        concurrentQueue.add(Thread.currentThread().getName() + i);
      }
    };

    Thread queueThread1 = new Thread(queueTask);
    Thread queueThread2 = new Thread(queueTask);
    queueThread1.start();
    queueThread2.start();
    queueThread1.join();
    queueThread2.join();
    System.out.println("ConcurrentLinkedQueue after threads: " + concurrentQueue);

    // CopyOnWriteArraySet example
    // CopyOnWriteArraySet is a thread-safe variant of a set backed by a CopyOnWriteArrayList.
    // It is best suited for scenarios where set size is small and read operations are more frequent than write operations.
    // It is implemented using CopyOnWriteArrayList internally.
    // It does not allow duplicate elements.
    // It is not suitable for scenarios where write operations are frequent.
    CopyOnWriteArraySet<String> cowSet = new CopyOnWriteArraySet<>();
    cowSet.add("A");
    cowSet.add("B");
    System.out.println("CopyOnWriteArraySet: " + cowSet);

    Runnable setTask = () -> {
      for (int i = 0; i < 5; i++) {
        cowSet.add(Thread.currentThread().getName() + i);
      }
    };

    Thread setThread1 = new Thread(setTask);
    Thread setThread2 = new Thread(setTask);
    setThread1.start();
    setThread2.start();
    setThread1.join();
    setThread2.join();
    System.out.println("CopyOnWriteArraySet after threads: " + cowSet);
  }
}
```
