# 🔁 Revision & Retention System — Spaced Repetition Plan
#revision #retention #spaced-repetition #memory
← [[09_Common_Mistakes_Debugging]] | [[11_Milestones_Checklist]] →

---

## 🧠 The Core Retention Strategy

> **Learn → Apply → Recall → Space → Recall again.**
> Never re-read passively. Always **reconstruct from memory** first.

### The Golden Rule
```
DAY 1: Learn concept
DAY 2: Recall without looking (write from memory)
DAY 4: Recall again
DAY 7: Recall again
DAY 14: Recall again
DAY 30: Final consolidation
```

---

## 📅 Weekly Revision Structure

### Every Day (15 min):
- [ ] Recall yesterday's concept: write the template from scratch
- [ ] Quick-check: can you explain it in one sentence?

### Every Sunday (2 hrs):
- [ ] Recode all topics from the current week — NO LOOKING
- [ ] Update completion checklists
- [ ] Attempt 3 problems mixing concepts from the week

### Monthly Review (Half day):
- [ ] Write complete class from scratch for each Phase completed
- [ ] Do one capstone problem from [[08_Practice_Problem_Map]]
- [ ] Review [[09_Common_Mistakes_Debugging]] — add new ones

---

## 🗂️ Flashcard System (Anki-Style)

> Create these flashcards in Obsidian or Anki app.

### Phase 1 Flashcards
```
Q: What is a class vs object?
A: Class = blueprint; Object = instance built from blueprint

Q: What does `private` do?
A: Field/method only accessible within the same class

Q: What is `this` keyword?
A: Reference to the current object instance

Q: What does `super()` do in a constructor?
A: Calls the parent class constructor; must be first line

Q: What is encapsulation?
A: Bundling data (private) + methods (public) in one class, hiding implementation

Q: When should you use `static`?
A: When something belongs to the CLASS, not individual objects (shared state, utility methods)
```

### Phase 2 Flashcards
```
Q: Difference between overloading and overriding?
A: Overloading = same name, different params, same class, compile-time
   Overriding = same name+params, child class, runtime

Q: What is upcasting?
A: Assigning subclass object to parent reference (automatic, safe)

Q: What is downcasting?
A: Casting parent reference back to subclass (manual, use instanceof)

Q: When use abstract class vs interface?
A: Abstract class: shared code + IS-A relationship
   Interface: contract + CAN-DO capability + multiple inheritance

Q: What is dynamic method dispatch?
A: JVM decides at runtime which version of overridden method to call

Q: What is LSP?
A: Subclass must be substitutable for parent without breaking functionality
```

### Phase 3 Flashcards
```
Q: What is SOLID?
A: S=Single Responsibility, O=Open/Closed, L=Liskov, I=Interface Segregation, D=Dependency Inversion

Q: When to use Singleton?
A: When only ONE instance should ever exist (DB connection, Logger, Config)

Q: When to use Builder?
A: When object has many optional parameters / complex construction

Q: When to use Observer?
A: When multiple objects need to react to changes in one object

Q: When to use Strategy?
A: When you need to swap algorithms/behaviors at runtime

Q: `List<?> vs List<T>`?
A: `?` = wildcard (unknown type, mostly read-only), `T` = defined type parameter
```

---

## 📊 Pattern Recognition Drills

> Do these drills every 3 days (10 min each):

### Drill 1: "What concept is this?"
```
Given code snippet → identify OOP concept used
1. Show code with private fields + getters → "Encapsulation"
2. Show child.method() calling parent logic → "super keyword"
3. Show Animal a = new Dog() → "Upcasting / Polymorphism"
4. Show abstract class → "Abstract class / Template Method"
5. Show new Entity.Builder().field().build() → "Builder Pattern"
```

### Drill 2: "What's wrong with this code?"
> Each Sunday, look at 5 broken code snippets from [[09_Common_Mistakes_Debugging]]
> Identify the bug → fix it → explain WHY it was wrong

### Drill 3: "Design from scratch"
> Given a scenario, draw UML class diagram in 10 min:
- "Design a school system" → School, Department, Teacher, Student
- "Design a zoo" → Animal, Habitat, Keeper
- "Design a music player" → Song, Playlist, Player

---

## 📋 Long-Term Retention Plan

| Milestone | Action |
|-----------|--------|
| End of Week 1 | Recode all Phase 1 classes from memory |
| End of Week 3 | Build mini Zoo project using ALL Phase 1+2 concepts |
| End of Week 6 | Refactor Zoo project to use SOLID principles |
| End of Week 9 | Build full Library System from scratch |
| Month 3 | Solve 3 capstone design problems |
| Month 4+ | Teach someone else (best retention method!) |

---

## 🧪 Self-Test Protocol

### After Learning Each Topic:
```
Test 1 (Immediate): Close notes. Write the template from memory.
Test 2 (Next Day): Explain the concept to yourself out loud in simple words.
Test 3 (Week Later): Apply the concept in a NEW problem you haven't seen before.
```

### Green/Yellow/Red Rating System:
- 🟢 **Green**: Can write template + explain without any help → Move on
- 🟡 **Yellow**: Can write with minor prompting → Review once more
- 🔴 **Red**: Struggling → Revisit concept, try different analogy, practice more

---

## 🗃️ Topic Status Tracker

| Topic | Learned | Recalled D+1 | Recalled D+7 | Recalled D+30 | Status |
|-------|---------|-------------|--------------|---------------|--------|
| Classes & Objects | | | | | 🔴 |
| Constructors | | | | | 🔴 |
| Encapsulation | | | | | 🔴 |
| Inheritance | | | | | 🔴 |
| Polymorphism | | | | | 🔴 |
| Abstract Classes | | | | | 🔴 |
| Interfaces | | | | | 🔴 |
| Generics | | | | | 🔴 |
| Collections | | | | | 🔴 |
| SOLID | | | | | 🔴 |
| Design Patterns | | | | | 🔴 |

> Update dates and change 🔴→🟡→🟢 as you master each topic
