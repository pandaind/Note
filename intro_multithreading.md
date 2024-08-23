Module 1: Introduction to Multithreading

1.1 Basics of Multithreading
- Overview of Threads
- Process vs. Thread
- Benefits and Challenges of Multithreading

1.2 Creating and Managing Threads
- Creating Threads by Extending Thread Class
- Creating Threads by Implementing Runnable Interface
- Thread Lifecycle and States
- Thread Priority and Daemon Threads

1.3 Thread Management
- Starting and Stopping Threads
- Joining Threads
- Thread.sleep() and Thread.yield()

```java
class MyThread extends Thread {
  public void run() {
    // This will print a message indicating that the thread created by extending Thread class is running.
    System.out.println("Thread by extending Thread class is running.");
  }
}

class MyRunnable implements Runnable {
  public void run() {
    // This will print a message indicating that the thread created by implementing Runnable interface is running.
    System.out.println("Thread by implementing Runnable interface is running.");
  }
}

public class Main {
  public static void main(String[] args) {
    // Creating and starting a thread by extending Thread class
    MyThread thread1 = new MyThread();
    thread1.start();

    // Creating and starting a thread by implementing Runnable interface
    Thread thread2 = new Thread(new MyRunnable());
    thread2.start();

    // Demonstrating thread lifecycle and states
    Thread thread3 = new Thread(new MyRunnable());
    // This will print the state of thread3 after creation, which should be NEW.
    System.out.println("Thread state after creation: " + thread3.getState());
    thread3.start();
    // This will print the state of thread3 after start, which should be RUNNABLE.
    System.out.println("Thread state after start: " + thread3.getState());

    // Setting thread priority
    thread1.setPriority(Thread.MAX_PRIORITY);
    // This will print the priority of thread1, which should be MAX_PRIORITY.
    System.out.println("Thread1 priority: " + thread1.getPriority());

    // Setting daemon thread
    thread2.setDaemon(true);
    // This will print whether thread2 is a daemon thread, which should be true.
    System.out.println("Thread2 is daemon: " + thread2.isDaemon());

    // Starting and stopping a thread using a flag
    StoppableRunnable stoppableRunnable = new StoppableRunnable();
    Thread thread4 = new Thread(stoppableRunnable);
    thread4.start();
    try {
      // This will let thread4 run for 1 second.
      Thread.sleep(1000);
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    // This will stop thread4 by setting the running flag to false.
    stoppableRunnable.stop();
    // This will print a message indicating that thread4 has stopped.
    System.out.println("Thread4 stopped.");

    // Joining threads
    try {
      // This will wait for thread1, thread2, thread3, and thread4 to die.
      thread1.join();
      thread2.join();
      thread3.join();
      thread4.join();
    } catch (InterruptedException e) {
      e.printStackTrace();
    }

    // Demonstrating Thread.sleep() and Thread.yield()
    try {
      // This will print a message and then make the main thread sleep for 1 second.
      System.out.println("Main thread sleeping for 1 second.");
      Thread.sleep(1000);
    } catch (InterruptedException e) {
      e.printStackTrace();
    }
    // This will print a message and then make the main thread yield.
    System.out.println("Main thread yielding.");
    Thread.yield();
  }
}

class StoppableRunnable implements Runnable {
  private volatile boolean running = true;

  public void run() {
    // This will keep printing a message indicating that the stoppable thread is running until the running flag is set to false.
    while (running) {
      System.out.println("Stoppable thread is running.");
      try {
        // This will make the thread sleep for 200 milliseconds to simulate work.
        Thread.sleep(200);
      } catch (InterruptedException e) {
        e.printStackTrace();
      }
    }
  }

  public void stop() {
    // This will set the running flag to false, stopping the thread.
    running = false;
  }
}
```
```bash
Thread by extending Thread class is running.
Thread by implementing Runnable interface is running.
Thread state after creation: NEW
Thread state after start: RUNNABLE
Thread by implementing Runnable interface is running.
Thread1 priority: 5
Thread2 is daemon: true
Stoppable thread is running.
Stoppable thread is running.
Stoppable thread is running.
Stoppable thread is running.
Stoppable thread is running.
Thread4 stopped.
Main thread sleeping for 1 second.
Main thread yielding.
```
