
# SOLID Principles

## Low Level Design

SOLID is an acronym for five object-oriented design principles that help you write **clean, maintainable, and scalable code**.
Mastering these is the **foundation of professional Low Level Design (LLD).**

| Letter | Principle | One-Line Summary |
|------|-----------|----------------|
| S | Single Responsibility | One class = One job |
| O | Open/Closed | Open for extension, closed for modification |
| L | Liskov Substitution | Subtypes must be substitutable for base types |
| I | Interface Segregation | Don't force classes to implement unused methods |
| D | Dependency Inversion | Depend on abstractions, not concretions |

---

# S — Single Responsibility Principle (SRP)

> **"A class should have only one reason to change"**

## What does it mean?

Every class should focus on doing **one thing well**.
If a class handles multiple responsibilities, a change to one responsibility can break unrelated functionality.

---

## ❌ Violation — Bad Example

```java
class Employee {

    String name;
    double salary;

    double calculateBonus() {
        return salary * 0.10;
    }

    void saveToDatabase() {
        // SQL code here
    }

    void generatePayslip() {
        // Format payslip
    }
}
```

Problem:
- Business logic
- Database logic
- Reporting logic

All in **one class**.

---

## ✅ Fix — Good Example

```java
class Employee {
    String name;
    double salary;

    double calculateBonus() {
        return salary * 0.10;
    }
}

class EmployeeRepository {
    void save(Employee e) {
        // DB operations
    }
}

class PayslipGenerator {
    void generate(Employee e) {
        // Report generation
    }
}
```

### Key Takeaway

Ask: **What is this class responsible for?**
The answer should be **one thing only**.

---

# O — Open/Closed Principle (OCP)

> **"Open for extension, closed for modification"**

## What does it mean?

You should be able to **add new behavior without modifying existing code**.

---

## ❌ Violation — Bad Example

```java
class AreaCalculator {

    double calculateArea(Object shape) {

        if (shape instanceof Circle) {
            Circle c = (Circle) shape;
            return Math.PI * c.radius * c.radius;

        } else if (shape instanceof Rectangle) {
            Rectangle r = (Rectangle) shape;
            return r.width * r.height;
        }

        return 0;
    }
}
```

Problem:
Adding **Triangle** requires modifying this class.

---

## ✅ Fix — Good Example

```java
interface Shape {
    double calculateArea();
}

class Circle implements Shape {

    double radius;

    public double calculateArea() {
        return Math.PI * radius * radius;
    }
}

class Rectangle implements Shape {

    double width;
    double height;

    public double calculateArea() {
        return width * height;
    }
}

class Triangle implements Shape {

    double base;
    double height;

    public double calculateArea() {
        return 0.5 * base * height;
    }
}

class AreaCalculator {

    double calculateArea(Shape shape) {
        return shape.calculateArea();
    }
}
```

### Key Takeaway

New feature → **Add new class**
Do NOT modify existing class.

---

# L — Liskov Substitution Principle (LSP)

> **"Subclasses must be replaceable for their parent class"**

## ❌ Violation — Square Rectangle Problem

```java
class Rectangle {

    int width;
    int height;

    void setWidth(int w) {
        this.width = w;
    }

    void setHeight(int h) {
        this.height = h;
    }

    int area() {
        return width * height;
    }
}

class Square extends Rectangle {

    void setWidth(int w) {
        this.width = w;
        this.height = w;
    }

    void setHeight(int h) {
        this.height = h;
        this.width = h;
    }
}
```

Usage:

```java
Rectangle r = new Square();

r.setWidth(5);
r.setHeight(10);

// Expected = 50
// Actual = 100
```

---

## ✅ Fix

```java
interface Shape {
    int area();
}

class Rectangle implements Shape {

    int width;
    int height;

    Rectangle(int w, int h) {
        width = w;
        height = h;
    }

    public int area() {
        return width * height;
    }
}

class Square implements Shape {

    int side;

    Square(int s) {
        side = s;
    }

    public int area() {
        return side * side;
    }
}
```

---

# I — Interface Segregation Principle (ISP)

> **"Don't force classes to implement methods they don't need"**

## ❌ Violation

```java
interface Worker {
    void work();
    void eat();
    void sleep();
}
```

Robot forced to implement unnecessary methods.

---

## ✅ Fix

```java
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

interface Sleepable {
    void sleep();
}

class HumanWorker implements Workable, Eatable, Sleepable {

    public void work() {}
    public void eat() {}
    public void sleep() {}
}

class RobotWorker implements Workable {

    public void work() {}
}
```

---

# D — Dependency Inversion Principle (DIP)

> **Depend on abstractions, not concrete classes**

---

## ❌ Violation

```java
class MySQLDatabase {

    void save(String data) {
        System.out.println("Saving to MySQL: " + data);
    }
}

class OrderService {

    MySQLDatabase db = new MySQLDatabase();

    void placeOrder(String order) {
        db.save(order);
    }
}
```

Problem:
Tightly coupled code.

---

## ✅ Fix

```java
interface Database {
    void save(String data);
}

class MySQLDatabase implements Database {

    public void save(String data) {
        System.out.println("Saving to MySQL: " + data);
    }
}

class MongoDatabase implements Database {

    public void save(String data) {
        System.out.println("Saving to MongoDB: " + data);
    }
}

class OrderService {

    private Database db;

    OrderService(Database db) {
        this.db = db;
    }

    void placeOrder(String order) {
        db.save(order);
    }
}
```

Usage:

```java
OrderService s1 = new OrderService(new MySQLDatabase());
OrderService s2 = new OrderService(new MongoDatabase());
```

---

# Quick Reference

| Principle | Meaning |
|----------|--------|
| SRP | One class, one responsibility |
| OCP | Extend without modifying |
| LSP | Subclasses must work like parent |
| ISP | Many small interfaces |
| DIP | Depend on abstractions |

---

# Next Steps

After SOLID learn:

- Factory Pattern
- Builder Pattern
- Singleton Pattern
- Parking Lot LLD Design
- Dependency Injection (Spring)
