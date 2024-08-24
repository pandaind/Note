**Pseudocode:**
1. Import necessary classes from `java.util.concurrent`.
2. Create a class `ExchangerExample`.
3. Inside the class, define the `main` method.
4. Create an `Exchanger` object for exchanging `String` data.
5. Create two `Runnable` tasks:
   - Task 1: Exchange a message with Task 2.
   - Task 2: Exchange a message with Task 1.
6. Create and start two threads to run the tasks.
7. Use `exchanger.exchange` method to exchange messages between the threads.
8. Print messages before and after the exchange to the console.

```java
import java.util.concurrent.Exchanger;

public class ExchangerExample {
    public static void main(String[] args) {
        // Create an Exchanger object to exchange String data
        Exchanger<String> exchanger = new Exchanger<>();

        // Define the first task
        Runnable task1 = () -> {
            try {
                String message = "Message from Task 1";
                System.out.println("Task 1: Sending - " + message);
                // Exchange message with Task 2
                String response = exchanger.exchange(message);
                System.out.println("Task 1: Received - " + response);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        };

        // Define the second task
        Runnable task2 = () -> {
            try {
                String message = "Message from Task 2";
                System.out.println("Task 2: Sending - " + message);
                // Exchange message with Task 1
                String response = exchanger.exchange(message);
                System.out.println("Task 2: Received - " + response);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        };

        // Create and start the threads
        Thread thread1 = new Thread(task1);
        Thread thread2 = new Thread(task2);

        thread1.start();
        thread2.start();
    }
}
```

**Console Output:**
```
Task 1: Sending - Message from Task 1
Task 2: Sending - Message from Task 2
Task 1: Received - Message from Task 2
Task 2: Received - Message from Task 1
```
