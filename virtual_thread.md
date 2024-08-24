```java
import java.util.concurrent.Executors;
import java.util.concurrent.ExecutorService;

public class Main {
  public static void main(String[] args) {
    // Create an ExecutorService with virtual threads
    try (ExecutorService executor = Executors.newVirtualThreadPerTaskExecutor()) {

      // Submit tasks to the executor
      for (int i = 0; i < 10; i++) {
        int taskId = i;
        executor.submit(() -> {
          // Simulate some work with a sleep
          try {
            Thread.sleep(1000);
          } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
          }
          // Print the task ID and thread name
          System.out.println("Task " + taskId + " executed by " + Thread.currentThread().threadId());
        });
      }

      // Shutdown the executor
      executor.shutdown();


      // Creating a virtual thread using the Thread.ofVirtual() factory method
      Thread virtualThread = Thread.ofVirtual().start(() -> {
        System.out.println("Running in a virtual thread: " + Thread.currentThread());
      });

      // Wait for the virtual thread to finish execution
      try {
        virtualThread.join();
      } catch (InterruptedException e) {
        e.printStackTrace();
      }

      System.out.println("Main thread finished execution");
    }
  }
}
```
```bash
Running in a virtual thread: VirtualThread[#42]/runnable@ForkJoinPool-1-worker-3
Main thread finished execution
Task 6 executed by 37
Task 7 executed by 38
Task 8 executed by 39
Task 0 executed by 30
Task 2 executed by 33
Task 3 executed by 34
Task 1 executed by 32
Task 4 executed by 35
Task 9 executed by 40
Task 5 executed by 36
```
