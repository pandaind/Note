```java
import java.util.concurrent.CountDownLatch;
import java.util.concurrent.CyclicBarrier;

public class Main {

    public static void main(String[] args) throws InterruptedException {
        // CountDownLatch example
        int latchCount = 3;
        CountDownLatch latch = new CountDownLatch(latchCount);

        Runnable latchTask = () -> {
            System.out.println(Thread.currentThread().getName() + " is working on CountDownLatch task");
            latch.countDown();
            System.out.println(Thread.currentThread().getName() + " has finished CountDownLatch task");
        };

        for (int i = 0; i < latchCount; i++) {
            new Thread(latchTask).start();
        }

        latch.await(); // Main thread waits until latch count reaches zero
        System.out.println("All CountDownLatch tasks are completed");

        // CyclicBarrier example
        int barrierCount = 3;
        CyclicBarrier barrier = new CyclicBarrier(barrierCount, () -> {
            System.out.println("All CyclicBarrier tasks are completed");
        });

        Runnable barrierTask = () -> {
            System.out.println(Thread.currentThread().getName() + " is working on CyclicBarrier task");
            try {
                barrier.await(); // Each thread waits at the barrier until all threads reach it
            } catch (Exception e) {
                e.printStackTrace();
            }
            System.out.println(Thread.currentThread().getName() + " has finished CyclicBarrier task");
        };

        for (int i = 0; i < barrierCount; i++) {
            new Thread(barrierTask).start();
        }
    }
}
```

**Explanation:**
- **CountDownLatch**: Used to make one or more threads wait until a set of operations being performed in other threads completes. The main thread waits until the latch count reaches zero.
- **CyclicBarrier**: Used to make a set of threads wait for each other to reach a common barrier point. Once all threads reach the barrier, they can proceed. The barrier can be reused after the waiting threads are released.
