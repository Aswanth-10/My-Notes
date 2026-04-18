# 🎯 Practice Problem Map — Curated by Pattern & Difficulty
#practice #problems #coding #java #oop
← [[07_Daily_Execution_Plan]] | [[09_Common_Mistakes_Debugging]] →

---

## 🟢 Phase 1 Problems — Foundation

### Group 1: Classes & Objects
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 1 | Build a `Student` class with name, rollNo, marks. Print report card. | 🟢 Easy | Your first class — foundation of everything |
| 2 | Build a `Rectangle` class with area() and perimeter() | 🟢 Easy | Methods that use fields |
| 3 | Build a `Car` class with make, model, speed. Add accelerate() and brake() | 🟢 Easy | State changes via methods |
| 4 | Build a `BankAccount` with deposit, withdraw, getBalance (validation!) | 🟡 Medium | Encapsulation in action |
| 5 | Build a `Counter` with both instance count and static total count | 🟡 Medium | Instance vs Static mastery |
| 6 | Build an immutable `Point` class — no setters, translate() returns new Point | 🔴 Hard | Immutability pattern |

### Group 2: Constructors
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 7 | Create `Pizza` with 5 different constructors (name only, name+size, etc.) | 🟢 Easy | Overloading practice |
| 8 | Chain constructors in `Employee` — all delegate to full constructor | 🟡 Medium | `this()` chaining pattern |
| 9 | Build a `Date` class. Validate in constructor (1–31, 1–12, year > 0) | 🟡 Medium | Constructor with validation |
| 10 | Create `Matrix` class with copy constructor | 🔴 Hard | Deep copy understanding |

---

## 🔵 Phase 2 Problems — Inheritance & Polymorphism

### Group 3: Inheritance
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 11 | `Animal → Dog → GoldenRetriever` — 3 levels | 🟢 Easy | Multilevel inheritance |
| 12 | `Vehicle → Car, Bike, Truck` — each with unique attributes | 🟢 Easy | Hierarchical inheritance |
| 13 | Override `toString()` in every class — include parent fields via super | 🟡 Medium | super.toString() pattern |
| 14 | `Employee → Manager → Director` — each overrides `calculateSalary()` | 🟡 Medium | Override with different logic |
| 15 | Prevent `BankAccount` from being subclassed (final) | 🟢 Easy | `final` keyword usage |

### Group 4: Polymorphism
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 16 | `List<Shape>` with Circle, Rectangle, Triangle — print areas | 🟡 Medium | Polymorphic collections |
| 17 | Safe downcast: from `Animal` ref, downcast only if Dog | 🟡 Medium | instanceof + cast pattern |
| 18 | Design `Notification` system — push(), email(), sms() as subclasses | 🟡 Medium | Strategy via Polymorphism |
| 19 | `Calculator` with 6 overloaded `calculate()` methods | 🟢 Easy | Overloading all variations |
| 20 | `PaymentProcessor` — CreditCard, UPI, Cash all implement `pay()` | 🔴 Hard | Real-world polymorphism |

### Group 5: Abstract + Interface
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 21 | Abstract `Shape` → Circle, Rect, Triangle with area() + perimeter() | 🟡 Medium | Template Method pattern |
| 22 | `Flyable` + `Swimmable` → Duck, FlyingFish, Penguin | 🟡 Medium | Multiple interfaces |
| 23 | Design `DatabaseConnector` as abstract with connect() abstract | 🔴 Hard | DIP preview |
| 24 | `Comparable<Student>` — sort by GPA, then by name | 🟡 Medium | Comparable implementation |
| 25 | Create `Printable`, `Saveable`, `Loadable` interfaces for `Document` | 🔴 Hard | ISP practice |

---

## 🔴 Phase 3 Problems — Advanced

### Group 6: Generics
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 26 | Generic `Pair<K, V>` class with swap() | 🟡 Medium | Generic class fundamentals |
| 27 | Generic `Stack<T>` with push, pop, peek, isEmpty | 🟡 Medium | Generics with data structures |
| 28 | Generic `findMin(List<T extends Comparable<T>>)` method | 🔴 Hard | Bounded type parameters |
| 29 | Generic `Repository<T>` with save, findById, findAll, delete | 🔴 Hard | Real-world generic pattern |

### Group 7: Collections
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 30 | Word frequency counter using `HashMap<String, Integer>` | 🟡 Medium | Map usage |
| 31 | Student grade manager — sort by GPA 3 ways using Comparator | 🟡 Medium | Comparator chaining |
| 32 | Remove duplicates from list using Set, preserve order | 🟡 Medium | Set + LinkedHashSet |
| 33 | Phonebook: `Map<String, List<String>>` — one person, multiple phones | 🔴 Hard | Nested collections |
| 34 | Implement a simple `LRU Cache` using LinkedHashMap | 🔴 Hard | Advanced Map usage |

### Group 8: SOLID + Design Patterns
| # | Problem | Difficulty | Why Important |
|---|---------|-----------|--------------|
| 35 | Singleton `Logger` class — log to file | 🟡 Medium | Singleton pattern |
| 36 | `ShapeFactory` — create any shape by string type | 🟡 Medium | Factory pattern |
| 37 | `PersonBuilder` — build Person step by step | 🟡 Medium | Builder pattern |
| 38 | `EventBus` — publish/subscribe notification system | 🔴 Hard | Observer pattern |
| 39 | `SortContext` with pluggable strategy | 🔴 Hard | Strategy pattern |
| 40 | Refactor a bad `OrderProcessor` to follow all 5 SOLID rules | 🔴 Hard | SOLID in practice |

---

## 🏆 Capstone Problems (Interview Level)
| # | Problem | Difficulty |
|---|---------|-----------|
| 41 | Design a Parking Lot system (OOP design) | 🔴 Hard |
| 42 | Design a Chess game class hierarchy | 🔴 Hard |
| 43 | Implement a mini ATM machine | 🔴 Hard |
| 44 | Design a Food Delivery system (Restaurant, Order, Delivery) | 🔴 Hard |
| 45 | Design a Social Media post/comment/like system | 🔴 Hard |

---

## 📊 Problem Completion Tracker

### Phase 1 (10 problems)
- [ ] P1 [ ] P2 [ ] P3 [ ] P4 [ ] P5 [ ] P6 [ ] P7 [ ] P8 [ ] P9 [ ] P10

### Phase 2 (15 problems)
- [ ] P11 [ ] P12 [ ] P13 [ ] P14 [ ] P15 [ ] P16 [ ] P17 [ ] P18 [ ] P19 [ ] P20
- [ ] P21 [ ] P22 [ ] P23 [ ] P24 [ ] P25

### Phase 3 (15 problems)
- [ ] P26 [ ] P27 [ ] P28 [ ] P29 [ ] P30 [ ] P31 [ ] P32 [ ] P33 [ ] P34 [ ] P35
- [ ] P36 [ ] P37 [ ] P38 [ ] P39 [ ] P40

### Capstone (5 problems)
- [ ] P41 [ ] P42 [ ] P43 [ ] P44 [ ] P45

---

## 💡 How to Practice Each Problem
```
Step 1: Read problem → identify which OOP concept(s) apply
Step 2: Draw UML / sketch class hierarchy on paper
Step 3: Write code WITHOUT looking at templates
Step 4: Test with edge cases (null, negative, empty)
Step 5: Compare with template → note differences
Step 6: Refactor to be cleaner
Step 7: Add to your notes what you learned
```
