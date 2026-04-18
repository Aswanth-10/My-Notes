# 🏗️ Real-World Project — Library Management System
#project #real-world #java #oop #capstone
← [[11_Milestones_Checklist]] | [[00_MOC_OOP_Java_Mastery]] →

---

## 📦 Project Overview

**Name:** Library Management System (LMS)
**Goal:** Apply EVERY OOP concept learned in a real, working Java project
**Duration:** 1 week (Week 9–10)
**Complexity:** Medium → Advanced

---

## 🎯 What This Project Covers

| Concept | Where Used |
|---------|-----------|
| Classes & Objects | Book, Member, Library, Librarian |
| Encapsulation | All private fields, controlled access |
| Inheritance | PhysicalBook extends Book, EBook extends Book |
| Polymorphism | List<Book>, all books can display() |
| Abstract Class | Book (abstract) — can't borrow an "abstract book" |
| Interface | Searchable, Printable, Notifiable |
| Custom Exceptions | BookNotFoundException, MemberLimitException |
| Generics | Repository<T> for storing any entity |
| Collections | HashMap for catalog, List for borrowed books |
| SOLID Principles | Separate concerns, DI for notifications |
| Design Patterns | Singleton (Library), Observer (notifications), Builder (Member) |

---

## 📐 Class Design (UML)

```
                    ┌─────────────────┐
                    │   «abstract»    │
                    │     Book        │
                    │─────────────────│
                    │ -id: String     │
                    │ -title: String  │
                    │ -author: String │
                    │ -isAvailable    │
                    │─────────────────│
                    │ +display()      │
                    │ +abstract checkout() │
                    └────────┬────────┘
                             │ extends
              ┌──────────────┼──────────────┐
              │                             │
    ┌─────────┴────────┐        ┌───────────┴──────┐
    │  PhysicalBook    │        │     EBook        │
    │──────────────────│        │──────────────────│
    │ -shelfLocation   │        │ -fileSize (MB)   │
    │ -condition       │        │ -format (PDF/ePub)│
    │──────────────────│        │──────────────────│
    │ +checkout()      │        │ +checkout()      │
    └──────────────────┘        └──────────────────┘

    ┌──────────────────────────────────────────┐
    │               Member                     │
    │──────────────────────────────────────────│
    │ -memberId: String                        │
    │ -name: String                            │
    │ -borrowedBooks: List<Book>               │
    │ -maxBorrowLimit: int = 5                 │
    │──────────────────────────────────────────│
    │ +borrowBook(Book)                        │
    │ +returnBook(Book)                        │
    │ +getBorrowedBooks()                      │
    └──────────────────────────────────────────┘

    ┌──────────────────────────────────────────┐
    │          Library (Singleton)             │
    │──────────────────────────────────────────│
    │ -instance: Library (static)              │
    │ -catalog: Map<String, Book>              │
    │ -members: Map<String, Member>            │
    │──────────────────────────────────────────│
    │ +getInstance(): Library                  │
    │ +addBook(Book)                           │
    │ +registerMember(Member)                  │
    │ +searchByTitle(String): List<Book>       │
    │ +checkoutBook(memberId, bookId)          │
    │ +returnBook(memberId, bookId)            │
    └──────────────────────────────────────────┘
```

---

## 💻 Project Code Structure

### Step 1: Abstract Book class
```java
public abstract class Book {
    private final String id;
    private final String title;
    private final String author;
    private boolean isAvailable;

    public Book(String id, String title, String author) {
        this.id = id;
        this.title = title;
        this.author = author;
        this.isAvailable = true;
    }

    public abstract void checkout();          // each type handles differently
    public abstract String getBookType();

    public void returnBook() { isAvailable = true; }

    public String getId() { return id; }
    public String getTitle() { return title; }
    public String getAuthor() { return author; }
    public boolean isAvailable() { return isAvailable; }
    protected void setAvailable(boolean b) { isAvailable = b; }

    @Override
    public String toString() {
        return "[" + getBookType() + "] " + title + " by " + author
               + " (Available: " + isAvailable + ")";
    }
}
```

### Step 2: Concrete Book classes
```java
public class PhysicalBook extends Book {
    private String shelfLocation;
    private String condition; // "New", "Good", "Worn"

    public PhysicalBook(String id, String title, String author, String shelf) {
        super(id, title, author);
        this.shelfLocation = shelf;
        this.condition = "New";
    }

    @Override
    public void checkout() {
        if (!isAvailable()) throw new IllegalStateException("Book not available!");
        setAvailable(false);
        System.out.println("Physical book checked out from shelf: " + shelfLocation);
    }

    @Override public String getBookType() { return "Physical"; }
    public String getShelfLocation() { return shelfLocation; }
}

public class EBook extends Book {
    private double fileSizeMB;
    private String format; // "PDF", "ePub", "MOBI"

    public EBook(String id, String title, String author, double fileSizeMB, String format) {
        super(id, title, author);
        this.fileSizeMB = fileSizeMB;
        this.format = format;
    }

    @Override
    public void checkout() {
        // EBooks can be borrowed by multiple people
        System.out.println("EBook (" + format + ") sent to device. Size: " + fileSizeMB + " MB");
    }

    @Override public String getBookType() { return "EBook"; }
}
```

### Step 3: Member with Builder Pattern
```java
public class Member {
    private final String memberId;
    private final String name;
    private final String email;
    private final int maxBorrowLimit;
    private List<Book> borrowedBooks;

    private Member(Builder builder) {
        this.memberId = builder.memberId;
        this.name = builder.name;
        this.email = builder.email;
        this.maxBorrowLimit = builder.maxBorrowLimit;
        this.borrowedBooks = new ArrayList<>();
    }

    public void borrowBook(Book book) throws Exception {
        if (borrowedBooks.size() >= maxBorrowLimit) {
            throw new MemberLimitException(name + " has reached borrow limit of " + maxBorrowLimit);
        }
        if (!book.isAvailable()) {
            throw new BookNotAvailableException("Book '" + book.getTitle() + "' is not available.");
        }
        book.checkout();
        borrowedBooks.add(book);
    }

    public void returnBook(Book book) {
        if (borrowedBooks.remove(book)) {
            book.returnBook();
            System.out.println(name + " returned: " + book.getTitle());
        }
    }

    public List<Book> getBorrowedBooks() { return Collections.unmodifiableList(borrowedBooks); }
    public String getMemberId() { return memberId; }
    public String getName() { return name; }

    // BUILDER
    public static class Builder {
        private final String memberId;
        private final String name;
        private String email = "";
        private int maxBorrowLimit = 5;

        public Builder(String memberId, String name) {
            this.memberId = memberId;
            this.name = name;
        }
        public Builder email(String e) { this.email = e; return this; }
        public Builder maxBorrowLimit(int limit) { this.maxBorrowLimit = limit; return this; }
        public Member build() { return new Member(this); }
    }
}
```

### Step 4: Custom Exceptions
```java
public class BookNotAvailableException extends Exception {
    public BookNotAvailableException(String msg) { super(msg); }
}

public class MemberLimitException extends Exception {
    public MemberLimitException(String msg) { super(msg); }
}

public class BookNotFoundException extends RuntimeException {
    public BookNotFoundException(String bookId) {
        super("Book not found with ID: " + bookId);
    }
}
```

### Step 5: Library Singleton
```java
public class Library {
    private static Library instance;
    private final Map<String, Book> catalog = new HashMap<>();
    private final Map<String, Member> members = new HashMap<>();
    private final List<LibraryObserver> observers = new ArrayList<>();

    private Library() { }

    public static Library getInstance() {
        if (instance == null) instance = new Library();
        return instance;
    }

    public void addBook(Book book) {
        catalog.put(book.getId(), book);
        notifyObservers("New book added: " + book.getTitle());
    }

    public void registerMember(Member member) {
        members.put(member.getMemberId(), member);
    }

    public List<Book> searchByTitle(String query) {
        return catalog.values().stream()
            .filter(b -> b.getTitle().toLowerCase().contains(query.toLowerCase()))
            .collect(Collectors.toList());
    }

    public void checkoutBook(String memberId, String bookId) throws Exception {
        Member member = members.get(memberId);
        Book book = catalog.get(bookId);
        if (book == null) throw new BookNotFoundException(bookId);
        member.borrowBook(book);
    }

    // Observer pattern
    public void subscribe(LibraryObserver o) { observers.add(o); }
    private void notifyObservers(String event) {
        observers.forEach(o -> o.onLibraryEvent(event));
    }

    public void printCatalog() {
        System.out.println("\n=== LIBRARY CATALOG ===");
        catalog.values().forEach(System.out::println);
    }
}
```

### Step 6: Observer Interface
```java
public interface LibraryObserver {
    void onLibraryEvent(String event);
}

public class EmailNotifier implements LibraryObserver {
    private String adminEmail;
    public EmailNotifier(String email) { this.adminEmail = email; }
    public void onLibraryEvent(String event) {
        System.out.println("[EMAIL to " + adminEmail + "] " + event);
    }
}
```

### Step 7: Main class
```java
public class Main {
    public static void main(String[] args) {
        Library library = Library.getInstance();

        // Subscribe observer
        library.subscribe(new EmailNotifier("admin@library.com"));

        // Add books
        library.addBook(new PhysicalBook("B001", "Clean Code", "Robert Martin", "A-12"));
        library.addBook(new PhysicalBook("B002", "Effective Java", "Joshua Bloch", "B-05"));
        library.addBook(new EBook("E001", "Java 17 Guide", "Oracle", 12.5, "PDF"));

        // Register members
        Member alice = new Member.Builder("M001", "Alice")
            .email("alice@example.com")
            .maxBorrowLimit(3)
            .build();
        library.registerMember(alice);

        // Checkout
        try {
            library.checkoutBook("M001", "B001");
            library.checkoutBook("M001", "E001");
        } catch (Exception e) {
            System.out.println("Error: " + e.getMessage());
        }

        // Print
        library.printCatalog();
        System.out.println("\nAlice borrowed: " + alice.getBorrowedBooks().size() + " books");
    }
}
```

---

## 📋 Project Completion Checklist
- [ ] All classes designed with proper encapsulation
- [ ] Abstract Book class with 2 concrete implementations
- [ ] Member class using Builder pattern
- [ ] Library using Singleton pattern
- [ ] Observer pattern for notifications
- [ ] Custom exceptions thrown and caught
- [ ] Generic Repository<T> added for stretch goal
- [ ] Search functionality using Collections/Streams
- [ ] All SOLID principles applied
- [ ] README written explaining design decisions
- [ ] Code compiles and runs without errors

---

## 🚀 Extension Challenges
1. Add a `Reservation` system (reserve books that are checked out)
2. Add a `FineCalculator` for overdue books (Strategy pattern)
3. Add `CSVExporter` and `JSONExporter` for reports (Strategy + OCP)
4. Add `BookGenre` enum and filter by genre
5. Make the system multi-threaded safe (synchronized Singleton)
