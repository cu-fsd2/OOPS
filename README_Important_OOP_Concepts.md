# Important Concepts in OOP (Java) -- Quick Classroom Reference

This README is a concise, classroom-ready guide to the important
supporting concepts in Object-Oriented Programming (OOP) beyond the 4
pillars.

------------------------------------------------------------------------

## Table of Contents

1.  this keyword\
2.  super keyword\
3.  Constructors\
4.  Method Overloading\
5.  Method Overriding (@Override)\
6.  static keyword\
7.  final keyword\
8.  Abstract Classes & Methods\
9.  Composition vs Inheritance\
10. Access Modifiers\
11. Common Interview/Exam Pitfalls\
12. Quick Recap

------------------------------------------------------------------------

## 1. this keyword (Current Object Reference)

``` java
class Student {
    String name;

    Student(String name) {
        this.name = name;
    }
}
```

------------------------------------------------------------------------

## 2. super keyword (Parent Reference)

``` java
class Person {
    String name = "Parent";
    void greet() { System.out.println("Hello from Person"); }
}

class Student extends Person {
    String name = "Child";

    void show() {
        System.out.println(super.name);
        super.greet();
    }
}
```

------------------------------------------------------------------------

## 3. Constructors

``` java
class User {
    String username;

    User(String username) {
        this.username = username;
    }
}
```

------------------------------------------------------------------------

## 4. Method Overloading

``` java
class Calculator {
    int add(int a, int b) { return a + b; }
    int add(int a, int b, int c) { return a + b + c; }
}
```

------------------------------------------------------------------------

## 5. Method Overriding

``` java
class Animal {
    void sound() { System.out.println("Animal sound"); }
}

class Dog extends Animal {
    @Override
    void sound() { System.out.println("Dog barks"); }
}
```

------------------------------------------------------------------------

## 6. static keyword

``` java
class MathUtil {
    static int add(int a, int b) { return a + b; }
}
```

------------------------------------------------------------------------

## 7. final keyword

``` java
final class Constants {
    static final double PI = 3.14;
}
```

------------------------------------------------------------------------

## 8. Abstract Classes

``` java
abstract class Vehicle {
    abstract void move();
}

class Car extends Vehicle {
    void move() { System.out.println("Car is moving"); }
}
```

------------------------------------------------------------------------

## 9. Composition vs Inheritance

``` java
class Engine {}

class Car {
    private Engine engine = new Engine();
}
```

------------------------------------------------------------------------

## 10. Access Modifiers

``` java
class Account {
    private double balance;
    public double getBalance() { return balance; }
}
```

------------------------------------------------------------------------

## 11. Common Pitfalls

-   Overloading ≠ Overriding\
-   static methods cannot be overridden\
-   final methods cannot be overridden\
-   Cannot instantiate abstract classes

------------------------------------------------------------------------

## 12. Quick Recap

-   this → current object\
-   super → parent object\
-   Constructors → object initialization\
-   Overloading → compile-time\
-   Overriding → runtime\
-   static → class-level\
-   final → no further change\
-   Composition \> Inheritance

------------------------------------------------------------------------

Happy Teaching!
