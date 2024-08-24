Module 5: Concurrency Design Patterns

5.1 Introduction to Concurrency Design Patterns
- Producer-Consumer Pattern
- Future Pattern
- Thread Pool Pattern

5.2 Practical Implementations
- Real-world examples using concurrency patterns
- Best Practices for Concurrency in Enterprise Applications

```java
import java.util.concurrent.*;

// Producer-Consumer Pattern
class Producer implements Runnable {
  private final BlockingQueue<Integer> queue;

  public Producer(BlockingQueue<Integer> queue) {
    this.queue = queue;
  }

  @Override
  public void run() {
    try {
      for (int i = 0; i < 10; i++) {
        queue.put(i);
        System.out.println("Produced: " + i);
      }
      queue.put(-1); // End signal
    } catch (InterruptedException e) {
      Thread.currentThread().interrupt();
    }
  }
}

class Consumer implements Runnable {
  private final BlockingQueue<Integer> queue;

  public Consumer(BlockingQueue<Integer> queue) {
    this.queue = queue;
  }

  @Override
  public void run() {
    try {
      while (true) {
        Integer value = queue.take();
        if (value == -1) break; // End signal
        System.out.println("Consumed: " + value);
      }
    } catch (InterruptedException e) {
      Thread.currentThread().interrupt();
    }
  }
}

// Future Pattern
class FutureTaskExample implements Callable<String> {
  @Override
  public String call() throws Exception {
    Thread.sleep(2000); // Simulate long computation
    return "Future result";
  }
}

// Thread Pool Pattern
class Task implements Runnable {
  private final int taskId;

  public Task(int taskId) {
    this.taskId = taskId;
  }

  @Override
  public void run() {
    System.out.println("Executing task " + taskId);
  }
}

public class Main {
  public static void main(String[] args) throws InterruptedException, ExecutionException {
    // Producer-Consumer Pattern
    BlockingQueue<Integer> queue = new ArrayBlockingQueue<>(10);
    Thread producerThread = new Thread(new Producer(queue));
    Thread consumerThread = new Thread(new Consumer(queue));
    producerThread.start();
    consumerThread.start();
    producerThread.join();
    consumerThread.join();

    // Future Pattern
    ExecutorService executor = Executors.newSingleThreadExecutor();
    Future<String> future = executor.submit(new FutureTaskExample());
    System.out.println("Future result: " + future.get());
    executor.shutdown();

    // Thread Pool Pattern
    ExecutorService threadPool = Executors.newFixedThreadPool(3);
    for (int i = 0; i < 5; i++) {
      threadPool.execute(new Task(i));
    }
    threadPool.shutdown();
  }
}
```
```bash
Consumed: 0
Produced: 0
Produced: 1
Produced: 2
Produced: 3
Produced: 4
Produced: 5
Produced: 6
Produced: 7
Produced: 8
Produced: 9
Consumed: 1
Consumed: 2
Consumed: 3
Consumed: 4
Consumed: 5
Consumed: 6
Consumed: 7
Consumed: 8
Consumed: 9
Future result: Future result
Executing task 0
Executing task 1
Executing task 4
Executing task 2
Executing task 3
```
