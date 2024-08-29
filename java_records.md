1. Define a `Person` record class with fields `name` and `age`.
2. Define a `Student` record class that extends `Person` and adds a field `studentId`.
3. Define a `Teacher` record class that extends `Person` and adds a field `subject`.
4. Demonstrate the usage of these record classes in a `main` method.

### Code

#### `src/Person.java`
```java
// Define the record class Person
public record Person(String name, int age) {
}
```

#### `src/Student.java`
```java
// Define the record class Student that extends Person
public record Student(String name, int age, String studentId) {
    public Student {
        // Custom constructor logic (if needed)
        if (age < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
    }
}
```

#### `src/Teacher.java`
```java
// Define the record class Teacher that extends Person
public record Teacher(String name, int age, String subject) {
    public Teacher {
        // Custom constructor logic (if needed)
        if (age < 0) {
            throw new IllegalArgumentException("Age cannot be negative");
        }
    }
}
```

#### `src/Test.java`
```java
// Main class to demonstrate the usage
public class Test {
    public static void main(String[] args) {
        Person person = new Person("Alice", 30);
        Student student = new Student("Bob", 20, "S12345");
        Teacher teacher = new Teacher("Charlie", 40, "Mathematics");

        System.out.println("Person: " + person);
        System.out.println("Student: " + student);
        System.out.println("Teacher: " + teacher);
    }
}
```

### Explanation
- `Person` is a record class with fields `name` and `age`.
- `Student` is a record class that extends `Person` and adds a field `studentId`.
- `Teacher` is a record class that extends `Person` and adds a field `subject`.
- The `main` method demonstrates creating instances of these record classes and printing their details.
