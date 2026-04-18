# 📅 Daily Execution Plan — 4 Hours/Day
#daily #schedule #execution #plan
← [[06_Templates_and_Patterns]] | [[08_Practice_Problem_Map]] →

---

## ⏰ Daily 4-Hour Block Structure

| Time Block | Duration | Activity |
|-----------|----------|----------|
| Block 1 | 60 min | 📖 **Learn** — New concept (read + understand) |
| Block 2 | 90 min | 💻 **Code** — Write templates + practice problems |
| Block 3 | 45 min | 🧠 **Review** — Flashcards + pattern recognition |
| Block 4 | 45 min | 🔁 **Revision** — Yesterday's topic + spaced reps |

> 💡 **Rule:** Never move to Block 2 without understanding Block 1 first.

---

## 📆 Phase 1 Weekly Plan (Weeks 1–3)

### Week 1: Classes, Objects, Constructors

| Day | Topic | Practice Task | Expected Output |
|-----|-------|--------------|----------------|
| Mon | Java Setup + JVM + first class | Write `Student` class from scratch | Student object prints info |
| Tue | Fields, Methods, `this` | Add 5 methods to Student | Working Student with all methods |
| Wed | Constructors (all types) | Build `Car` class with 4 constructor types | All constructors work |
| Thu | Access Modifiers | Refactor Student to use private fields | Data protected, methods work |
| Fri | Encapsulation + Getters/Setters | Build `BankAccount` with full encapsulation | Deposit/Withdraw with validation |
| Sat | Static vs Instance | Build `Counter` class | Track total vs individual counts |
| Sun | **REVISION DAY** | Re-code everything from memory | All 3 classes without looking |

### Week 2: Inheritance + Polymorphism

| Day | Topic | Practice Task | Expected Output |
|-----|-------|--------------|----------------|
| Mon | Inheritance basics + `extends` | Animal → Dog → GoldenRetriever | 3-level inheritance chain |
| Tue | `super` keyword | Override `eat()` in Dog, call `super.eat()` | Both behaviors visible |
| Wed | Method Overriding + `@Override` | Override `toString()` in every class | Meaningful print output |
| Thu | Polymorphism — upcasting | `List<Animal>` with Dog, Cat, Bird | Each speaks differently |
| Fri | Downcasting + `instanceof` | Safe casting with instanceof checks | No ClassCastException |
| Sat | Method Overloading | Calculator with 4 overloaded `add()` | Works for int, double, 3 params |
| Sun | **REVISION DAY** | Draw UML of Animal hierarchy | Can explain all relationships |

### Week 3: Abstract + Interface + Exceptions

| Day | Topic | Practice Task | Expected Output |
|-----|-------|--------------|----------------|
| Mon | Abstract classes | Shape → Circle, Rectangle, Triangle | area() works for all |
| Tue | Interfaces — basics | `Flyable`, `Swimmable` → Duck | Duck can fly and swim |
| Wed | Multiple interfaces | `Serializable`, `Comparable` on Student | Student sortable by age |
| Thu | Abstract vs Interface | Design a Vehicle system | Mixed use of both |
| Fri | Custom Exceptions | `InsufficientFundsException` in BankAccount | Proper throw/catch |
| Sat | Exception hierarchy | Try-with-resources, multi-catch | Clean exception code |
| Sun | **REVISION DAY** | Mini project: Zoo System | Animals, Interfaces, Exceptions |

---

## 📆 Phase 2 Weekly Plan (Weeks 4–6)

### Week 4: Generics

| Day | Topic | Practice Task |
|-----|-------|--------------|
| Mon | Generic classes | `Box<T>`, `Pair<K,V>` |
| Tue | Generic methods | `findMax(T a, T b)` |
| Wed | Bounded parameters | `NumberBox<T extends Number>` |
| Thu | Wildcards | `printList(List<?>)` |
| Fri | Generic with inheritance | `Stack<T>` implementation |
| Sat | Real use: Generic Repository | `Repository<T>` pattern |
| Sun | Revision |  |

### Week 5: Collections

| Day | Topic | Practice Task |
|-----|-------|--------------|
| Mon | ArrayList + LinkedList | Student grade manager |
| Tue | HashSet + TreeSet | Unique word counter |
| Wed | HashMap + TreeMap | Student-score lookup |
| Thu | Comparable + Comparator | Sort Students 3 different ways |
| Fri | Collections utility methods | sort, shuffle, min, max |
| Sat | Mixed collections problem | Phonebook: Map + Set + List |
| Sun | Revision |  |

### Week 6: SOLID Principles

| Day | Topic | Practice Task |
|-----|-------|--------------|
| Mon | S — Single Responsibility | Refactor bloated class |
| Tue | O — Open/Closed | Add new shape without changing calculator |
| Wed | L — Liskov Substitution | Find LSP violation, fix it |
| Thu | I — Interface Segregation | Split fat interface |
| Fri | D — Dependency Inversion | Inject database dependency |
| Sat | Apply ALL 5 to one system | Order Processing System |
| Sun | Revision |  |

---

## 📆 Phase 3 Weekly Plan (Weeks 7–9)

### Week 7–8: Design Patterns

| Day | Pattern | Build |
|-----|---------|-------|
| Mon | Singleton | Config Manager |
| Tue | Factory | Shape Factory |
| Wed | Builder | HTTP Request Builder |
| Thu | Observer | Event notification system |
| Fri | Strategy | Payment strategy (Cash/Card/UPI) |
| Sat | Decorator | Coffee shop with add-ons |
| Sun | Revision |  |

### Week 9: Real-World Project
> Build the **Library Management System** — see [[12_Real_World_Project]]

---

## 📋 Daily Habit Checklist
```
Morning Session (2 hrs):
  [ ] Read new concept in note
  [ ] Understand intuition + analogy
  [ ] Copy template from [[06_Templates_and_Patterns]]
  [ ] Write it from scratch WITHOUT looking

Evening Session (2 hrs):
  [ ] Solve 2-3 practice problems
  [ ] Review yesterday's topic (15 min)
  [ ] Update Obsidian notes with learnings
  [ ] Add new mistakes to [[09_Common_Mistakes_Debugging]]
```

---

## 🚦 Pace Adjustment Rules
- **If a topic takes 2+ days:** Don't move forward. Mastery over speed.
- **If completing topics early:** Go deeper. Add edge cases. Write more variations.
- **College exam weeks:** Reduce to 2 hours/day (1 learn + 1 practice only)
- **Stuck for >1 hour:** Write the question + attempt in notes, search Stack Overflow, move on — come back tomorrow.

---

## ⏱️ Weekly Time Budget (4 hr/day × 7 days = 28 hrs/week)

| Activity | Hours/Week |
|----------|-----------|
| Learning new content | 8 hrs |
| Coding practice | 10 hrs |
| Revision & Flashcards | 5 hrs |
| Project work | 3 hrs |
| Note updating (Obsidian) | 2 hrs |
| **Total** | **28 hrs** |
