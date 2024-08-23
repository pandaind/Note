Module 2: Thread Synchronization
2.1 Understanding Synchronization
- The Need for Synchronization
- Race Conditions and Critical Sections

2.2 Synchronized Blocks and Methods
- Synchronized Methods
- Synchronized Blocks
- Intrinsic Locks and Monitor Objects

2.3 Inter-Thread Communication
- wait(), notify(), and notifyAll()
- Producer-Consumer Problem
- Deadlocks and How to Avoid Them


```java
public class Main {
  public static void main(String[] args) throws InterruptedException {
    // Example usage of Counter to demonstrate race conditions and critical sections
    Counter counter = new Counter();
    Thread t1 = new Thread(new CounterRunnable(counter));
    Thread t2 = new Thread(new CounterRunnable(counter));
    t1.start();
    t2.start();

    // Wait for threads to finish
    t1.join();
    t2.join();

    // Print the final count
    System.out.println("Final Count: " + counter.getCount());

    // Example usage of Producer-Consumer problem to demonstrate inter-thread communication
    ProducerConsumer pc = new ProducerConsumer();
    Thread producer = new Thread(new Producer(pc));
    Thread consumer = new Thread(new Consumer(pc));

    producer.start();
    consumer.start();

    // Wait for producer and consumer to finish
    producer.join();
    consumer.join();
  }
}

// Counter class to demonstrate synchronized methods
class Counter {
  private int count = 0;

  // Synchronized method to ensure atomicity and avoid race conditions
  public synchronized void increment() {
    count++;
  }

  // Synchronized method to safely retrieve the count value
  public synchronized int getCount() {
    return count;
  }
}

// Runnable to increment counter, demonstrating critical sections
class CounterRunnable implements Runnable {
  private Counter counter;

  public CounterRunnable(Counter counter) {
    this.counter = counter;
  }

  @Override
  public void run() {
    for (int i = 0; i < 1000; i++) {
      counter.increment();
    }

    System.out.println("Count: " + counter.getCount() + ", Thread: " + Thread.currentThread().getName());
  }
}

// Producer-Consumer problem to demonstrate inter-thread communication
class ProducerConsumer {
  private int item;
  private boolean available = false;

  // Synchronized method to produce an item, demonstrating wait() and notifyAll()
  public synchronized void produce(int value) throws InterruptedException {
    while (available) {
      wait();
    }
    item = value;
    available = true;
    notifyAll();
  }

  // Synchronized method to consume an item, demonstrating wait() and notifyAll()
  public synchronized int consume() throws InterruptedException {
    while (!available) {
      wait();
    }
    available = false;
    notifyAll();
    return item;
  }
}

// Producer class to produce items, demonstrating the producer side of the Producer-Consumer problem
class Producer implements Runnable {
  private ProducerConsumer pc;

  public Producer(ProducerConsumer pc) {
    this.pc = pc;
  }

  @Override
  public void run() {
    for (int i = 0; i <= 10; i++) {
      try {
        pc.produce(i);
        System.out.println("Produced: " + i);
      } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
      }
    }
  }
}

// Consumer class to consume items, demonstrating the consumer side of the Producer-Consumer problem
class Consumer implements Runnable {
  private ProducerConsumer pc;

  public Consumer(ProducerConsumer pc) {
    this.pc = pc;
  }

  @Override
  public void run() {
    for (int i = 0; i <= 10; i++) {
      try {
        int value = pc.consume();
        System.out.println("Consumed: " + value);
      } catch (InterruptedException e) {
        Thread.currentThread().interrupt();
      }
    }
  }
}
```

```bash
Count: 1413, Thread: Thread-0
Count: 2000, Thread: Thread-1
Final Count: 2000
Produced: 0
Produced: 1
Consumed: 0
Consumed: 1
Produced: 2
Produced: 3
Consumed: 2
Consumed: 3
Consumed: 4
Produced: 4
Produced: 5
Produced: 6
Consumed: 5
Consumed: 6
Consumed: 7
Produced: 7
Produced: 8
Produced: 9
Consumed: 8
Consumed: 9
Produced: 10
Consumed: 10
```
