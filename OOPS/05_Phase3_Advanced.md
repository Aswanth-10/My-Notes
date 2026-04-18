# 🔴 Phase 3: Advanced & Real-World — SOLID, Design Patterns, Generics, Collections
#phase3 #java #oop #solid #designpatterns #generics #collections
← [[04_Phase2_Pattern_Mastery]] | [[06_Templates_and_Patterns]] →

---

## 📌 1. SOLID Principles

### Core Intuition
> SOLID = 5 rules that make OOP code maintainable, extensible, and not a nightmare to change.

---

### S — Single Responsibility Principle
> A class should have ONE reason to change.

```java
// ❌ WRONG — does too many things
public class Student {
    public void study() { }
    public void saveToDatabase() { }   // DB concern
    public void sendEmail() { }        // Email concern
    public void printReport() { }      // Report concern
}

// ✅ CORRECT — each class does ONE thing
public class Student { public void study() { } }
public class StudentRepository { public void save(Student s) { } }
public class StudentNotifier { public void sendEmail(Student s) { } }
public class StudentReporter { public void print(Student s) { } }
```

---

### O — Open/Closed Principle
> Open for EXTENSION, Closed for MODIFICATION.

```java
// ❌ WRONG — adding new shape means changing existing code
public class AreaCalculator {
    public double calculate(Object shape) {
        if (shape instanceof Circle) { ... }
        else if (shape instanceof Rectangle) { ... }
        // Adding Triangle means editing THIS class — risky!
    }
}

// ✅ CORRECT — new shapes extend without changing AreaCalculator
public abstract class Shape {
    public abstract double area();
}
public class Circle extends Shape {
    public double area() { return Math.PI * r * r; }
}
public class Triangle extends Shape {
    public double area() { return 0.5 * base * height; }
}
public class AreaCalculator {
    public double calculate(Shape shape) {
        return shape.area();  // Never changes!
    }
}
```

---

### L — Liskov Substitution Principle
> If S extends P, you must be able to use S wherever P is expected — WITHOUT breaking things.

```java
// ❌ WRONG — Square "is-a" Rectangle breaks LSP
public class Rectangle {
    protected int width, height;
    public void setWidth(int w) { width = w; }
    public void setHeight(int h) { height = h; }
    public int area() { return width * height; }
}
public class Square extends Rectangle {
    @Override
    public void setWidth(int w) { width = height = w; }  // breaks Rectangle behavior!
    @Override
    public void setHeight(int h) { width = height = h; }
}

// ✅ CORRECT — Use composition or separate hierarchy
public abstract class Shape { public abstract int area(); }
public class Rectangle extends Shape { ... }
public class Square extends Shape { ... }
```

---

### I — Interface Segregation Principle
> Don't force classes to implement methods they don't need.

```java
// ❌ WRONG — fat interface
public interface Worker {
    void work();
    void eat();
    void sleep();  // Robot doesn't eat or sleep!
}

// ✅ CORRECT — segregated interfaces
public interface Workable { void work(); }
public interface Eatable { void eat(); }
public interface Sleepable { void sleep(); }

public class Human implements Workable, Eatable, Sleepable { ... }
public class Robot implements Workable { ... }  // Only implements what it needs
```

---

### D — Dependency Inversion Principle
> Depend on ABSTRACTIONS (interfaces), not CONCRETIONS (concrete classes).

```java
// ❌ WRONG — tightly coupled to MySQLDatabase
public class UserService {
    private MySQLDatabase db = new MySQLDatabase();
    public void save(User u) { db.save(u); }
}

// ✅ CORRECT — depends on abstraction
public interface Database {
    void save(Object obj);
}
public class MySQLDatabase implements Database { ... }
public class MongoDatabase implements Database { ... }

public class UserService {
    private Database db;  // depends on interface
    public UserService(Database db) { this.db = db; }  // Dependency Injection
    public void save(User u) { db.save(u); }
}
// Now switch database by just passing different implementation
UserService service = new UserService(new MongoDatabase());
```

---

## 📌 2. Design Patterns (The Big 6 for OOP)

### Pattern 1: Singleton
> Only ONE instance of a class ever exists.

```java
public class DatabaseConnection {
    private static DatabaseConnection instance;  // only instance
    private String url;

    private DatabaseConnection() {               // private constructor
        url = "jdbc:mysql://localhost/db";
    }

    public static DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }

    // Thread-safe version
    public static synchronized DatabaseConnection getThreadSafeInstance() {
        if (instance == null) instance = new DatabaseConnection();
        return instance;
    }
}

// Usage
DatabaseConnection conn = DatabaseConnection.getInstance();
```

---

### Pattern 2: Factory Method
> Let subclasses/methods decide which object to create.

```java
public abstract class Animal {
    public abstract void speak();

    // Factory method
    public static Animal createAnimal(String type) {
        return switch (type) {
            case "dog" -> new Dog();
            case "cat" -> new Cat();
            default -> throw new IllegalArgumentException("Unknown: " + type);
        };
    }
}

// Usage
Animal a = Animal.createAnimal("dog");
a.speak();
```

---

### Pattern 3: Builder
> Construct complex objects step by step. Avoids telescoping constructors.

```java
public class Person {
    private final String firstName;    // required
    private final String lastName;     // required
    private final String email;        // optional
    private final int age;             // optional

    private Person(Builder builder) {
        this.firstName = builder.firstName;
        this.lastName = builder.lastName;
        this.email = builder.email;
        this.age = builder.age;
    }

    public static class Builder {
        private final String firstName;
        private final String lastName;
        private String email;
        private int age;

        public Builder(String firstName, String lastName) {
            this.firstName = firstName;
            this.lastName = lastName;
        }

        public Builder email(String email) { this.email = email; return this; }
        public Builder age(int age) { this.age = age; return this; }
        public Person build() { return new Person(this); }
    }
}

// Usage — readable, no constructor chaos
Person p = new Person.Builder("John", "Doe")
    .email("john@example.com")
    .age(25)
    .build();
```

---

### Pattern 4: Observer
> When one object changes, notify all dependents automatically.

```java
// OBSERVER INTERFACE
public interface Observer {
    void update(String event);
}

// SUBJECT (Observable)
public class EventSystem {
    private List<Observer> observers = new ArrayList<>();

    public void subscribe(Observer o) { observers.add(o); }
    public void unsubscribe(Observer o) { observers.remove(o); }

    public void notify(String event) {
        for (Observer o : observers) {
            o.update(event);
        }
    }
}

// CONCRETE OBSERVERS
public class EmailNotifier implements Observer {
    public void update(String event) {
        System.out.println("Email sent for: " + event);
    }
}
public class SMSNotifier implements Observer {
    public void update(String event) {
        System.out.println("SMS sent for: " + event);
    }
}

// Usage
EventSystem events = new EventSystem();
events.subscribe(new EmailNotifier());
events.subscribe(new SMSNotifier());
events.notify("New Order Placed");
```

---

### Pattern 5: Strategy
> Define a family of algorithms, encapsulate each, and make them interchangeable.

```java
// STRATEGY INTERFACE
public interface SortStrategy {
    void sort(int[] arr);
}

// STRATEGIES
public class BubbleSort implements SortStrategy {
    public void sort(int[] arr) { /* bubble sort */ }
}
public class QuickSort implements SortStrategy {
    public void sort(int[] arr) { /* quick sort */ }
}

// CONTEXT
public class Sorter {
    private SortStrategy strategy;

    public Sorter(SortStrategy strategy) { this.strategy = strategy; }
    public void setStrategy(SortStrategy s) { this.strategy = s; }
    public void sort(int[] arr) { strategy.sort(arr); }
}

// Usage — swap strategies at runtime
Sorter sorter = new Sorter(new BubbleSort());
sorter.sort(arr);
sorter.setStrategy(new QuickSort());  // change strategy
sorter.sort(arr);
```

---

## 📌 3. Generics

### Core Intuition
> Write code that works for ANY type, with type safety at compile time.

### ✅ Generic Templates
```java
// GENERIC CLASS
public class Box<T> {
    private T content;

    public Box(T content) { this.content = content; }
    public T getContent() { return content; }
    public void setContent(T content) { this.content = content; }
}

Box<String> stringBox = new Box<>("Hello");
Box<Integer> intBox = new Box<>(42);

// GENERIC METHOD
public static <T extends Comparable<T>> T findMax(T a, T b) {
    return a.compareTo(b) >= 0 ? a : b;
}

// BOUNDED TYPE PARAMETER
public class NumberBox<T extends Number> {  // only Number and subclasses
    private T value;
    public double doubleValue() { return value.doubleValue(); }
}

// WILDCARDS
public void printList(List<?> list) { /* any type */ }
public void addNumbers(List<? extends Number> list) { /* read-only, any Number */ }
public void addToList(List<? super Integer> list) { /* write Integer or subtypes */ }
```

---

## 📌 4. Collections (OOP Applied)

### When to Use Which Collection
```
Need ORDERED list with duplicates?
    → ArrayList (fast read) or LinkedList (fast insert/delete)

Need UNIQUE elements?
    → HashSet (fastest) → TreeSet (sorted) → LinkedHashSet (insertion order)

Need KEY-VALUE pairs?
    → HashMap (fastest) → TreeMap (sorted by key) → LinkedHashMap (insertion order)

Need FIFO queue?
    → LinkedList as Queue, or ArrayDeque

Need SORTED automatically?
    → TreeSet / TreeMap
```

### ✅ Collections Template
```java
// LIST
List<String> list = new ArrayList<>();
list.add("Alice"); list.add("Bob");
list.get(0);           // O(1)
list.remove("Alice");
Collections.sort(list);

// SET
Set<String> set = new HashSet<>();
set.add("Apple"); set.add("Apple"); // only one "Apple"
set.contains("Apple");              // O(1) for HashSet

// MAP
Map<String, Integer> map = new HashMap<>();
map.put("Alice", 90);
map.get("Alice");                   // 90
map.getOrDefault("Bob", 0);         // 0 (safe default)
map.containsKey("Alice");

// Iterating Map
for (Map.Entry<String, Integer> entry : map.entrySet()) {
    System.out.println(entry.getKey() + " → " + entry.getValue());
}

// SORTING with Comparator
List<Student> students = new ArrayList<>();
students.sort(Comparator.comparing(Student::getName));
students.sort(Comparator.comparingInt(Student::getAge).reversed());
```

### Comparable vs Comparator
```java
// Comparable — natural order (inside the class)
public class Student implements Comparable<Student> {
    private int age;
    @Override
    public int compareTo(Student other) {
        return Integer.compare(this.age, other.age);
    }
}
Collections.sort(students); // uses compareTo

// Comparator — external, custom order
Comparator<Student> byName = Comparator.comparing(Student::getName);
students.sort(byName);
// OR multiple sort criteria:
students.sort(Comparator.comparing(Student::getName)
                        .thenComparingInt(Student::getAge));
```

---

## 📌 5. equals() and hashCode() Contract

### Core Intuition
> If two objects are `equal()`, they MUST have the same `hashCode()`. Always override both together.

```java
public class Student {
    private String id;
    private String name;

    @Override
    public boolean equals(Object obj) {
        if (this == obj) return true;              // same reference
        if (obj == null) return false;
        if (getClass() != obj.getClass()) return false;
        Student other = (Student) obj;
        return Objects.equals(id, other.id);       // compare by id
    }

    @Override
    public int hashCode() {
        return Objects.hash(id);                   // hash based on same field(s)
    }
}
```

---

## ✅ Phase 3 Completion Checklist
- [ ] Can explain all 5 SOLID principles with examples
- [ ] Can identify SOLID violations in code and fix them
- [ ] Can implement Singleton, Factory, Builder patterns
- [ ] Can implement Observer and Strategy patterns
- [ ] Can write generic classes and methods with bounds
- [ ] Can choose the right Collection type for any scenario
- [ ] Can implement Comparable and Comparator
- [ ] Can override equals() and hashCode() correctly

---
*Next: [[06_Templates_and_Patterns]]*
