### Serialization in Java

Serialization is a fundamental concept in Java that allows objects to be converted into a byte stream, making it possible to save the state of an object to a file or transmit it over a network. Understanding serialization, its intricacies, and its impact on inheritance, customization, and performance is essential for effective Java programming.

#### 1. **Introduction to Serialization**

- **Serialization:** The process of converting an object from its current state in memory to a byte stream, which can then be saved to a file or sent over a network.
- **Deserialization:** The reverse process, where the byte stream is converted back into a copy of the object.

**Key Classes:**

- `ObjectOutputStream` and `FileOutputStream` are used for serialization.
- `ObjectInputStream` and `FileInputStream` are used for deserialization.

**Example:**

```java
import java.io.*;

class Dog implements Serializable {
    int i = 10;
    int j = 20;
}

public class SerializeDemo {
    public static void main(String[] args) throws Exception {
        Dog d1 = new Dog();
        
        // Serialization
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(d1);
        
        // Deserialization
        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Dog d2 = (Dog) ois.readObject();
        
        System.out.println(d2.i + "..." + d2.j);
    }
}
```

**Output:**

```
10...20
```

#### 2. **Object Graph in Serialization**

When an object is serialized, all objects that are reachable from that object (the object graph) are serialized as well. Every object in the graph must be serializable; otherwise, a `NotSerializableException` is thrown.

**Example:**

```java
import java.io.*;

class Dog implements Serializable {
    Cat c = new Cat();
}

class Cat implements Serializable {
    Rat r = new Rat();
}

class Rat implements Serializable {
    int j = 0;
}

public class TestSerialized {
    public static void main(String[] args) throws Exception {
        Dog d1 = new Dog();
        
        // Serialization
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(d1);
        
        // Deserialization
        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Dog d2 = (Dog) ois.readObject();
        System.out.println(d2.c.r.j);
    }
}
```

**Output:**

```
0
```

#### 3. **Customized Serialization**

Customized serialization allows us to control the serialization and deserialization process to avoid loss of data or to perform additional tasks during serialization.

**Methods for Customized Serialization:**

- `private void writeObject(ObjectOutputStream os) throws Exception {}`
- `private void readObject(ObjectInputStream is) throws Exception {}`

**Example:**

```java
import java.io.*;

class Account implements Serializable {
    String userName = "Durga";
    transient String passwd = "software";
    
    private void writeObject(ObjectOutputStream oos) throws Exception {
        oos.defaultWriteObject();
        String epwd = "123" + passwd;
        oos.writeObject(epwd);
    }
    
    private void readObject(ObjectInputStream ois) throws Exception {
        ois.defaultReadObject();
        String epwd = (String) ois.readObject();
        passwd = epwd.substring(3);
    }
}

public class CustomSerializedDemo {
    public static void main(String[] args) throws Exception {
        Account a1 = new Account();
        System.out.println(a1.userName + "..." + a1.passwd);
        
        // Serialization
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(a1);
        
        // Deserialization
        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Account a2 = (Account) ois.readObject();
        System.out.println(a2.userName + "..." + a2.passwd);
    }
}
```

**Output:**

```
Durga...software
Durga...software
```

#### 4. **Serialization with Respect to Inheritance**

- **Serializable Parent:** If a parent class implements the `Serializable` interface, all child classes are automatically serializable.
- **Non-Serializable Parent:** If a parent class does not implement `Serializable` but the child class does:
  - The parent's state will not be saved; instead, the default values are assigned.
  - During deserialization, the JVM calls the no-argument constructor of the non-serializable parent class to initialize its state.

**Important Note:** Every non-serializable class must have a no-argument constructor, either default or explicitly provided; otherwise, deserialization will fail with `InvalidClassException`.

**Example:**

```java
import java.io.*;

class Animal {
    int i = 10;
    
    // No-argument constructor
    Animal() {
        System.out.println("Animal constructor called");
    }
}

class Dog extends Animal implements Serializable {
    int j = 20;
    
    Dog() {
        System.out.println("Dog constructor called");
    }
}

public class SerializeDemoInheritance {
    public static void main(String[] args) throws Exception {
        Dog d1 = new Dog();
        d1.i = 888;
        d1.j = 999;
        
        // Serialization
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        oos.writeObject(d1);
        
        // Deserialization
        System.out.println("Deserializing starts");
        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Dog d2 = (Dog) ois.readObject();
        
        System.out.println(d2.i + "..." + d2.j);
    }
}
```

**Output:**

```
Animal constructor called
Dog constructor called
Deserializing starts
Animal constructor called
10...999
```

#### 5. **Externalization**

Externalization provides more control over the serialization process than the default serialization. It allows the programmer to decide exactly what to serialize and what not to, which can improve performance.

**Externalizable Interface Methods:**

- `void writeExternal(ObjectOutput out)`
- `void readExternal(ObjectInput in)`

**Example:**

```java
import java.io.*;

class Account implements Externalizable {
    String userName;
    String passwd;
    
    public Account() {
        // Required no-arg constructor
    }

    public void writeExternal(ObjectOutput out) throws IOException {
        out.writeObject(userName);
        out.writeObject("123" + passwd);  // Simple encryption example
    }

    public void readExternal(ObjectInput in) throws IOException, ClassNotFoundException {
        userName = (String) in.readObject();
        String epwd = (String) in.readObject();
        passwd = epwd.substring(3);  // Decryption
    }
}

public class ExternalizationDemo {
    public static void main(String[] args) throws Exception {
        Account a1 = new Account();
        a1.userName = "Durga";
        a1.passwd = "software";
        
        // Serialization
        FileOutputStream fos = new FileOutputStream("abc.ser");
        ObjectOutputStream oos = new ObjectOutputStream(fos);
        a1.writeExternal(oos);
        oos.close();
        
        // Deserialization
        FileInputStream fis = new FileInputStream("abc.ser");
        ObjectInputStream ois = new ObjectInputStream(fis);
        Account a2 = new Account();
        a2.readExternal(ois);
        
        System.out.println(a2.userName + "..." + a2.passwd);
    }
}
```

**Output:**

```
Pandac...software
```

#### 6. **Serial Version UID**

`serialVersionUID` is a unique identifier for each Serializable class and is used during deserialization to ensure that the sender and receiver of a serialized object have loaded classes that are compatible. If no UID is explicitly specified, Java generates one automatically, but this can lead to `InvalidClassException` if the class definition changes.

**Best Practice:** Always declare `serialVersionUID` explicitly to avoid compatibility issues.

```java
private static final long serialVersionUID = 1L;
```

### Key Points to Remember

- **Transient Keyword:** Used to prevent certain fields from being serialized.
- **Serialization Order:** The order of objects during serialization must match the order during deserialization.
- **Object Graph:** All objects within an object's graph must be serializable.
- **Custom Serialization:** Provides more control and prevents data loss for transient fields.
- **Inheritance and Serialization:** Serializable nature can be inherited, but non-serializable parents require special handling.
- **Externalization:** Offers more control and can enhance performance by allowing selective serialization.
