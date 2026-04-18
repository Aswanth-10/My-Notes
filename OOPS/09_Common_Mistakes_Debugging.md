# 🐛 Common Mistakes & Debugging Guide
#mistakes #debugging #java #oop #errors
← [[08_Practice_Problem_Map]] | [[10_Revision_Retention_System]] →

---

## 🔴 Compile-Time Errors (Caught by IDE)

### Mistake 1: Calling instance method in static context
```java
// ❌ ERROR
public class Student {
    private String name;
    public static void main(String[] args) {
        System.out.println(name);  // ERROR: non-static variable cannot be referenced
    }
}

// ✅ FIX
public static void main(String[] args) {
    Student s = new Student("Alice");
    System.out.println(s.name);   // access via object
}
```

### Mistake 2: Forgetting `super()` must be first
```java
// ❌ ERROR
public Dog(String name, String breed) {
    this.breed = breed;
    super(name);          // ERROR: super() must be first statement
}

// ✅ FIX
public Dog(String name, String breed) {
    super(name);          // always first!
    this.breed = breed;
}
```

### Mistake 3: Not implementing all interface methods
```java
// ❌ ERROR
public class Duck implements Flyable, Swimmable {
    public void fly() { }
    // forgot swim() → compile error!
}

// ✅ FIX — implement ALL methods, or make class abstract
public class Duck implements Flyable, Swimmable {
    public void fly() { }
    public void swim() { }
}
```

### Mistake 4: Trying to instantiate abstract class
```java
// ❌ ERROR
Shape s = new Shape();    // ERROR: Shape is abstract

// ✅ FIX
Shape s = new Circle("red", 5.0);   // use concrete subclass
```

---

## 🟡 Runtime Errors (Crash at Runtime)

### Mistake 5: NullPointerException (NPE)
```java
// ❌ ERROR
Student s;                // declared but not initialized
s.getName();              // NPE! s is null

// ✅ FIX
Student s = new Student("Alice");  // always initialize
// OR check before use:
if (s != null) { s.getName(); }
```

### Mistake 6: ClassCastException — unsafe downcast
```java
// ❌ ERROR
Animal a = new Cat("Whiskers", 2);
Dog d = (Dog) a;          // ClassCastException! Cat cannot be cast to Dog

// ✅ FIX — always check with instanceof
if (a instanceof Dog) {
    Dog d = (Dog) a;
}
// Java 16+ cleaner:
if (a instanceof Dog d) {
    d.bark();
}
```

### Mistake 7: StackOverflowError — infinite recursion
```java
// ❌ ERROR
public int factorial(int n) {
    return n * factorial(n);    // forgot to reduce n → infinite loop
}

// ✅ FIX
public int factorial(int n) {
    if (n <= 1) return 1;       // base case!
    return n * factorial(n - 1);
}
```

---

## 🔵 Logic Errors (Code runs but wrong result)

### Mistake 8: `this.field = field` confusion
```java
// ❌ WRONG — does nothing!
public void setName(String name) {
    name = name;     // assigns parameter to itself!
}

// ✅ FIX
public void setName(String name) {
    this.name = name;  // this.name = field, name = parameter
}
```

### Mistake 9: Shallow copy instead of deep copy
```java
// ❌ WRONG — both objects share same array!
public Student(Student other) {
    this.grades = other.grades;     // shallow copy
}
// Changing other.grades now changes this.grades too!

// ✅ FIX — deep copy
public Student(Student other) {
    this.grades = Arrays.copyOf(other.grades, other.grades.length);
}
```

### Mistake 10: equals() without hashCode()
```java
// ❌ WRONG — works in list, fails in HashSet/HashMap
@Override
public boolean equals(Object o) { ... }
// Missing hashCode → HashSet treats equal objects as different!

// ✅ FIX — ALWAYS override both together
@Override
public boolean equals(Object o) { ... }
@Override
public int hashCode() { return Objects.hash(id); }
```

### Mistake 11: Modifying static field thinking it's per-object
```java
// ❌ WRONG
Student.count = 5;    // this changes for ALL students!
// They wanted to change only one student's something

// ✅ FIX — understand what's static vs instance
// static = shared by all objects
// instance = each object has its own copy
```

---

## 🟠 OOP Design Mistakes

### Mistake 12: Inheritance for code reuse (wrong!)
```java
// ❌ WRONG REASON — Dog extends Vehicle just to reuse move()
// Dog is NOT a Vehicle!

// ✅ FIX — Use COMPOSITION for code reuse, INHERITANCE for IS-A
public class Dog {
    private Legs legs;  // composition — has legs
    public void move() { legs.walk(); }
}
```

### Mistake 13: Making everything public (no encapsulation)
```java
// ❌ WRONG
public class Person {
    public String name;
    public int age;
    public double salary;  // anyone can set salary = -1!
}

// ✅ FIX — private fields + controlled access
public class Person {
    private String name;
    private int age;
    private double salary;
    public void setSalary(double s) {
        if (s < 0) throw new IllegalArgumentException("Salary cannot be negative");
        this.salary = s;
    }
}
```

### Mistake 14: Fat class (violates SRP)
```java
// ❌ WRONG — one class does everything
public class Student {
    // data
    // calculateGPA()
    // saveToDatabase()  // should be in Repository
    // sendEmailReport() // should be in Notifier
    // printTranscript() // should be in Printer
}

// ✅ FIX — split into focused classes
```

---

## 🔧 Debugging Workflow
```
When code doesn't work:
1. READ the error message carefully — what TYPE of error?
   - Compile error → fix syntax/type issue
   - NullPointerException → find where object is null
   - ClassCastException → find unsafe cast, add instanceof check
   - Logic error → add print statements to trace values

2. LOCATE the line number in error
3. ADD sysout to see variable values
   System.out.println("DEBUG: value = " + variable);
4. TRACE the execution flow mentally
5. CHECK your constructor — is object initialized?
6. CHECK your if conditions — is condition ever met?
7. Google the EXACT error message if stuck
```

---

## ⚠️ My Personal Mistake Log
> Add your own mistakes here as you encounter them

| Date | Mistake | Fix | Note |
|------|---------|-----|------|
| | | | |
| | | | |
