- ```java
  package main;
  
  class Base {
  	public void Print()
  	{
  		System.out.println("Base");
  	}
  }
  
  class Derived extends Base {
  	public void Print()
  	{
  		System.out.println("Derived");
  	}
  }
  
  class Main {
  	public static void DoPrint(Base o)
  	{
  		o.Print();
  	}
  	public static void main(String[] args)
  	{
  		Base x = new Base();
  		Base y = new Derived();
  		Derived z = new Derived();
  		DoPrint(x);
  		DoPrint(y);
  		DoPrint(z);
  	}
  }
  ```

- ```java
  package main;
  
  // filename Main.java
  class Point {
  	protected int x, y;
  
  	public Point(int _x, int _y)
  	{
  		x = _x;
  		y = _y;
  	}
  }
  
  public class Main {
  	public static void main(String args[])
  	{
  		Point p = new Point();
  		System.out.println("x = " + p.x + ", y = " + p.y);
  	}
  }
  ```

- ```java
  // filename: Test.java
  
  class Test {
  
  	// Declaring and initializing integer variable
  	int x = 10;
  
  	// Main driver method
  	public static void main(String[] args)
  	{
  
  		// Creating an object of class inside main()
  		Test t = new Test();
  
  		// Printing the value insiode the object by
  		// above created object
  		System.out.println(t.x);
  	}
  }
  ```

- ```java
  // filename: Test.java
  
  // Main class
  class Test {
  
  	// Declaring and initializing variables
  	int y = 2;
  	int x = y + 2;
  
  	// main driver method
  	public static void main(String[] args)
  	{
  
  		// Creating an object of class inside main() method
  		Test m = new Test();
  
  		// Printing the value of x and y
  		// using above object created
  		System.out.println("x = " + m.x + ", y = " + m.y);
  	}
  }
  ```

- ```java
  // filename: Test.java
  
  // Main clas
  public class Test {
  	// Declaring and initializing integer with custom value
  	int x = 2;
  
  	// Constructor of this class
  	// Parametrized constructor
  	Test(int i) { x = i; }
  
  	// Main driver method
  	public static void main(String[] args)
  	{
  
  		// Creating object of class in main()
  		Test t = new Test(5);
  
  		// Printing the value
  		System.out.println("x = " + t.x);
  	}
  }
  ```

- ```java
  // filename: Test2.java
  
  // Class 1
  // Helper class
  class Test1 {
  
  	// Constructor of this class
  	Test1(int x)
  	{
  
  		// Print statement whenever this constructor is
  		// called
  		System.out.println("Constructor called " + x);
  	}
  }
  
  // Class 2
  // Class contains an instance of Test1
  // Main class
  class Test2 {
  
  	// Creating instance(object) of class1 in this class
  	Test1 t1 = new Test1(10);
  
  	// Constructor of this class
  	Test2(int i) { t1 = new Test1(i); }
  
  	// Main driver method
  	public static void main(String[] args)
  	{
  		// Creating instance of this class inside main()
  		Test2 t2 = new Test2(5);
  	}
  }
  ```

- ```java
  // file name: Main.java
  
  class Base {
  	protected void foo() {}
  }
  class Derived extends Base {
  	void foo() {} // error
  }
  public class Main {
  	public static void main(String args[]) {
  		Derived d = new Derived();
  		d.foo();
  	}
  }
  
  ```

- ```java
  // file name: Main.java
  
  class Complex {
  	private double re, im;	
  	public String toString() {
  		return "(" + re + " + " + im + "i)";
  	}
  	Complex(Complex c) {
  		re = c.re;
  		im = c.im;
  	}
  }
  
  public class Main {
  	public static void main(String[] args) {
  		Complex c1 = new Complex(); // error
  		Complex c2 = new Complex(c1);
  		System.out.println(c2);
  	}
  }
  
  ```

- ```java
  // Main.java
  public class Main
  {
  	public static void gfg(String s)
  	{	
  		System.out.println("String");
  	}
  	public static void gfg(Object o)
  	{
  		System.out.println("Object");
  	}
  
  	public static void main(String args[])
  	{
  		gfg(null);
  	}
  } //end class
  
  ```

- ```java
  // Main.java
  public class Main
  {
  	public static void gfg(String s)
  	{	
  		System.out.println("String");
  	}
  	public static void gfg(Object o)
  	{
  		System.out.println("Object");
  	}
  	public static void gfg(Integer i)
  	{
  		System.out.println("Integer");
  	}
  
  	public static void main(String args[])
  	{
  		gfg(null);
  	}
  } //end class
  ```

- ```java
  // Main.java
  public class Main
  {
  	public static void main(String args[])
  	{
  		String s1 = "abc";
  		String s2 = s1;
  		s1 += "d";
  		System.out.println(s1 + " " + s2 + " " + (s1 == s2));
  
  		StringBuffer sb1 = new StringBuffer("abc");
  		StringBuffer sb2 = sb1;
  		sb1.append("d");
  		System.out.println(sb1 + " " + sb2 + " " + (sb1 == sb2));
  	}
  } //end class
  ```

- ```java
  // Main.java
  public class Main
  {
  	public static void main(String args[])
  	{
  		short s = 0;
  		int x = 07;
  		int y = 08;
  		int z = 112345;
  
  		s += z;
  		System.out.println("" + x + y + s);
  	}
  } //end class
  
  ```

- ```java
  class First
  {
  	public First() { System.out.println("a"); }
  }
  
  class Second extends First
  {
  	public Second() { System.out.println("b"); }
  }
  
  class Third extends Second
  {
  	public Third() { System.out.println("c"); }
  }
  
  public class MainClass
  {
  	public static void main(String[] args)
  	{
  		Third c = new Third();
  	}
  }
  
  ```

- ```java
  class First
  {
  	int i = 10;
  
  	public First(int j)
  	{
  		System.out.println(i);
  		this.i = j * 10;
  	}
  }
  
  class Second extends First
  {
  	public Second(int j)
  	{
  		super(j);
  		System.out.println(i);
  		this.i = j * 20;
  	}
  }
  
  public class MainClass
  {
  	public static void main(String[] args)
  	{
  		Second n = new Second(20);
  		System.out.println(n.i);
  	}
  }
  
  ```

- ```java
  import java.util.*;
  class I
  {
  	public static void main (String[] args)
  	{
  		Object i = new ArrayList().iterator();
  		System.out.print((i instanceof List) + ", ");
  		System.out.print((i instanceof Iterator) + ", ");
  		System.out.print(i instanceof ListIterator);
  	}
  }
  
  ```

- ```java
  class ThreadEx extends Thread
  {
  	public void run()
  	{
  		System.out.print("Hello...");
  	}
  	public static void main(String args[])
  	{
  		ThreadEx T1 = new ThreadEx();
  		T1.start();
  		T1.stop();
  		T1.start(); // cant start twice
  	}
  }
  
  ```

- ```java
  public class Calculator
  {
  	int num = 100;
  	public void calc(int num) { this.num = num * 10; }
  	public void printNum()	 { System.out.println(num); }
  
  	public static void main(String[] args)
  	{
  		Calculator obj = new Calculator();
  		obj.calc(2);
  		obj.printNum();
  	}
  }
  
  ```

- ```java
  public class MyStuff
  {
  	String name;
  
  	MyStuff(String n) { name = n; }
  
  	public static void main(String[] args)
  	{
  		MyStuff m1 = new MyStuff("guitar");
  		MyStuff m2 = new MyStuff("tv");
  		System.out.println(m2.equals(m1));
  	}
  
  	@Override
  	public boolean equals(Object obj)
  	{
  		MyStuff m = (MyStuff) obj;
  		if (m.name != null) { return true; }
  		return false;
  	}
  }
  
  ```

- ```java
  class Alpha
  {
  	public String type = "a ";
  	public Alpha() { System.out.print("alpha "); }
  }
  
  public class Beta extends Alpha
  {
  	public Beta() { System.out.print("beta "); }
  
  	void go()
  	{
  		type = "b ";
  		System.out.print(this.type + super.type);
  	}
  
  	public static void main(String[] args)
  	{
  		new Beta().go();
  	}
  }
  ```

- ```java
  public class Test
  {
  	public static void main(String[] args)
  	{
  		StringBuilder s1 = new StringBuilder("Java");
  		String s2 = "Love";
  		s1.append(s2);
  		s1.substring(4);
  		int foundAt = s1.indexOf(s2);
  		System.out.println(foundAt);
  	}
  }
  ```

- ```java
  class Writer
  {
  	public static void write()
  	{
  		System.out.println("Writing...");
  	}
  }
  class Author extends Writer
  {
  	public static void write()
  	{
  		System.out.println("Writing book");
  	}
  }
  
  public class Programmer extends Author
  {
  	public static void write()
  	{
  		System.out.println("Writing code");
  	}
  
  	public static void main(String[] args)
  	{
  		Author a = new Programmer();
  		a.write();
  	}
  }
  
  ```

- ```java
  class GfG
  {
  	public static void main(String args[])
  	{
  		String s1 = new String("geeksforgeeks");
  		String s2 = new String("geeksforgeeks");
  		if (s1 == s2)
  			System.out.println("Equal");
  		else
  			System.out.println("Not equal");
  	}
  }
  
  ```

- ```java
  class Person
  {
  	private void who()
  	{
  		System.out.println("Inside private method Person(who)");
  	}
  
  	public static void whoAmI()
  	{
  		System.out.println("Inside static method, Person(whoAmI)");
  	}
  
  	public void whoAreYou()
  	{
  		who();
  		System.out.println("Inside virtual method, Person(whoAreYou)");
  	}
  }
  
  class Kid extends Person
  {
  	private void who()
  	{
  		System.out.println("Kid(who)");
  	}
  
  	public static void whoAmI()
  	{
  		System.out.println("Kid(whoAmI)");
  	}
  
  	public void whoAreYou()
  	{
  		who();
  		System.out.println("Kid(whoAreYou)");
  	}
  }
  public class Gfg
  {
  	public static void main(String args[])
  	{
  		Person p = new Kid();
  		p.whoAmI();
  		p.whoAreYou();
  	}
  }
  
  ```

- ```java
  class GfG
  {
  	public static void main(String args[])
  	{
  		try
  		{
  			System.out.println("First statement of try block");
  			int num=45/3;
  			System.out.println(num);
  		}
  		catch(Exception e)
  		{
  			System.out.println("Gfg caught Exception");
  		}
  		finally
  		{
  			System.out.println("finally block");
  		}
  		System.out.println("Main method");
  	}
  }
  
  ```

- ```java
  class One implements Runnable
  {
  	public void run()
  	{
  		System.out.print(Thread.currentThread().getName());
  	}
  }
  class Two implements Runnable
  {
  	public void run()
  	{
  		new One().run();
  		new Thread(new One(),"gfg2").run();
  		new Thread(new One(),"gfg3").start();
  	}
  }
  class Three
  {
  	public static void main (String[] args)
  	{
  		new Thread(new Two(),"gfg1").start();
  	}
  }
  
  ```

- ```java
  class Gfg
  {
  	// constructor
  	Gfg()
  	{
  		System.out.println("Geeksforgeeks");
  	}
  	
  	static Gfg a = new Gfg(); //line 8
  
  	public static void main(String args[])
  	{
  		Gfg b; //line 12
  		b = new Gfg();
  	}
  }
  
  ```

- ```java
  class Gfg
  {
  	static int num;
  	static String mystr;
  
  	// constructor
  	Gfg()
  	{
  		num = 100;
  		mystr = "Constructor";
  	}
  
  	// First Static block
  	static
  	{
  		System.out.println("Static Block 1");
  		num = 68;
  		mystr = "Block1";
  	}
  
  	// Second static block
  	static
  	{
  		System.out.println("Static Block 2");
  		num = 98;
  		mystr = "Block2";
  	}
  
  	public static void main(String args[])
  	{
  		Gfg a = new Gfg();
  		System.out.println("Value of num = " + a.num);
  		System.out.println("Value of mystr = " + a.mystr);
  	}
  }
  
  ```

- ```java
  class superClass
  {
  	final public int calc(int a, int b)
  	{
  		return 0;
  	}
  }
  class subClass extends superClass
  {
  	public int calc(int a, int b)
  	{
  		return 1;
  	}
  }
  public class Gfg
  {
  	public static void main(String args[])
  	{
  		subClass get = new subClass();
  		System.out.println("x = " + get.calc(0, 1));
  	}
  }
  
  ```

- ```java
  public class Gfg
  {
  	public static void main(String[] args)
  	{
  		Integer a = 128, b = 128;
  		System.out.println(a == b);
  
  		Integer c = 100, d = 100; // IntegerCache
  		System.out.println(c == d);
  	}
  }
  
  ```

- ```java
  public class Test
  {
  	public static void main(String[] args) throws InterruptedException
  	{
  		String str = new String("GeeksForGeeks");
  			
  		// making str eligible for gc
  		str = null;
  			
  		// calling garbage collector
  		System.gc();
  			
  		// waiting for gc to complete
  		Thread.sleep(1000);
  	
  		System.out.println("end of main");
  	}
  
  	@Override
  	protected void finalize()
  	{
  		System.out.println("finalize method called");
  	}
  }
  
  ```

- ```java
  public class Test
  {
  	public static void main(String[] args) throws InterruptedException
  	{
  		Test t = new Test();
  			
  		// making t eligible for garbage collection
  		t = null;
  			
  		// calling garbage collector
  		System.gc();
  			
  		// waiting for gc to complete
  		Thread.sleep(1000);
  	
  		System.out.println("end main");
  	}
  
  	@Override
  	protected void finalize()
  	{
  		System.out.println("finalize method called");
  		System.out.println(10/0);
  	}
  	
  }
  
  ```

- ```java
  public class Test
  {
  	static Test t ;
  	
  	static int count =0;
  	
  	public static void main(String[] args) throws InterruptedException
  	{
  		Test t1 = new Test();
  			
  		// making t1 eligible for garbage collection
  		t1 = null; // line 12
  			
  		// calling garbage collector
  		System.gc(); // line 15
  			
  		// waiting for gc to complete
  		Thread.sleep(1000);
  	
  		// making t eligible for garbage collection,
  		t = null; // line 21
  			
  		// calling garbage collector
  		System.gc(); // line 24
          // it will call finalize() method on a particular object exactly one time
  	
  		// waiting for gc to complete
  		Thread.sleep(1000);
  			
  		System.out.println("finalize method called "+count+" times");
  		
  	}
  	
  	@Override
  	protected void finalize()
  	{
  		count++;
  		
  		t = this; // line 38
  			
  	}
  	
  }
  
  ```

- ```java
  public class Test
  {
  	public static void main(String[] args)
  	{
  		// How many objects are eligible for
  		// garbage collection after this line?
  		m1(); // Line 5
  	}
  
  	static void m1()
  	{
  		Test t1 = new Test();
  		Test t2 = new Test();
  	}
  }
  // How many objects are eligible for garbage collection after execution of line 5 ?
  ```

- ```java
  public class Test
  {
  	public static void main(String [] args)
  	{
  		Test t1 = new Test();
  		Test t2 = m1(t1); // line 6
  		Test t3 = new Test();
  		t2 = t3; // line 8
  		
  	}
  	
  	static Test m1(Test temp)
  	{
  		temp = new Test();
  		return temp;
  	}
  }
  // How many objects are eligible for garbage collection after execution of line 8?
  ```

- ```java
  public class Base
  {
  	private int data;
  
  	public Base()
  	{
  		data = 5;
  	}
  
  	public int getData()
  	{
  		return this.data;
  	}
  }
  
  class Derived extends Base
  {
  	private int data;
  	public Derived()
  	{
  		data = 6;
  	}
  	private int getData() // compile error
  	{
  		return data;
  	}
  
  	public static void main(String[] args)
  	{
  		Derived myData = new Derived();
  		System.out.println(myData.getData());
  	}
  }
  
  ```

- ```java
  public class Test
  {
  	private int data = 5;
  
  	public int getData()
  	{
  		return this.data;
  	}
  	public int getData(int value)
  	{
  		return (data+1);
  	}
  	public int getData(int... value)
  	{
  		return (data+2);
  	}
  
  	public static void main(String[] args)
  	{
  		Test temp = new Test();
  		System.out.println(temp.getData(7, 8, 12));
  	}
  }
  
  ```

- ```java
  public class Base
  {
  	private int multiplier(int data) // private compile error
  	{
  		return data*5;
  	}
  }
  
  class Derived extends Base
  {
  	private static int data;
  	public Derived()
  	{
  		data = 25;
  	}
  	public static void main(String[] args)
  	{
  		Base temp = new Derived();
  		System.out.println(temp.multiplier(data));
  	}
  }
  
  ```

- ```java
  import java.io.IOException;
  import java.util.EmptyStackException;
  
  public class newclass
  {
  	public static void main(String[] args)
  	{
  		try
  		{
  			System.out.printf("%d", 1);
  			throw(new Exception());
  		}
  		catch(IOException e)
  		{
  			System.out.printf("%d", 2);
  		}
  		catch(EmptyStackException e)
  		{
  			System.out.printf("%d", 3);
  		}
  		catch(Exception e)
  		{
  			System.out.printf("%d", 4);
  		}
  		finally
  		{
  			System.out.printf("%d", 5);
  		}
  	}
  }
  
  ```

- ```java
  public class javaclass
  {
  	static
  	{
  		System.out.printf("%d", 1);
  	}
  	static
  	{
  		System.out.printf("%d", 2);
  	}
  	static
  	{
  		System.out.printf("%d", 3);
  	}
  	private static int myMethod()
  	{
  		return 4;
  	}
  	private int function()
  	{
  		return 5;
  	}
  
  	public static void main(String[] args)
  	{
  		System.out.printf("%d", (new javaclass()).function() + myMethod());
  	}
  }
  
  ```

- ```java
  public class Test implements Runnable
  {
  	public void run()
  	{
  		System.out.printf("%d",3);
  	}
  	public static void main(String[] args) throws InterruptedException
  	{
  		Thread thread = new Thread(new Test());
  		thread.start();
  		System.out.printf("%d",1);
  		thread.join();
  		System.out.printf("%d",2);
  	}
  }
  ```

- ```java
  public class Test
  {
  	private static int value = 20;
  	public int s = 15;
  	public static int temp = 10;
  	public static class Nested
  	{
          private void display()
          {
              System.out.println(temp + s + value);
          }
  	}
  	
  	public static void main(String args[])
  	{
          Test.Nested inner = new Test.Nested();
          inner.display();
  	}
  }
  ```

- ```java
  import java.io.*;
  public class Test
  {
  	public void display() throws IOException
  	{
  		System.out.println("Test");
  	}
  
  }
  
  class Derived extends Test
  {
  	public void display() throws IOException
  	{
  		System.out.println("Derived");
  	}
  	public static void main(String[] args) throws IOException
  	{
  		Derived object = new Derived();
  		object.display();
  	}
  }
  
  ```

- ```java
  public class Test extends Thread
  {
  	public void run()
  	{
  		System.out.printf("Test ");
  	}
  	public static void main(String[] args)
  	{
  		Test test = new Test();
  		test.run();
  		test.start();
  	}
  }
  ```

- ```java
  public class Test extends Thread
  {
  	public static void main(String[] args)
  	{
  		String a = "GeeksforGeeks";
  		String b = new String(a);
  		int value = 0;
  		value = (a==b) ? 1:2;
  		if(value == 1)
  		{
  			System.out.println("GeeksforGeeks");
  		}
  		else if(value == 2)
  		{
  			System.out.println("Geeks for Geeks");
  		}
  		else
  		{
  			System.out.println("GFG");
  		}
  		
  	}
  }
  ```

- ```java
  public class Test
  {
  	try
  	{
  		public Test() // constructor
  		{
  			System.out.println("GeeksforGeeks");
  			throw new Exception();
  		}
  	}
  	catch(Exception e)
  	{
  		System.out.println("GFG");
  	}
  	public static void main(String[] args)
  	{
  		Test test = new Test();
  	}
  }
  
  ```

- ```java
  public interface Test
  {
  	public int calculate();
  	protected interface NestedInterface // protected compile error
  	{
  		public void nested();
  	}
  }
  ```

- ```java
  import java.util.*;
  
  public class priorityQueue {
  	public static void main(String[] args)
  	{
  		PriorityQueue<Integer> queue
  			= new PriorityQueue<>();
  		queue.add(11);
  		queue.add(10);
  		queue.add(22);
  		queue.add(5);
  		queue.add(12);
  		queue.add(2);
  
  		while (queue.isEmpty() == false)
  			System.out.printf("%d ", queue.remove());
  
  		System.out.println("\n");
  	}
  }
  // 2 5 10 11 12 22
  ```

- ```java
  import java.util.*;
  
  public class Treeset {
  	public static void main(String[] args)
  	{
  		TreeSet<String> treeSet = new TreeSet<>();
  
  		treeSet.add("Geeks");
  		treeSet.add("For");
  		treeSet.add("Geeks");
  		treeSet.add("GeeksforGeeks");
  
  		for (String temp : treeSet)
  			System.out.printf(temp + " ");
  
  		System.out.println("\n");
  	}
  }
  
  ```

- ```java
  import java.util.*;
  
  public class linkedList {
  	public static void main(String[] args)
  	{
  		List<String> list1 = new LinkedList<>();
  		list1.add("Geeks");
  		list1.add("For");
  		list1.add("Geeks");
  		list1.add("GFG");
  		list1.add("GeeksforGeeks");
  
  		List<String> list2 = new LinkedList<>();
  		list2.add("Geeks");
  
  		list1.removeAll(list2);
  
  		for (String temp : list1)
  			System.out.printf(temp + " ");
  
  		System.out.println();
  	}
  }
  
  ```

- ```java
  import java.util.*;
  
  public class hashSet {
  	public static void main(String[] args)
  	{
  		HashSet<String> hashSet = new HashSet<>();
  		hashSet.add("Geeks");
  		hashSet.add("For");
  		hashSet.add("Geeks");
  		hashSet.add("GeeksforGeeks");
  
  		System.out.println(hashSet);
  	}
  }
  
  ```

- ```java
  import java.util.*;
  
  public class stack {
  	public static void main(String[] args)
  	{
  		List<String> list = new LinkedList<>();
  		list.add("Geeks");
  		list.add("For");
  		list.add("Geeks");
  		list.add("GeeksforGeeks");
  		Iterator<Integer> iter = list.iterator();
  
  		while (iter.hasNext())
  			System.out.printf(iter.next() + " ");
  
  		System.out.println();
  	}
  }
  
  ```

- ```java
  class Helper
  {
  	private int data;
  	private Helper() / private error
  	{
  		data = 5;
  	}
  }
  public class Test
  {
  	public static void main(String[] args)
  	{
  		Helper help = new Helper();
  		System.out.println(help.data);
  	}
  }
  
  ```

- ```java
  public class Test implements Runnable
  {
  	public void run()
  	{
  		System.out.printf(" Thread's running ");
  	}
  
  	try
  	{
  		public Test()
  		{
  			Thread.sleep(5000);
  		}
  	}
  	catch (InterruptedException e)
  	{
  		e.printStackTrace();
  	}
  	
  	public static void main(String[] args)
  	{
  		Test obj = new Test();
  		Thread thread = new Thread(obj);
  		thread.start();
  		System.out.printf(" GFG ");
  	}
  }
  
  ```

- ```java
  class Temp
  {
  	private Temp(int data)
  	{
  		System.out.printf(" Constructor called ");
  	}
  	protected static Temp create(int data)
  	{
  		Temp obj = new Temp(data);
  		return obj;
  	}
  	public void myMethod()
  	{
  		System.out.printf(" Method called ");
  	}
  }
  
  public class Test
  {
  	public static void main(String[] args)
  	{
  		Temp obj = Temp.create(20);
  		obj.myMethod();
  	}
  }
  
  ```

- ```java
  public class Test
  {
  	public Test()
  	{
  		System.out.printf("1");
  		new Test(10);
  		System.out.printf("5");
  	}
  	public Test(int temp)
  	{
  		System.out.printf("2");
  		new Test(10, 20);
  		System.out.printf("4");
  	}
  	public Test(int data, int temp)
  	{
  		System.out.printf("3");
  		
  	}
  	
  	public static void main(String[] args)
  	{
  		Test obj = new Test();
  		
  	}
  	
  }
  
  ```

- ```java
  class Base
  {
  	public static String s = " Super Class ";
  	public Base()
  	{
  		System.out.printf("1");
  	}
  }
  public class Derived extends Base
  {
  	public Derived()
  	{
  		System.out.printf("2");
  		super();
  	}
  	
  	public static void main(String[] args)
  	{
  		Derived obj = new Derived();
  		System.out.printf(s);
  	}
  }
  
  ```

- ```java
  public class Outer
  {
  	public static int temp1 = 1;
  	private static int temp2 = 2;
  	public int temp3 = 3; // not static
  	private int temp4 = 4;
  	
  	public static class Inner
  	{
  		private static int temp5 = 5;
  		
  		private static int getSum()
  		{
  			return (temp1 + temp2 + temp3 + temp4 + temp5);
  		}
  	}
  	
  	public static void main(String[] args)
  	{
  		Outer.Inner obj = new Outer.Inner();
  		System.out.println(obj.getSum());
  	}
  	
  }
  
  ```

- ```java
  public class Outer
  {
  	private static int data = 10;
  	private static int LocalClass()
  	{
  		class Inner
  		{
  			public int data = 20;
  			private int getData()
  			{
  				return data;
  			}
  		};
  		Inner inner = new Inner();
  		return inner.getData();
  	}
  	
  	public static void main(String[] args)
  	{
  		System.out.println(data * LocalClass());
  	}
  }
  
  ```

- ```java
  interface Anonymous
  {
  	public int getValue();
  }
  public class Outer
  {
  	private int data = 15;
  	public static void main(String[] args)
  	{
  		Anonymous inner = new Anonymous()
  				{
  					int data = 5;
  					public int getValue()
  					{
  						return data;
  					}
  					public int getData() // compile error
  					{
  						return data;
  					}
  				};
  		Outer outer = new Outer();
  		System.out.println(inner.getValue() + inner.getData() + outer.data);
  	}
  }
  
  ```

- ```java
  public class Outer
  {
  	private int data = 10;
  	
  	class Inner
  	{
  		private int data = 20;
  		private int getData()
  		{
  			return data;
  		}
  		public void main(String[] args)
  		{
  			Inner inner = new Inner();
  			System.out.println(inner.getData());
  			
  		}
  	}
  	private int getData()
  	{
  		return data;
  	}
  	public static void main(String[] args)
  	{
  		Outer outer = new Outer();
  		Outer.Inner inner = outer.new Inner();
  		System.out.printf("%d", outer.getData());
  		inner.main(args);
  	}
  }
  
  ```

- ```java
  interface OuterInterface
  {
  	public void InnerMethod();
  	public interface InnerInterface
  	{
  		public void InnerMethod();
  	}
  }
  public class Outer implements OuterInterface.InnerInterface, OuterInterface
  {
  	public void InnerMethod()
  	{
  		System.out.println(100);
  	}
  	
  	
  	public static void main(String[] args)
  	{
  		Outer obj = new Outer();
  		obj.InnerMethod();
  	}
  }
  
  ```

- ```java
  public class Test implements Runnable
  {
  	public void run()
  	{
  		System.out.printf("GFG ");
  		System.out.printf("Geeks ");
  	}
  	public static void main(String[] args)
  	{
  		Test obj = new Test();
  		Thread thread = new Thread(obj);
  		
  		thread.start();
  		System.out.printf("Geeks ");
  		try
  		{
  			thread.join();
  		}
  		catch (InterruptedException e)
  		{
  			e.printStackTrace();
  		}
  		System.out.println("for ");
  	}
  }
  
  ```

- ```java
  public class Test implements Runnable
  {
  	public void run()
  	{
  		System.out.printf("GFG ");
  	}
  	public static void main(String[] args) throws InterruptedException
  	{
  		Thread thread1 = new Thread(new Test());
  		thread1.start();
  		thread1.start();
  		System.out.println(thread1.getState());
  	}
  }
  
  ```

- ```java
  public class Test extends Thread implements Runnable
  {
  	public void run()
  	{
  		System.out.printf("GFG ");
  	}
  	public static void main(String[] args) throws InterruptedException
  	{
  		Test obj = new Test();
  		obj.run();
  		obj.start();
  	}
  }
  
  ```

- ```java
  class myThread implements Runnable
  {
  	public void run()
  	{
  		Test.obj.notify();
  	}
  }
  
  public class Test implements Runnable
  {
  	public static Test obj;
  	private int data;
  	public Test()
  	{
  		data = 10;
  	}
  	public void run()
  	{
  		obj = new Test();
  		obj.wait(); // compile error
  		obj.data += 20;
  		
  		System.out.println(obj.data);
  	}
  	public static void main(String[] args) throws InterruptedException
  	{
  		Thread thread1 = new Thread(new Test());
  		Thread thread2 = new Thread(new myThread());
  		
  		thread1.start();
  		thread2.start();
  	
  		System.out.printf(" GFG - ");
  	}
  }
  
  ```

- ```java
  import java.util.concurrent.*;
  
  public class Test implements Runnable
  {
  	public static CyclicBarrier barrier = new CyclicBarrier(3);
  	public void run()
  	{
  		System.out.printf(" GFG ");
  		try
  		{
  			barrier.await();
  		} catch (InterruptedException | BrokenBarrierException e)
  		{
  			e.printStackTrace();
  		}
  	}
  	public static void main(String[] args) throws InterruptedException
  	{
  		Thread thread1 = new Thread(new Test());
  		Thread thread2 = new Thread(new Test());
  		
  		thread1.start();
  		thread2.start();
  		System.out.printf(" GeeksforGeeks ");
  		try
  		{
  			barrier.await();
  		} catch (InterruptedException | BrokenBarrierException e)
  		{
  			e.printStackTrace();
  		}
  		System.out.printf(" End ");
  		
  	}
  }
  
  ```

- ```java
  // Java code for thread creation by extending
  // the Thread class
  class MultithreadingDemo extends Thread {
  	public void run()
  	{
  		try {
  			// Displaying the thread that is running
  			System.out.println(
  				"Thread " + Thread.currentThread().getId()
  				+ " is running");
  		}
  		catch (Exception e) {
  			// Throwing an exception
  			System.out.println("Exception is caught");
  		}
  	}
  }
  
  // Main Class
  public class Multithread {
  	public static void main(String[] args)
  	{
  		int n = 8; // Number of threads
  		for (int i = 0; i < n; i++) {
  			MultithreadingDemo object
  				= new MultithreadingDemo();
  			object.start();
  		}
  	}
  }
  
  ```

- ```java
  import java.util.ArrayList;
  import java.util.Arrays;
  import java.util.IntSummaryStatistics;
  import java.util.List;
  import java.util.Random;
  import java.util.stream.Collectors;
  import java.util.Map;
  
  public class Java8Tester {
  
     public static void main(String args[]) {
        System.out.println("Using Java 7: ");
  		
        // Count empty strings
        List<String> strings = Arrays.asList("abc", "", "bc", "efg", "abcd","", "jkl");
        System.out.println("List: " +strings);
        long count = getCountEmptyStringUsingJava7(strings);
  		
        System.out.println("Empty Strings: " + count);
        count = getCountLength3UsingJava7(strings);
  		
        System.out.println("Strings of length 3: " + count);
  		
        //Eliminate empty string
        List<String> filtered = deleteEmptyStringsUsingJava7(strings);
        System.out.println("Filtered List: " + filtered);
  		
        //Eliminate empty string and join using comma.
        String mergedString = getMergedStringUsingJava7(strings,", ");
        System.out.println("Merged String: " + mergedString);
        List<Integer> numbers = Arrays.asList(3, 2, 2, 3, 7, 3, 5);
  		
        //get list of square of distinct numbers
        List<Integer> squaresList = getSquares(numbers);
        System.out.println("Squares List: " + squaresList);
        List<Integer> integers = Arrays.asList(1,2,13,4,15,6,17,8,19);
  		
        System.out.println("List: " +integers);
        System.out.println("Highest number in List : " + getMax(integers));
        System.out.println("Lowest number in List : " + getMin(integers));
        System.out.println("Sum of all numbers : " + getSum(integers));
        System.out.println("Average of all numbers : " + getAverage(integers));
        System.out.println("Random Numbers: ");
  		
        //print ten random numbers
        Random random = new Random();
  		
        for(int i = 0; i < 10; i++) {
           System.out.println(random.nextInt());
        }
  		
        System.out.println("Using Java 8: ");
        System.out.println("List: " +strings);
  		
        count = strings.stream().filter(string->string.isEmpty()).count();
        System.out.println("Empty Strings: " + count);
  		
        count = strings.stream().filter(string -> string.length() == 3).count();
        System.out.println("Strings of length 3: " + count);
  		
        filtered = strings.stream().filter(string ->!string.isEmpty()).collect(Collectors.toList());
        System.out.println("Filtered List: " + filtered);
  		
        mergedString = strings.stream().filter(string ->!string.isEmpty()).collect(Collectors.joining(", "));
        System.out.println("Merged String: " + mergedString);
  		
        squaresList = numbers.stream().map( i ->i*i).distinct().collect(Collectors.toList());
        System.out.println("Squares List: " + squaresList);
        System.out.println("List: " +integers);
  		
        IntSummaryStatistics stats = integers.stream().mapToInt((x) ->x).summaryStatistics();
  		
        System.out.println("Highest number in List : " + stats.getMax());
        System.out.println("Lowest number in List : " + stats.getMin());
        System.out.println("Sum of all numbers : " + stats.getSum());
        System.out.println("Average of all numbers : " + stats.getAverage());
        System.out.println("Random Numbers: ");
  		
        random.ints().limit(10).sorted().forEach(System.out::println);
  		
        //parallel processing
        count = strings.parallelStream().filter(string -> string.isEmpty()).count();
        System.out.println("Empty Strings: " + count);
     }
  	
     private static int getCountEmptyStringUsingJava7(List<String> strings) {
        int count = 0;
  
        for(String string: strings) {
  		
           if(string.isEmpty()) {
              count++;
           }
        }
        return count;
     }
  	
     private static int getCountLength3UsingJava7(List<String> strings) {
        int count = 0;
  		
        for(String string: strings) {
  		
           if(string.length() == 3) {
              count++;
           }
        }
        return count;
     }
  	
     private static List<String> deleteEmptyStringsUsingJava7(List<String> strings) {
        List<String> filteredList = new ArrayList<String>();
  		
        for(String string: strings) {
  		
           if(!string.isEmpty()) {
               filteredList.add(string);
           }
        }
        return filteredList;
     }
  	
     private static String getMergedStringUsingJava7(List<String> strings, String separator) {
        StringBuilder stringBuilder = new StringBuilder();
  		
        for(String string: strings) {
  		
           if(!string.isEmpty()) {
              stringBuilder.append(string);
              stringBuilder.append(separator);
           }
        }
        String mergedString = stringBuilder.toString();
        return mergedString.substring(0, mergedString.length()-2);
     }
  	
     private static List<Integer> getSquares(List<Integer> numbers) {
        List<Integer> squaresList = new ArrayList<Integer>();
  		
        for(Integer number: numbers) {
           Integer square = new Integer(number.intValue() * number.intValue());
  			
           if(!squaresList.contains(square)) {
              squaresList.add(square);
           }
        }
        return squaresList;
     }
  	
     private static int getMax(List<Integer> numbers) {
        int max = numbers.get(0);
  		
        for(int i = 1;i < numbers.size();i++) {
  		
           Integer number = numbers.get(i);
  			
           if(number.intValue() > max) {
              max = number.intValue();
           }
        }
        return max;
     }
  	
     private static int getMin(List<Integer> numbers) {
        int min = numbers.get(0);
  		
        for(int i= 1;i < numbers.size();i++) {
           Integer number = numbers.get(i);
  		
           if(number.intValue() < min) {
              min = number.intValue();
           }
        }
        return min;
     }
  	
     private static int getSum(List numbers) {
        int sum = (int)(numbers.get(0));
  		
        for(int i = 1;i < numbers.size();i++) {
           sum += (int)numbers.get(i);
        }
        return sum;
     }
  	
     private static int getAverage(List<Integer> numbers) {
        return getSum(numbers) / numbers.size();
     }
  }
  ```

  

