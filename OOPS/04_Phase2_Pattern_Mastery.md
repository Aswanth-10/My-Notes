# 🔵 Phase 2: Pattern Mastery — Inheritance, Polymorphism, Abstraction, Interfaces
#phase2 #java #oop #inheritance #polymorphism #abstraction #interfaces
← [[03_Phase1_Foundation]] | [[05_Phase3_Advanced]] →

---

## 📌 1. Inheritance

### Core Intuition
> Child class = Parent class + Extra stuff. You inherit everything, you can override anything.

### ✅ Inheritance Template
```java
// PARENT CLASS
public class Animal {
    protected String name;       // protected = accessible in child
    protected int age;

    public Animal(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public void eat() {
        System.out.println(name + " is eating.");
    }

    public void sleep() {
        System.out.println(name + " is sleeping.");
    }

    @Override
    public String toString() {
        return "Animal{name=" + name + ", age=" + age + "}";
    }
}

// CHILD CLASS
public class Dog extends Animal {
    private String breed;

    // ALWAYS call super() first in child constructor
    public Dog(String name, int age, String breed) {
        super(name, age);        // calls Animal's constructor
        this.breed = breed;
    }

    // NEW METHOD (only Dog has this)
    public void bark() {
        System.out.println(name + " says: Woof!");
    }

    // OVERRIDE (Dog does this differently)
    @Override
    public void eat() {
        System.out.println(name + " eats dog food.");
    }

    @Override
    public String toString() {
        return "Dog{" + super.toString() + ", breed=" + breed + "}";
    }
}
```

### Inheritance Types
```
// Multilevel Inheritance
Animal → Dog → Labrador

// Hierarchical Inheritance
Animal → Dog
Animal → Cat
Animal → Bird
```

### `super` Keyword
```java
// In constructor: call parent constructor
super(args);           // MUST be first line

// In method: call parent version of method
super.eat();           // calls Animal.eat() from inside Dog.eat()

// Access parent field
super.name;            // access Animal's name
```

### ⚠️ Key Rules
- Java supports only **single inheritance** (one parent per class)
- `super()` must be the FIRST statement in child constructor
- `private` fields/methods of parent are NOT inherited (but exist)
- `final` class cannot be extended

---

## 📌 2. Polymorphism (The Most Powerful Concept)

### Core Intuition
> Same interface, different behavior. One reference, many forms.

### ✅ Polymorphism Template
```java
// RUNTIME POLYMORPHISM PATTERN
Animal animal;                          // Parent reference

animal = new Dog("Rex", 3, "Husky");   // Upcasting (automatic)
animal.eat();                           // Calls Dog's eat() → "Rex eats dog food"

animal = new Cat("Whiskers", 2);
animal.eat();                           // Calls Cat's eat() → "Whiskers eats fish"

// POWER: Use parent type in collections
List<Animal> animals = new ArrayList<>();
animals.add(new Dog("Rex", 3, "Husky"));
animals.add(new Cat("Whiskers", 2));
animals.add(new Bird("Tweety", 1));

for (Animal a : animals) {
    a.eat();    // Each calls its OWN version — this is polymorphism!
}
```

### Upcasting vs Downcasting
```java
// UPCASTING — safe, automatic
Animal a = new Dog("Rex", 3, "Lab");   // Dog → Animal

// DOWNCASTING — risky, must cast manually
Dog d = (Dog) a;                       // Animal → Dog

// SAFE DOWNCASTING — always use instanceof first!
if (a instanceof Dog) {
    Dog d = (Dog) a;
    d.bark();
}

// Java 16+ pattern matching (cleaner)
if (a instanceof Dog d) {
    d.bark();  // d is auto-cast
}
```

### Method Overloading (Compile-Time Polymorphism)
```java
// Same method name, different parameters
public class Calculator {
    public int add(int a, int b) { return a + b; }
    public double add(double a, double b) { return a + b; }
    public int add(int a, int b, int c) { return a + b + c; }
    // Resolved at COMPILE TIME based on parameter types
}
```

### Pattern Recognition: Overloading vs Overriding
| | Overloading | Overriding |
|--|------------|-----------|
| Where | Same class | Parent + Child |
| When resolved | Compile-time | Runtime |
| Parameters | Must differ | Must be same |
| `@Override` | Not needed | Required (best practice) |
| Return type | Can differ | Must be same (or covariant) |

---

## 📌 3. Abstract Classes

### Core Intuition
> A class that's INCOMPLETE by design. You cannot instantiate it. It defines the "what", not the "how" for some methods.

### ✅ Abstract Class Template
```java
// ABSTRACT CLASS — partial implementation
public abstract class Shape {
    protected String color;

    public Shape(String color) {
        this.color = color;
    }

    // ABSTRACT METHOD — no body, must be overridden
    public abstract double area();
    public abstract double perimeter();

    // CONCRETE METHOD — has body, inherited as-is
    public void displayInfo() {
        System.out.println("Shape: " + color + ", Area: " + area());
    }
}

// CONCRETE SUBCLASS — must implement ALL abstract methods
public class Circle extends Shape {
    private double radius;

    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }

    @Override
    public double area() {
        return Math.PI * radius * radius;
    }

    @Override
    public double perimeter() {
        return 2 * Math.PI * radius;
    }
}

public class Rectangle extends Shape {
    private double width, height;

    public Rectangle(String color, double width, double height) {
        super(color);
        this.width = width;
        this.height = height;
    }

    @Override
    public double area() { return width * height; }

    @Override
    public double perimeter() { return 2 * (width + height); }
}
```

---

## 📌 4. Interfaces

### Core Intuition
> A pure contract. "If you implement me, you MUST provide these behaviors." Zero implementation (mostly). Enables multiple inheritance of type.

### ✅ Interface Template
```java
// INTERFACE DEFINITION
public interface Flyable {
    // All fields are public static final by default
    double MAX_ALTITUDE = 10000.0;

    // All methods are public abstract by default
    void fly();
    void land();

    // DEFAULT METHOD (Java 8+) — has implementation
    default void describeAltitude() {
        System.out.println("Max altitude: " + MAX_ALTITUDE);
    }

    // STATIC METHOD (Java 8+)
    static boolean canFlyInStorm() {
        return false;
    }
}

public interface Swimmable {
    void swim();
}

// CLASS IMPLEMENTING MULTIPLE INTERFACES
public class Duck extends Animal implements Flyable, Swimmable {
    public Duck(String name) {
        super(name, 1);
    }

    @Override public void fly() { System.out.println(name + " is flying!"); }
    @Override public void land() { System.out.println(name + " landed."); }
    @Override public void swim() { System.out.println(name + " is swimming!"); }
}
```

### Abstract Class vs Interface — Decision Tree
```
Does the class share CODE (concrete methods) across subclasses?
  ↓ YES → Abstract Class
  ↓ NO  → Interface

Does the class need CONSTRUCTORS or instance fields?
  ↓ YES → Abstract Class
  ↓ NO  → Interface (fields are static final)

Is this a "IS-A" relationship with shared state?
  ↓ YES → Abstract Class (e.g., Dog IS-A Animal)

Is this a "CAN-DO" capability/contract?
  ↓ YES → Interface (e.g., Dog CAN Runnable, Serializable)

Does the class need to implement MULTIPLE behaviors?
  ↓ YES → Interface (Java doesn't allow multiple inheritance of classes)
```

### Abstract Class vs Interface — Comparison Table
| Feature | Abstract Class | Interface |
|---------|---------------|-----------|
| Instantiation | ❌ No | ❌ No |
| Constructors | ✅ Yes | ❌ No |
| Instance fields | ✅ Yes | ❌ No (only static final) |
| Concrete methods | ✅ Yes | ✅ Default/Static only |
| Abstract methods | ✅ Yes | ✅ Yes (implicit) |
| Multiple inheritance | ❌ One parent | ✅ Multiple interfaces |
| Use when | Shared code + IS-A | Pure contract + CAN-DO |

---

## 📌 5. Exception Handling (OOP Way)

### Core Intuition
> Exceptions are objects. You can create your own exception classes.

### ✅ Custom Exception Template
```java
// CUSTOM CHECKED EXCEPTION
public class InsufficientFundsException extends Exception {
    private double amount;

    public InsufficientFundsException(double amount) {
        super("Insufficient funds. Tried to withdraw: " + amount);
        this.amount = amount;
    }

    public double getAmount() { return amount; }
}

// USING CUSTOM EXCEPTION
public class BankAccount {
    private double balance;

    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(amount);
        }
        balance -= amount;
    }
}

// CATCHING CUSTOM EXCEPTION
try {
    account.withdraw(1000);
} catch (InsufficientFundsException e) {
    System.out.println(e.getMessage());
    System.out.println("Tried: " + e.getAmount());
} finally {
    System.out.println("Transaction attempted.");
}
```

### Exception Hierarchy
```
Throwable
  ├── Error (don't catch — JVM level: OutOfMemoryError)
  └── Exception
        ├── Checked (must handle: IOException, SQLException)
        │     └── Your custom exceptions extend Exception
        └── RuntimeException (unchecked: NullPointerException, etc.)
              └── Your custom runtime exceptions extend RuntimeException
```

---

## 🧠 Phase 2 — Master Decision Tree

```
I need to define a relationship between classes:
         ↓
IS-A relationship? (Dog IS-A Animal)
    ↓ YES → use extends (inheritance)
    ↓
    Does parent have SHARED CODE to give?
        ↓ YES → Concrete parent class or Abstract class
        ↓ NO → Consider Interface

CAN-DO capability? (Duck CAN-DO Flyable)
    ↓ YES → use implements (interface)
    ↓
    Multiple capabilities needed?
        ↓ YES → implement multiple interfaces

Method does different things for different objects?
    ↓ YES → Override method in subclass → Runtime Polymorphism

Same method name, different parameters?
    ↓ YES → Method Overloading → Compile-Time Polymorphism
```

---

## ⚠️ Common Mistakes in Phase 2

| Mistake | Fix |
|---------|-----|
| Forgetting `super()` in child constructor | Always call `super(args)` as FIRST line |
| Not using `@Override` annotation | Always add it — catches typos at compile time |
| Casting without `instanceof` check | Always `if (obj instanceof Dog d)` before cast |
| Trying to instantiate abstract class | `new Shape()` → compile error; must use subclass |
| Not implementing ALL interface methods | Compile error; use abstract class if partial impl needed |
| Accessing private parent field directly | Use `super.getField()` or make it `protected` |

---

## ✅ Phase 2 Completion Checklist
- [ ] Can write parent/child class with proper `super()` usage
- [ ] Can override methods with `@Override`
- [ ] Can explain compile-time vs runtime polymorphism with examples
- [ ] Can safely upcast and downcast with `instanceof`
- [ ] Can design an abstract class with abstract + concrete methods
- [ ] Can design interfaces and implement multiple interfaces
- [ ] Can decide when to use abstract class vs interface
- [ ] Can create custom exception classes

---
*Next: [[05_Phase3_Advanced]]*
