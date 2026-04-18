# 🏆 Milestones & Master Checklist
#milestones #checklist #progress #mastery
← [[10_Revision_Retention_System]] | [[12_Real_World_Project]] →

---

## 🎯 Milestone 1: Phase 1 Complete (End of Week 3)

### Definition of Done:
> Can build a complete, working Java class system from scratch in under 30 minutes

### Checkpoint Tasks:
- [ ] Build `BankAccount` with full encapsulation (no notes)
- [ ] Build `Employee` hierarchy (3 levels) with overriding toString
- [ ] Explain to yourself: what is the difference between a class and object?
- [ ] Write a constructor chain from memory

### Skills Verified:
- [ ] Create classes with proper fields, constructors, methods
- [ ] Apply all 4 access modifiers correctly
- [ ] Use `this` and `super` without confusion
- [ ] Write fully encapsulated class with validation
- [ ] Distinguish static vs instance members instantly

**🏁 Milestone 1 Achieved on:** ________

---

## 🎯 Milestone 2: Phase 2 Complete (End of Week 6)

### Definition of Done:
> Can design an inheritance hierarchy with polymorphism + interfaces in 45 minutes

### Checkpoint Tasks:
- [ ] Design a `Shape` system: abstract class + 3 concrete shapes + polymorphic list
- [ ] Implement `Flyable` + `Swimmable` on `Duck` with multiple interfaces
- [ ] Explain: overloading vs overriding (without notes, in 60 seconds)
- [ ] Safe downcast with instanceof in 5 lines
- [ ] Design a custom `InsufficientFundsException` and use it

### Skills Verified:
- [ ] Write inheritance chain with `super()` correctly
- [ ] Override methods with `@Override`, call `super.method()` when needed
- [ ] Explain runtime polymorphism with upcasting
- [ ] Choose between abstract class vs interface for any scenario
- [ ] Implement multiple interfaces on one class
- [ ] Write and throw custom exceptions

**🏁 Milestone 2 Achieved on:** ________

---

## 🎯 Milestone 3: Phase 3 Complete (End of Week 9)

### Definition of Done:
> Can design any OOP system using SOLID principles and design patterns

### Checkpoint Tasks:
- [ ] Write a `Singleton Logger` from memory
- [ ] Write a `Builder` for a complex class from memory
- [ ] Implement `Observer` for an event system
- [ ] Identify all 5 SOLID violations in a given code snippet
- [ ] Write a `Generic<T extends Comparable<T>>` method
- [ ] Sort a collection 3 ways using Comparator

### Skills Verified:
- [ ] Explain all 5 SOLID principles with real examples
- [ ] Implement Singleton, Factory, Builder patterns correctly
- [ ] Implement Observer and Strategy patterns
- [ ] Write generic classes + methods with bounded parameters
- [ ] Choose the right Collection for any scenario
- [ ] Override equals() + hashCode() together

**🏁 Milestone 3 Achieved on:** ________

---

## 🎯 Milestone 4: Real-World Mastery (End of Week 10)

### Definition of Done:
> Built a complete Library Management System using ALL OOP concepts

### Checkpoint Tasks:
- [ ] Completed Library System project (see [[12_Real_World_Project]])
- [ ] Applied at least 3 design patterns in the project
- [ ] All SOLID principles followed
- [ ] No public fields in any class
- [ ] All edge cases handled with exceptions
- [ ] Can explain every design decision you made

**🏁 Milestone 4 Achieved on:** ________

---

## ✅ COMPLETE MASTER CHECKLIST

### 🟢 Phase 1: Foundation
- [ ] **Classes & Objects**: Can write class from scratch. Knows class vs object.
- [ ] **Fields**: Knows instance vs static. Uses appropriately.
- [ ] **Methods**: Can write instance + static methods. Understands void vs return.
- [ ] **this keyword**: Uses in constructor, setter, method chaining.
- [ ] **Constructors**: Default, parameterized, overloaded, chained (this()), copy constructor.
- [ ] **Access Modifiers**: private, default, protected, public — knows when to use each.
- [ ] **Encapsulation**: Private fields, getters/setters with validation, immutable class.
- [ ] **Static members**: Knows shared state use case. Never calls instance from static.
- [ ] **toString()**: Always overrides. Meaningful output.
- [ ] **equals() + hashCode()**: Overrides BOTH. Uses Objects.hash().

### 🔵 Phase 2: Pattern Mastery
- [ ] **Inheritance (extends)**: Multi-level and hierarchical. Always `super()` first.
- [ ] **super keyword**: In constructor AND method. Knows the difference.
- [ ] **Method Overriding**: @Override always. Covariant return type.
- [ ] **Method Overloading**: Different parameters. Compile-time resolution.
- [ ] **Polymorphism (runtime)**: Upcasting automatic. Downcasting with instanceof.
- [ ] **Dynamic Dispatch**: JVM picks method at runtime based on actual object type.
- [ ] **Abstract Classes**: abstract keyword. Must override abstract methods. Cannot instantiate.
- [ ] **Interfaces**: interface keyword. implements. Multiple interfaces. default/static methods.
- [ ] **Abstract vs Interface**: Can justify choice for any scenario instantly.
- [ ] **final keyword**: final class (no extend), final method (no override), final field (immutable).
- [ ] **Object class**: Know toString(), equals(), hashCode() come from Object.
- [ ] **Exception Handling**: try-catch-finally. throw/throws. Custom exceptions.
- [ ] **Exception Hierarchy**: Checked vs Unchecked. When to use each.
- [ ] **Packages**: Creating packages. import statement. Access across packages.

### 🔴 Phase 3: Advanced
- [ ] **Generics — Classes**: `class Box<T>`. Type safety.
- [ ] **Generics — Methods**: `<T> T method(T param)`. Generic methods.
- [ ] **Bounded Types**: `<T extends Number>`. Upper bound.
- [ ] **Wildcards**: `<?>`, `<? extends T>`, `<? super T>`. When each is needed.
- [ ] **ArrayList vs LinkedList**: Access vs insertion trade-off.
- [ ] **HashSet vs TreeSet vs LinkedHashSet**: When uniqueness + ordering matter.
- [ ] **HashMap vs TreeMap vs LinkedHashMap**: Fast lookup vs sorted vs ordered.
- [ ] **Comparable**: Natural ordering inside class.
- [ ] **Comparator**: External, flexible, chainable sorting.
- [ ] **Iterator pattern**: For-each on custom collections.
- [ ] **SOLID — S**: One reason to change.
- [ ] **SOLID — O**: Extend without modifying.
- [ ] **SOLID — L**: Subclass substitutable for parent.
- [ ] **SOLID — I**: No unnecessary interface methods.
- [ ] **SOLID — D**: Depend on abstractions.
- [ ] **Singleton pattern**: Private constructor, static instance, getInstance().
- [ ] **Factory pattern**: Static method returns subclass instance by type string.
- [ ] **Builder pattern**: Static inner Builder class, method chaining, build().
- [ ] **Observer pattern**: Subject + Observer interface + notify all.
- [ ] **Strategy pattern**: Context + Strategy interface + runtime swap.
- [ ] **Composition vs Inheritance**: HAS-A vs IS-A. Prefer composition for reuse.
- [ ] **Dependency Injection**: Pass dependencies via constructor. Depend on interfaces.
- [ ] **Nested/Inner classes**: Static nested vs non-static inner. When to use.
- [ ] **Enums**: enum with fields/methods. Enum in switch.
- [ ] **Lambdas (Java 8+)**: Basic lambda syntax. Functional interfaces.

### 🏆 Real-World
- [ ] **Library Management System**: Full project built with all concepts
- [ ] **Code Review**: Can identify OOP violations in others' code
- [ ] **Design Interview**: Can design any medium system using UML + OOP in 30 min
- [ ] **Teach**: Can explain any concept to a fellow beginner clearly

---

## 📊 Overall Progress

| Phase | Topics Total | Topics Done | % Complete |
|-------|-------------|-------------|-----------|
| Phase 1 Foundation | 10 | | |
| Phase 2 Pattern Mastery | 14 | | |
| Phase 3 Advanced | 21 | | |
| Real-World | 4 | | |
| **TOTAL** | **49** | | |
