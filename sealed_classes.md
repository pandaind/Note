1. Define a sealed class `Shape` that permits only specific subclasses.
2. Create a non-sealed subclass `Circle`.
3. Create a final subclass `Square`.
4. Create a sealed subclass `Rectangle` that permits further specific subclasses.
5. Create a final subclass `FilledRectangle` extending `Rectangle`.
6. Demonstrate the usage of these classes in a `main` method.

### Code
```java
// Define the sealed class Shape
public sealed class Shape permits Circle, Square, Rectangle {
    public abstract double area();
}

// Define a non-sealed subclass Circle
public non-sealed class Circle extends Shape {
    private final double radius;

    public Circle(double radius) {
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }
}

// Define a final subclass Square
public final class Square extends Shape {
    private final double side;

    public Square(double side) {
        this.side = side;
    }

    @Override
    public double area() {
        return side * side;
    }
}

// Define a sealed subclass Rectangle
public sealed class Rectangle extends Shape permits FilledRectangle {
    private final double length;
    private final double width;

    public Rectangle(double length, double width) {
        this.length = length;
        this.width = width;
    }

    @Override
    public double area() {
        return length * width;
    }
}

// Define a final subclass FilledRectangle
public final class FilledRectangle extends Rectangle {
    public FilledRectangle(double length, double width) {
        super(length, width);
    }
}

// Main class to demonstrate the usage
public class TestSealedClasses {
    public static void main(String[] args) {
        Shape circle = new Circle(5);
        Shape square = new Square(4);
        Shape rectangle = new Rectangle(3, 6);
        Shape filledRectangle = new FilledRectangle(3, 6);

        System.out.println("Circle area: " + circle.area());
        System.out.println("Square area: " + square.area());
        System.out.println("Rectangle area: " + rectangle.area());
        System.out.println("FilledRectangle area: " + filledRectangle.area());
    }
}
```

### Explanation
- `Shape` is a sealed class that permits only `Circle`, `Square`, and `Rectangle` to extend it.
- `Circle` is a non-sealed class, meaning it can be further extended.
- `Square` is a final class, meaning it cannot be extended.
- `Rectangle` is a sealed class that permits only `FilledRectangle` to extend it.
- `FilledRectangle` is a final class extending `Rectangle`.
