
# Design Patterns — Complete Guide

Design patterns are **reusable solutions to common software design problems**.
They are divided into three major categories:

- Creational
- Structural
- Behavioral

---

# Creational Patterns

Creational patterns deal with **object creation mechanisms**.

## 1. Singleton

**Intent:** Ensure a class has only **one instance** and provide a global access point.

**Use Cases**
- Logger
- Configuration Manager
- Database Connection Pool
- Thread Pool

```java
class Singleton {

    private static volatile Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {

        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }

        return instance;
    }
}
```

### Bill Pugh Singleton (Recommended)

```java
class BillPughSingleton {

    private static class Holder {
        static final BillPughSingleton INSTANCE = new BillPughSingleton();
    }

    public static BillPughSingleton getInstance() {
        return Holder.INSTANCE;
    }
}
```

---

## 2. Factory Pattern

**Intent:** Define an interface for creating objects.

```java
interface Notification {
    void send(String msg);
}

class EmailNotification implements Notification {

    private String email;

    EmailNotification(String email) {
        this.email = email;
    }

    public void send(String msg) {
        System.out.println("Email: " + msg);
    }
}
```

### Simple Factory

```java
class NotificationFactory {

    public static Notification create(String type, String target) {

        switch (type) {
            case "email":
                return new EmailNotification(target);
            case "sms":
                return new SMSNotification(target);
            default:
                throw new IllegalArgumentException("Unknown type");
        }
    }
}
```

Usage

```java
Notification n = NotificationFactory.create("email","user@mail.com");
n.send("Order confirmed");
```

---

## 3. Builder Pattern

Used when objects have **many optional parameters**.

```java
class User {

    private final String name;
    private final String email;
    private final String phone;
    private final int age;

    private User(Builder b){
        this.name = b.name;
        this.email = b.email;
        this.phone = b.phone;
        this.age = b.age;
    }

    public static class Builder {

        private final String name;
        private final String email;

        private String phone="";
        private int age=0;

        public Builder(String name,String email){
            this.name=name;
            this.email=email;
        }

        public Builder phone(String p){
            phone=p;
            return this;
        }

        public Builder age(int a){
            age=a;
            return this;
        }

        public User build(){
            return new User(this);
        }
    }
}
```

Usage

```java
User u = new User.Builder("Alice","alice@email.com")
            .phone("+91-9999")
            .age(28)
            .build();
```

---

## 4. Prototype

Create new objects by **cloning an existing object**.

Examples:
- Game characters
- Document templates

---

## 5. Abstract Factory

Creates **families of related objects**.

```java
interface UIFactory {

    Button createButton();
    TextField createTextField();

}
```

---

# Structural Patterns

Structural patterns deal with **class and object composition**.

---

## 6. Adapter

Converts one interface into another expected by the client.

```java
interface PaymentProcessor{
    boolean processPayment(String id,double amount);
}
```

---

## 7. Decorator

Adds behavior to objects **dynamically**.

```java
interface Coffee{

    String getDescription();
    double getCost();

}
```

---

## 8. Facade

Provides a **simplified interface to a complex system**.

Example

```java
orderFacade.placeOrder(customerId,productId,qty,amount,address,email);
```

---

## 9. Proxy

Acts as a **placeholder or access controller** for another object.

Use Cases

- Lazy loading
- Access control
- Caching

---

## 10. Composite

Treats **individual objects and groups uniformly**.

Example: File system structure.

---

# Behavioral Patterns

Behavioral patterns deal with **communication between objects**.

---

## 11. Observer

Defines **one-to-many dependency**.

Example: Stock price alerts.

---

## 12. Strategy

Defines **multiple algorithms** and switches them at runtime.

Example: Payment strategies.

---

## 13. Command

Encapsulates a request as an object.

Used for:
- Undo/Redo
- Task queues

---

## 14. Iterator

Sequential access to collection elements.

---

## 15. Template Method

Defines algorithm structure in base class.

```java
abstract class DataProcessor{

    public final void process(String source){

        String raw = readData(source);
        String parsed = parseData(raw);
        String result = processData(parsed);

        saveData(result);
    }

    protected abstract String readData(String s);
    protected abstract String parseData(String s);
    protected abstract String processData(String s);
}
```

---

# Systems to Practice

Build systems using these patterns:

- Parking Lot System
- ATM Machine
- Chess Game
- Splitwise
- Ride Sharing (Uber)
