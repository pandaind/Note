### Plan

1. **Create a `Phaser` instance**: This will be used to synchronize threads.
2. **Use `Phaser` as a `CountDownLatch`**:
   - Initialize the `Phaser` with the number of parties.
   - Each thread will arrive and deregister from the `Phaser`.
   - The main thread will wait for all parties to arrive.
3. **Use `Phaser` as a `CyclicBarrier`**:
   - Initialize the `Phaser` with the number of parties.
   - Each thread will arrive and wait for others.
   - The `Phaser` will advance to the next phase once all parties arrive.

### Code

```java
import java.util.concurrent.Phaser;

public class Main {

    public static void main(String[] args) {
        // Using Phaser as CountDownLatch
        Phaser phaserCountDownLatch = new Phaser(3); // 3 parties

        for (int i = 0; i < 3; i++) {
            new Thread(new Task(phaserCountDownLatch, "CountDownLatch")).start();
        }

        // Wait for all parties to arrive
        phaserCountDownLatch.awaitAdvance(0);
        System.out.println("All tasks completed using Phaser as CountDownLatch");

        // Using Phaser as CyclicBarrier
        Phaser phaserCyclicBarrier = new Phaser(3); // 3 parties

        for (int i = 0; i < 3; i++) {
            new Thread(new Task(phaserCyclicBarrier, "CyclicBarrier")).start();
        }

        // Wait for all parties to arrive
        phaserCyclicBarrier.awaitAdvance(0);
        System.out.println("All tasks completed using Phaser as CyclicBarrier");
    }

    static class Task implements Runnable {
        private Phaser phaser;
        private String type;

        Task(Phaser phaser, String type) {
            this.phaser = phaser;
            this.type = type;
        }

        @Override
        public void run() {
            System.out.println(Thread.currentThread().getName() + " started for " + type);
            try {
                Thread.sleep(1000); // Simulate work
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            if (type.equals("CountDownLatch")) {
                phaser.arriveAndDeregister();
            } else if (type.equals("CyclicBarrier")) {
                phaser.arriveAndAwaitAdvance();
            }
            System.out.println(Thread.currentThread().getName() + " completed for " + type);
        }
    }
}
```

This program demonstrates how to use `Phaser` as both a `CountDownLatch` and a `CyclicBarrier`.
