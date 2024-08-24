### CountdownLatch Example

**Pseudocode:**
1. Create a `CountDownLatch` with a count of 3.
2. Create and start 3 worker threads that perform some task and then call `countDown()` on the latch.
3. In the main thread, call `await()` on the latch to wait for all worker threads to finish.

```java
import java.util.concurrent.CountDownLatch;

public class Main {
    public static void main(String[] args) throws InterruptedException {
        CountDownLatch latch = new CountDownLatch(3);

        Runnable worker = () -> {
            try {
                // Simulate work
                Thread.sleep((long) (Math.random() * 1000));
                System.out.println(Thread.currentThread().getName() + " finished work");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            } finally {
                latch.countDown();
            }
        };

        for (int i = 0; i < 3; i++) {
            new Thread(worker).start();
        }

        latch.await(); // Wait for all workers to finish
        System.out.println("All workers finished");
    }
}
```

### Phaser Example

**Pseudocode:**
1. Create a `Phaser` with a count of 1 (for the main thread).
2. Create and start 3 worker threads that register with the phaser, perform some task, and then arrive and deregister.
3. In the main thread, wait for all worker threads to arrive at the phaser.

```java
import java.util.concurrent.Phaser;

public class Main {
    public static void main(String[] args) {
        Phaser phaser = new Phaser(1); // Register main thread

        Runnable worker = () -> {
            phaser.register();
            try {
                // Simulate work
                Thread.sleep((long) (Math.random() * 1000));
                System.out.println(Thread.currentThread().getName() + " finished work");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            } finally {
                phaser.arriveAndDeregister();
            }
        };

        for (int i = 0; i < 3; i++) {
            new Thread(worker).start();
        }

        phaser.arriveAndAwaitAdvance(); // Wait for all workers to finish
        System.out.println("All workers finished");
    }
}
```
