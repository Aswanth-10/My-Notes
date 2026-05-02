# 🟢 Phase 1: Foundation — Classes, Objects, Constructors, Encapsulation
#phase1 #java #oop #foundation
← [[02_Complete_Topic_Breakdown]] | [[04_Phase2_Pattern_Mastery]] →

---

## 📌 1. Classes & Objects

### Core Intuition
> A **Class** is a blueprint. An **Object** is a house built FROM that blueprint.
> You can build many houses (objects) from one blueprint (class).

### ✅ Template
```java
// TEMPLATE: Basic Class
public class ClassName {
    // === FIELDS (state) ===
    private dataType fieldName;         // instance field
    private static int count = 0;       // static field (shared)

    // === CONSTRUCTORS ===
    public ClassName() { }              // default
    public ClassName(dataType param) {  // parameterized
        this.fieldName = param;
    }

    // === METHODS (behavior) ===
    public returnType methodName(params) {
        // logic
        return value;
    }

    // === GETTERS & SETTERS ===
    public dataType getFieldName() { return fieldName; }
    public void setFieldName(dataType val) { this.fieldName = val; }

    // === toString (always override) ===
    @Override
    public String toString() {
        return "ClassName{field=" + fieldName + "}";
    }
}

// CREATING AN OBJECT:
ClassName obj = new ClassName(args);
obj.methodName();
```

### When to Use
- Every time you model a real-world entity (Student, Car, BankAccount)
- When you want to group related data + behavior together

### All Important Variations
```java
// Static method — belongs to class, not object
public static void staticMethod() { }
ClassName.staticMethod(); // called on class, not object

// Static field — shared across all objects
private static int objectCount = 0;

// this keyword — refers to current object
public void setName(String name) {
    this.name = name; // 'this.name' = field, 'name' = parameter
}
```

### ⚠️ Edge Cases
- `null` object → calling methods on it → `NullPointerException`
- Static methods CANNOT access instance fields directly
- `this` cannot be used in static context

---

## 📌 2. Constructors (Deep Dive)

### Core Intuition
> Constructor = the moment of birth of an object. It sets up initial state.

### ✅ Constructor Templates

```java
public class Student {
    private String name;
    private int age;
    private String course;

    // 1. DEFAULT CONSTRUCTOR
    public Student() {
        this.name = "Unknown";
        this.age = 0;
    }

    // 2. PARAMETERIZED CONSTRUCTOR
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // 3. CONSTRUCTOR OVERLOADING
    public Student(String name, int age, String course) {
        this.name = name;
        this.age = age;
        this.course = course;
    }

    // 4. CONSTRUCTOR CHAINING with this()
    public Student(String name) {
        this(name, 18); // calls the 2-param constructor
    }

    // 5. COPY CONSTRUCTOR
    public Student(Student other) {
        this.name = other.name;
        this.age = other.age;
    }
}
```

### Pattern Recognition
| Situation | Use |
|-----------|-----|
| Object needs default values | Default Constructor |
| Object must be initialized with data | Parameterized Constructor |
| Different ways to create same object | Constructor Overloading |
| Avoid duplicate initialization code | Constructor Chaining (this()) |
| Create a clone of an object | Copy Constructor |

---

## 📌 3. Access Modifiers

### Core Intuition
> Think of concentric circles: private → package → protected → public

```
+-----------------------------------+
|  public (everyone)                |
|  +-----------------------------+  |
|  | protected (package+child)   |  |
|  |  +----------------------+   |  |
|  |  | default (package)    |   |  |
|  |  |  +---------------+   |   |  | 
|  |  |  | private (me)  |   |   |  |
|  |  |  +---------------+   |   |  |
|  |  +----------------------+   |  |
|  +-----------------------------+  |
+-----------------------------------+
```

### ✅ Access Modifier Table
| Modifier | Same Class | Same Package | Subclass | World |
|----------|-----------|--------------|----------|-------|
| `private` | ✅ | ❌ | ❌ | ❌ |
| `default` | ✅ | ✅ | ❌ | ❌ |
| `protected` | ✅ | ✅ | ✅ | ❌ |
| `public` | ✅ | ✅ | ✅ | ✅ |

### Rule of Thumb
```
Fields    → always private
Constructors → usually public
Methods (utility) → private
Methods (API) → public
```

---

## 📌 4. Encapsulation (Full Template)

### Core Intuition
> Lock your data inside. Provide controlled doorways (getters/setters).

### ✅ Full Encapsulation Template
```java
public class BankAccount {
    // Step 1: Make fields PRIVATE
    private String owner;
    private double balance;

    // Step 2: Constructor
    public BankAccount(String owner, double initialBalance) {
        this.owner = owner;
        if (initialBalance < 0) throw new IllegalArgumentException("Balance cannot be negative");
        this.balance = initialBalance;
    }

    // Step 3: Getter (read-only access)
    public double getBalance() { return balance; }
    public String getOwner() { return owner; }

    // Step 4: NO setter for balance — only controlled methods
    public void deposit(double amount) {
        if (amount <= 0) throw new IllegalArgumentException("Invalid amount");
        balance += amount;
    }

    public boolean withdraw(double amount) {
        if (amount > balance) return false; // guard condition
        balance -= amount;
        return true;
    }

    @Override
    public String toString() {
        return "BankAccount{owner=" + owner + ", balance=" + balance + "}";
    }
}
```

### Immutable Class Template (Bonus — Senior Level)
```java
public final class ImmutablePoint {   // final = can't be subclassed
    private final int x;              // final = can't be changed
    private final int y;

    public ImmutablePoint(int x, int y) {
        this.x = x;
        this.y = y;
    }

    public int getX() { return x; }
    public int getY() { return y; }

    // No setters! Returns new object instead
    public ImmutablePoint translate(int dx, int dy) {
        return new ImmutablePoint(x + dx, y + dy);
    }
}
```

---

## 📌 5. `this` vs `static` — The Classic Confusion

```java
public class Counter {
    private int count;           // instance — each object has its own
    private static int total;    // static — shared by ALL objects

    public Counter() {
        count = 0;
        total++;                 // every new counter increases total
    }

    public void increment() {
        this.count++;            // 'this' = this specific counter object
    }

    public static int getTotal() {
        // return this.count; ← ERROR! 'this' not available in static
        return total;            // ← correct
    }
}
```

---

## 🧠 Phase 1 — Pattern Recognition Flowchart

```
I need to model something in code
         ↓
Does it have STATE (data) + BEHAVIOR (actions)?
         ↓ YES
Create a CLASS
         ↓
Should the data be changeable from outside?
         ↓ NO → make field private + add getters only
         ↓ YES → make field private + add getter + setter with validation
         ↓
Does object need initial data to exist?
         ↓ YES → Parameterized Constructor
         ↓ NO → Default Constructor
         ↓
Can objects be built in multiple ways?
         ↓ YES → Constructor Overloading
```

---

## ⚠️ Common Mistakes in Phase 1

| Mistake | Why Wrong | Fix |
|---------|-----------|-----|
| `public int balance` | Anyone can set `obj.balance = -999` | Make `private`, add methods |
| No `this.` in constructor | `name = name` → does nothing | `this.name = name` |
| Calling instance method in static | `static void m() { getBalance(); }` | Pass object as parameter |
| Forgetting `new` | `Student s; s.getName();` → NPE | `Student s = new Student();` |
| No `toString()` | `System.out.println(obj)` prints memory address | Override `toString()` |

---

## ✅ Phase 1 Completion Checklist
- [x] Can write a class from scratch with fields, constructors, methods
- [x] Can explain the difference between instance and static members
- [x] Can implement full encapsulation with private fields + public methods
- [x] Can use `this` keyword correctly in all contexts
- [x] Can write overloaded constructors with constructor chaining
- [x] Can write an immutable class
- [x] Can identify which access modifier to use in any situation

---
*Next: [[04_Phase2_Pattern_Mastery]]*
