### Plan
1. **Explain `LongAdder`**: A class designed for high-concurrency scenarios where multiple threads update a common sum.
2. **Explain `LongAccumulator`**: A class that allows for custom accumulation functions, useful for more complex operations than simple addition.
3. **Provide Example**: Show how to use both `LongAdder` and `LongAccumulator` in a multi-threaded environment.

### Explanation
- **`LongAdder`**: 
  - Optimized for scenarios where multiple threads frequently update a common sum.
  - Internally maintains a set of variables (cells) to reduce contention.
  - Use `add` method to add values and `sum` method to get the current total.

- **`LongAccumulator`**:
  - Allows for custom accumulation functions.
  - Use `accumulate` method to apply the function and `get` method to retrieve the result.

### Example Code

```java
import java.util.concurrent.atomic.LongAdder;
import java.util.concurrent.atomic.LongAccumulator;

public class Main {
    public static void main(String[] args) throws InterruptedException {
        // Example using LongAdder
        LongAdder adder = new LongAdder();
        Runnable adderTask = () -> {
            for (int i = 0; i < 1000; i++) {
                adder.increment();
            }
        };

        Thread[] adderThreads = new Thread[10];
        for (int i = 0; i < 10; i++) {
            adderThreads[i] = new Thread(adderTask);
            adderThreads[i].start();
        }
        for (Thread t : adderThreads) {
            t.join();
        }
        System.out.println("LongAdder sum: " + adder.sum());

        // Example using LongAccumulator
        LongAccumulator accumulator = new LongAccumulator(Long::sum, 0);
        Runnable accumulatorTask = () -> {
            for (int i = 0; i < 1000; i++) {
                accumulator.accumulate(1);
            }
        };

        Thread[] accumulatorThreads = new Thread[10];
        for (int i = 0; i < 10; i++) {
            accumulatorThreads[i] = new Thread(accumulatorTask);
            accumulatorThreads[i].start();
        }
        for (Thread t : accumulatorThreads) {
            t.join();
        }
        System.out.println("LongAccumulator sum: " + accumulator.get());
    }
}
```

### Summary
- **`LongAdder`**: Efficient for high-concurrency addition.
- **`LongAccumulator`**: Flexible for custom accumulation functions.
