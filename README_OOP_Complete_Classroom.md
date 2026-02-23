# OOP Concepts in Java -- Complete Classroom Guide (with Enterprise Examples)

This README is a **ready-to-teach classroom guide** for
**Object-Oriented Programming (OOP) in Java**.\
It includes **clear explanations, simple examples, diagrams-in-text, and
2 enterprise-level examples** that map naturally to Spring Boot and
backend development.

------------------------------------------------------------------------

## Table of Contents

1.  What is OOP?
2.  Class & Object\
3.  Encapsulation\
4.  Inheritance\
5.  Polymorphism\
6.  Abstraction\
7.  Interface vs Abstract Class\
8.  How OOP Maps to Backend & Spring Boot\
9.  Enterprise Example 1 -- Notification System\
10. Enterprise Example 2 -- Payment Gateway\
11. Mini Exercises for Students\
12. Key Takeaways

------------------------------------------------------------------------

## 1. What is OOP?

**OOP (Object-Oriented Programming)** is a programming paradigm based on
the concept of **objects**.

> Objects represent real-world entities with **state (data)** and
> **behavior (methods)**.

**Example:** - Student (name, rollNo, study()) - BankAccount (balance,
deposit(), withdraw())

**Why OOP?** - Code reusability\
- Better structure\
- Easier maintenance\
- Scalable for large systems (enterprise apps)

------------------------------------------------------------------------

## 2. Class & Object

### Definition

-   **Class** → Blueprint\
-   **Object** → Real instance created from the class

### Example

``` java
class Student {
    String name;
    int age;

    void study() {
        System.out.println(name + " is studying");
    }
}

public class Main {
    public static void main(String[] args) {
        Student s1 = new Student();
        s1.name = "Rahul";
        s1.age = 20;
        s1.study();
    }
}
```

**Teaching Line:**\
Class is like a form, Object is a filled form.

------------------------------------------------------------------------

## 3. Encapsulation (Data Hiding)

Encapsulation means: - Keeping data **private** - Accessing data using
**public methods (getters/setters)**

### Example

``` java
class BankAccount {
    private double balance;

    public void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
        }
    }

    public double getBalance() {
        return balance;
    }
}
```

**Why Encapsulation?** - Security\
- Controlled access\
- Prevents misuse of data

**Real-Life Analogy:**\
You cannot directly open a bank vault; you use ATM methods.

------------------------------------------------------------------------

## 4. Inheritance (Code Reusability)

Inheritance allows a child class to acquire properties of a parent
class.

### Example

``` java
class Person {
    String name;

    void walk() {
        System.out.println("Person is walking");
    }
}

class Student extends Person {
    void study() {
        System.out.println(name + " is studying");
    }
}
```

**Concept:**\
Student **is-a** Person.

------------------------------------------------------------------------

## 5. Polymorphism (Many Forms)

Same method name, different behavior.

### Example

``` java
class Animal {
    void sound() {
        System.out.println("Animal makes sound");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("Dog barks");
    }
}

public class Main {
    public static void main(String[] args) {
        Animal a = new Dog();
        a.sound();  // Dog barks
    }
}
```

**Key Idea:**\
Method call depends on object type, not reference type.

------------------------------------------------------------------------

## 6. Abstraction

Abstraction means: - Showing **what to do** - Hiding **how it is done**

### Using Abstract Class

``` java
abstract class Shape {
    abstract double area();
}

class Circle extends Shape {
    double radius = 5;

    double area() {
        return 3.14 * radius * radius;
    }
}
```

------------------------------------------------------------------------

## 7. Interface vs Abstract Class

An interface is a contract.
It tells what methods a class must implement, but not how to implement them.

One-liner you can say in class:

“Interface defines what to do, class defines how to do it.”

### Interface Example

``` java
interface PaymentService {
    void pay(double amount);
}
```
### Main Reasons:

- Abstraction – hide implementation

- Loose coupling – code depends on interface, not concrete class

- Multiple inheritance – Java allows implementing multiple interfaces

- Flexibility – easy to change implementations later (huge in Spring)

### Implementation

``` java
class UpiPaymentService implements PaymentService {
    public void pay(double amount) {
        System.out.println("Paid " + amount + " using UPI");
    }
}
```

### Comparison

  Feature                Interface     Abstract Class
  ---------------------- ------------- ------------------------
  Multiple inheritance   Yes           No
  Method body            No (mostly)   Yes
  Object creation        No            No
  Purpose                Contract      Partial implementation

------------------------------------------------------------------------

## 8. How OOP Maps to Backend & Spring Boot

  OOP Concept     Spring Boot Usage
  --------------- -------------------------
  Class/Object    Controllers, Services
  Encapsulation   Entity fields (private)
  Inheritance     Custom exceptions
  Abstraction     Interfaces (Repository)
  Polymorphism    Dependency Injection

------------------------------------------------------------------------

## 9. Enterprise Example 1 -- Notification System

### Interface

``` java
public interface NotificationService {
    void send(String message);
}
```

### Implementations

``` java
public class EmailNotificationService implements NotificationService {
    public void send(String message) {
        System.out.println("Sending Email: " + message);
    }
}

public class SmsNotificationService implements NotificationService {
    public void send(String message) {
        System.out.println("Sending SMS: " + message);
    }
}
```

### Controller Layer

``` java
public class UserController {

    private NotificationService notificationService;

    public UserController(NotificationService notificationService) {
        this.notificationService = notificationService;
    }

    public void notifyUser() {
        notificationService.send("Welcome User!");
    }

    public static void main(String[] args) {
        NotificationService service = new EmailNotificationService();
        UserController controller = new UserController(service);
        controller.notifyUser();
    }
}
```

**Enterprise Mapping:**\
Same pattern used in Spring Boot with Dependency Injection.

------------------------------------------------------------------------

## 10. Enterprise Example 2 -- Payment Gateway

``` java
public interface PaymentGateway {
    void process(double amount);
}

public class RazorpayGateway implements PaymentGateway {
    public void process(double amount) {
        System.out.println("Processing payment via Razorpay: " + amount);
    }
}

public class PaypalGateway implements PaymentGateway {
    public void process(double amount) {
        System.out.println("Processing payment via PayPal: " + amount);
    }
}

public class PaymentService {

    private PaymentGateway gateway;

    public PaymentService(PaymentGateway gateway) {
        this.gateway = gateway;
    }

    public void pay(double amount) {
        gateway.process(amount);
    }

    public static void main(String[] args) {
        PaymentGateway gateway = new RazorpayGateway();
        PaymentService service = new PaymentService(gateway);
        service.pay(1000);
    }
}
```

------------------------------------------------------------------------

## 11. Mini Exercises

1.  Create class `Employee` with id, name, salary.
2.  Create subclass `Manager` and override display method.
3.  Create interface `Shape` with method `area()` and implement Circle &
    Rectangle.

------------------------------------------------------------------------

## 12. Key Takeaways

-   OOP helps build **scalable systems**
-   Interfaces provide **flexibility**
-   Encapsulation provides **security**
-   Inheritance provides **reusability**
-   Polymorphism provides **dynamic behavior**
-   Spring Boot is built completely on these ideas

------------------------------------------------------------------------

