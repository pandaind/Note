A semaphore is a synchronization mechanism used to control access to a common resource in concurrent programming. It uses a counter to manage the number of permits available for accessing the resource. Semaphores can be used to solve various synchronization problems like mutual exclusion, producer-consumer, and reader-writer problems.

### Pseudocode
1. Create a semaphore with a specified number of permits.
2. Define a shared resource.
3. Create multiple threads that will try to access the shared resource.
4. Each thread will:
   - Acquire a permit from the semaphore before accessing the resource.
   - Release the permit back to the semaphore after accessing the resource.

### Example Code
```java
import java.util.concurrent.Semaphore;

public class Main {
    // Create a semaphore with 1 permit (binary semaphore for mutual exclusion)
    private static final Semaphore semaphore = new Semaphore(1);
    // Shared resource
    private static int sharedResource = 0;

    public static void main(String[] args) {
        // Create and start multiple threads
        Thread t1 = new Thread(new Worker(), "Thread-1");
        Thread t2 = new Thread(new Worker(), "Thread-2");
        t1.start();
        t2.start();
    }

    static class Worker implements Runnable {
        @Override
        public void run() {
            try {
                // Acquire a permit before accessing the shared resource
                semaphore.acquire();
                System.out.println(Thread.currentThread().getName() + " acquired the semaphore.");
                
                // Access the shared resource
                sharedResource++;
                System.out.println(Thread.currentThread().getName() + " incremented sharedResource to " + sharedResource);
                
                // Simulate some work with the shared resource
                Thread.sleep(1000);
                
                // Release the permit after accessing the shared resource
                semaphore.release();
                System.out.println(Thread.currentThread().getName() + " released the semaphore.");
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }
    }
}
```

### Comments
- The `Semaphore` class is used to create a semaphore with a specified number of permits.
- The `acquire()` method is used to acquire a permit before accessing the shared resource. If no permits are available, the thread will block until a permit is released.
- The `release()` method is used to release a permit back to the semaphore after accessing the shared resource.
- In this example, a binary semaphore (with 1 permit) is used to ensure mutual exclusion, allowing only one thread to access the shared resource at a time.
