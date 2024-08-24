Module 4: Parallelism and Performance

4.1 Parallel Streams in Java
- Introduction to Stream API
- Parallel Streams
- Best Practices and Performance Considerations

4.2 Fork/Join Framework
- Introduction to Fork/Join Framework
- RecursiveTask and RecursiveAction
- Work Stealing Algorithm

4.3 Performance Optimization Techniques
- Reducing Lock Contention
- Optimizing Thread Pools
- Profiling and Analyzing Multithreaded Applications


```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.RecursiveTask;
import java.util.stream.IntStream;

public class Main {
  public static void main(String[] args) {
    // Introduction to Stream API
    List<String> names = Arrays.asList("Alice", "Bob", "Charlie", "David", "Eve");
    names.stream()
        .filter(name -> name.startsWith("A"))
        .forEach(System.out::println); // Output: Alice

    // Parallel Streams
    IntStream.range(1, 100)
        .parallel()
        .filter(n -> n % 2 == 0)
        .forEach(System.out::print); // Outputs even numbers in parallel

    // Best Practices and Performance Considerations
    // Use parallel streams for large datasets and CPU-bound operations
    // Avoid using parallel streams for small datasets or IO-bound operations

    // Introduction to Fork/Join Framework
    ForkJoinPool forkJoinPool = new ForkJoinPool(2);
    int[] array = IntStream.range(1, 100).toArray();
    SumTask task = new SumTask(array, 0, array.length);
    int result = forkJoinPool.invoke(task);
    System.out.println("\nSum: " + result); // Output: Sum of numbers from 1 to 99

    // Performance Optimization Techniques
    // Reducing Lock Contention: Minimize synchronized blocks and use concurrent collections
    // Optimizing Thread Pools: Use appropriate thread pool sizes based on the workload
    // Profiling and Analyzing Multithreaded Applications: Use tools like VisualVM, JProfiler, etc.
  }
}

// RecursiveTask for Fork/Join Framework
class SumTask extends RecursiveTask<Integer> {
  private static final int THRESHOLD = 10;
  private int[] array;
  private int start;
  private int end;

  public SumTask(int[] array, int start, int end) {
    this.array = array;
    this.start = start;
    this.end = end;
  }

  @Override
  protected Integer compute() {
    if (end - start <= THRESHOLD) {
      int sum = 0;
      for (int i = start; i < end; i++) {
        sum += array[i];
      }
      return sum;
    } else {
      int mid = (start + end) / 2;
      SumTask leftTask = new SumTask(array, start, mid);
      SumTask rightTask = new SumTask(array, mid, end);
      leftTask.fork();
      int rightResult = rightTask.compute();
      int leftResult = leftTask.join();
      return leftResult + rightResult;
    }
  }
}
```
```bash
Alice
6664627274706858566054525090928816181422242046444846788076389822682848642409694323436283081210
Sum: 4950
```

`ForkJoinPool` to solve many recursive problems, especially those that can be broken down into smaller subproblems that can be solved in parallel. The `ForkJoinPool` is designed to work with tasks that can be recursively split into smaller tasks, which can then be executed concurrently.

Here is a step-by-step plan to solve a generic recursive problem using `ForkJoinPool`:

1. **Define the Recursive Task**: Create a class that extends `RecursiveTask` or `RecursiveAction` depending on whether you need a result or not.
2. **Implement the Compute Method**: In the `compute` method, define the base case and the recursive case. For the recursive case, split the task into smaller subtasks and use `fork` and `join` to execute them.
3. **Invoke the Task**: Create an instance of `ForkJoinPool` and use it to invoke the main task.

Here is an example of solving the Fibonacci sequence using `ForkJoinPool`:

```java
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.RecursiveTask;

// RecursiveTask for calculating Fibonacci numbers
class FibonacciTask extends RecursiveTask<Integer> {
    private final int n;

    public FibonacciTask(int n) {
        this.n = n;
    }

    @Override
    protected Integer compute() {
        if (n <= 1) {
            return n;
        }
        FibonacciTask f1 = new FibonacciTask(n - 1);
        FibonacciTask f2 = new FibonacciTask(n - 2);
        f1.fork(); // fork the first subtask
        return f2.compute() + f1.join(); // compute the second subtask and join the first
    }
}

public class Main {
    public static void main(String[] args) {
        ForkJoinPool forkJoinPool = new ForkJoinPool();
        int n = 10; // Example: Calculate the 10th Fibonacci number
        FibonacciTask task = new FibonacciTask(n);
        int result = forkJoinPool.invoke(task);
        System.out.println("Fibonacci number " + n + " is " + result);
    }
}
```
```bash
Fibonacci number 10 is 55
```

RecursiveAction Example

```java
import java.util.concurrent.ForkJoinPool;
import java.util.concurrent.RecursiveAction;

class PrintArrayTask extends RecursiveAction {
  private static final int THRESHOLD = 5;
  private int[] array;
  private int start;
  private int end;

  public PrintArrayTask(int[] array, int start, int end) {
    this.array = array;
    this.start = start;
    this.end = end;
  }

  @Override
  protected void compute() {
    if (end - start <= THRESHOLD) {
      for (int i = start; i < end; i++) {
        System.out.println(array[i]);
      }
    } else {
      int mid = (start + end) / 2;
      PrintArrayTask leftTask = new PrintArrayTask(array, start, mid);
      PrintArrayTask rightTask = new PrintArrayTask(array, mid, end);
      leftTask.fork();
      rightTask.compute();
      leftTask.join();
    }
  }
}

public class Main {
  public static void main(String[] args) {
    ForkJoinPool forkJoinPool = new ForkJoinPool();
    int[] array = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10};
    PrintArrayTask task = new PrintArrayTask(array, 0, array.length);
    forkJoinPool.invoke(task);
  }
}
```

```bash
6
7
8
9
10
1
2
3
4
5
```
