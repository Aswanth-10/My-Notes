# ⚡ Templates & Patterns — Quick Reference Card
#template #pattern #quickref #java #oop
← [[05_Phase3_Advanced]] | [[07_Daily_Execution_Plan]] →

---

## 🃏 Template Card 1: Basic Class (Every Time)
```java
public class EntityName {
    // Fields
    private Type field1;

    // Constructor
    public EntityName(Type field1) { this.field1 = field1; }

    // Getters
    public Type getField1() { return field1; }

    // Core methods
    public void doSomething() { }

    // Always
    @Override public String toString() { return "EntityName{field1=" + field1 + "}"; }
    @Override public boolean equals(Object o) { ... }
    @Override public int hashCode() { return Objects.hash(field1); }
}
```

---

## 🃏 Template Card 2: Inheritance Chain
```java
public class Parent {
    protected Type field;
    public Parent(Type field) { this.field = field; }
    public void method() { }
}

public class Child extends Parent {
    private Type extra;
    public Child(Type field, Type extra) {
        super(field);          // ← ALWAYS FIRST
        this.extra = extra;
    }
    @Override
    public void method() {
        super.method();        // ← call parent if needed
        // child-specific logic
    }
}
```

---

## 🃏 Template Card 3: Abstract + Concrete
```java
public abstract class AbstractBase {
    public abstract ReturnType abstractMethod();  // subclass MUST implement
    public void concreteMethod() { abstractMethod(); }  // can call abstract
}

public class ConcreteImpl extends AbstractBase {
    @Override
    public ReturnType abstractMethod() { return ...; }
}
```

---

## 🃏 Template Card 4: Interface + Implementation
```java
public interface Capability {
    void doAction();
    default void defaultBehavior() { }
}

public class MyClass extends ParentClass implements Capability, AnotherInterface {
    @Override public void doAction() { }
}
```

---

## 🃏 Template Card 5: Polymorphic Collection
```java
List<ParentType> items = new ArrayList<>();
items.add(new ChildA());
items.add(new ChildB());
for (ParentType item : items) {
    item.polymorphicMethod();  // each calls its own version
}
```

---

## 🃏 Template Card 6: Builder Pattern
```java
public class Entity {
    private final String required1;
    private final String optional1;

    private Entity(Builder b) { this.required1 = b.required1; this.optional1 = b.optional1; }

    public static class Builder {
        private final String required1;
        private String optional1;

        public Builder(String required1) { this.required1 = required1; }
        public Builder optional1(String v) { this.optional1 = v; return this; }
        public Entity build() { return new Entity(this); }
    }
}
// Usage: new Entity.Builder("req").optional1("opt").build();
```

---

## 🃏 Template Card 7: Singleton
```java
public class Singleton {
    private static Singleton instance;
    private Singleton() { }
    public static Singleton getInstance() {
        if (instance == null) instance = new Singleton();
        return instance;
    }
}
```

---

## 🃏 Template Card 8: Observer
```java
interface Observer { void update(String event); }

class Subject {
    private List<Observer> observers = new ArrayList<>();
    public void subscribe(Observer o) { observers.add(o); }
    public void notify(String event) { observers.forEach(o -> o.update(event)); }
}
```

---

## 🃏 Template Card 9: Strategy
```java
interface Strategy { void execute(); }
class Context {
    private Strategy strategy;
    public Context(Strategy s) { this.strategy = s; }
    public void setStrategy(Strategy s) { this.strategy = s; }
    public void run() { strategy.execute(); }
}
```

---

## 🃏 Template Card 10: Custom Exception
```java
public class MyException extends Exception {
    public MyException(String message) { super(message); }
    public MyException(String message, Throwable cause) { super(message, cause); }
}
// Throw: throw new MyException("Something went wrong");
// Catch: catch (MyException e) { e.getMessage(); }
```

---

## 🔍 Pattern Recognition Cheat Sheet

| Situation | Pattern/Concept |
|-----------|----------------|
| Model a real thing with data + behavior | **Class** |
| Protect data from direct access | **Encapsulation** |
| Share code between related classes | **Inheritance** |
| Force subclasses to implement methods | **Abstract Class** |
| Define a capability/contract | **Interface** |
| Same method, different result by type | **Polymorphism** |
| Only one instance needed globally | **Singleton** |
| Complex object construction | **Builder** |
| Decide which class to instantiate | **Factory** |
| Notify multiple objects of changes | **Observer** |
| Swap algorithms at runtime | **Strategy** |
| Work with any type safely | **Generics** |

---

## 📊 OOP Concept Decision Flowchart

```
NEW REQUIREMENT
      ↓
Is it a THING/ENTITY? → CLASS
      ↓
Does it share IS-A with another class? → INHERITANCE
      ↓
Are some methods undefined/abstract? → ABSTRACT CLASS
      ↓
Is it a capability (CAN-DO)? → INTERFACE
      ↓
Same method, different behavior? → POLYMORPHISM
      ↓
Is data sensitive? → ENCAPSULATION
      ↓
Complex object creation? → BUILDER
      ↓
One instance ever? → SINGLETON
      ↓
Notify on change? → OBSERVER
      ↓
Swappable behavior? → STRATEGY
```
