> Codeio YT Series | Videos 1–4

---

## ⚙️ Project Structure

- **Entry Point:** `src/main/java/.../Application.java`  
  - Bootstraps the Spring Boot application and initializes the **Spring Context**.

- **POM.xml**  
  - *Project Object Model* file used by **Maven**.
  - Manages:
    - Dependencies
    - Plugins
    - Build configuration
    - Project metadata

- Additional dependencies can be added from **Maven Repository**  
  https://mvnrepository.com  
  Example: **Lombok**

- **Default Server Port:**  
  ```
  localhost:8080
  ```
  Can be changed in:

  ```
  src/main/resources/application.properties
  ```

---

# 🖥️ Maven & Spring Boot Terminal Commands

| Command | Purpose |
|---|---|
| `mvn spring-boot:run` | Runs the Spring Boot application |
| `./mvnw clean` | Deletes `/target` directory |
| `./mvnw compile` | Compiles source code |
| `./mvnw clean compile` | Cleans and recompiles project |
| `./mvnw clean test` | Cleans and runs tests |
| `./mvnw clean verify` | Runs tests and verifies project |
| `./mvnw clean install` | Builds project and installs JAR locally |

### Running Packaged JAR

```
cd target
java -jar <jar-file-name>.jar
```

Maven packages the project into a **single executable JAR** stored inside:

```
/target
```

---

# 🏷️ Core Spring Boot Annotations

| Annotation | Scope | Purpose |
|---|---|---|
| `@RestController` | Class | Marks class as a REST API controller |
| `@RequestMapping("/path")` | Class | Defines base/root path |
| `@GetMapping("/path")` | Method | Handles HTTP GET requests |
| `@PostMapping("/path")` | Method | Handles HTTP POST requests |
| `@PutMapping("/path")` | Method | Handles HTTP PUT requests |
| `@DeleteMapping("/path")` | Method | Handles HTTP DELETE requests |
| `@PathVariable` | Parameter | Extracts value from URI path |
| `@RequestParam` | Parameter | Extracts query parameter |
| `@RequestBody` | Parameter | Binds HTTP request body to a method parameter |

---

# 📁 Basic Controller Structure

```java
package com.aswanth.helloworld;

import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/todo")
public class TodoController {

    // Endpoints defined here

}
```

Base URL:

```
http://localhost:8080/api/v1/todo
```

---

# 🟢 GET — Retrieve Data

GET requests are used to **read data from the server**.

There are **three common patterns**.

---

## 1️⃣ Static Endpoint

```java
@GetMapping("/all")
String getAll() {
    return "all todos";
}
```

Example:

```
GET /api/v1/todo/all
```

---

## 2️⃣ Path Variable

Used when the value is part of the **URL path**.

```
/api/v1/todo/{id}
```

```java
@GetMapping("/{id}")
String getById(@PathVariable int id) {
    return "todo id: " + id;
}
```

Example:

```
GET /api/v1/todo/5
```

---

## 3️⃣ Request Parameter

Used for **query parameters**.

```
/api/v1/todo?todoid=5
```

```java
@GetMapping("")
String getByParam(@RequestParam("todoid") int id) {
    return "req param id: " + id;
}
```

---

### GET Summary

| Method | Example |
|---|---|
| Static Path | `/todo/all` |
| Path Variable | `/todo/5` |
| Request Param | `/todo?todoid=5` |

---

# 🟡 POST — Create Resource

POST requests are used to **create new resources**.

```java
@PostMapping("/create")
String create(@RequestBody String body) {
    return body;
}
```

Key Points:

- Data is sent in the **HTTP request body**
- Not visible in the URL
- Commonly used for:
  - User registration
  - Login
  - Form submission
  - Creating resources

Testing Tool:

**Postman**

---

# 🔵 PUT — Update Resource

PUT requests update an **existing resource**.

```java
@PutMapping("/{id}")
String update(@PathVariable int id) {
    return "Updated todo with id " + id;
}
```

Example:

```
PUT /api/v1/todo/5
```

---

# 🔴 DELETE — Remove Resource

DELETE requests remove a resource.

```java
@DeleteMapping("/{id}")
String delete(@PathVariable int id) {
    return "Deleted todo with id " + id;
}
```

Example:

```
DELETE /api/v1/todo/5
```

---

# 🧩 Full Controller Example

```java
@RestController
@RequestMapping("/api/v1/todo")
public class TodoController {

    // GET — static
    @GetMapping("/all")
    String getAll() {
        return "all todos";
    }

    // GET — path variable
    @GetMapping("/{id}")
    String getById(@PathVariable int id) {
        return "id: " + id;
    }

    // GET — request param
    @GetMapping("")
    String getByParam(@RequestParam("todoid") int id) {
        return "param id: " + id;
    }

    // POST — create
    @PostMapping("/create")
    String create(@RequestBody String body) {
        return body;
    }

    // PUT — update
    @PutMapping("/{id}")
    String update(@PathVariable int id) {
        return "Updated: " + id;
    }

    // DELETE — remove
    @DeleteMapping("/{id}")
    String delete(@PathVariable int id) {
        return "Deleted: " + id;
    }
}
```

---

# 🌐 REST Endpoint Summary

| HTTP Method | URL | Description |
|---|---|---|
| GET | `/api/v1/todo/all` | Retrieve all resources |
| GET | `/api/v1/todo/{id}` | Retrieve resource by ID |
| GET | `/api/v1/todo?todoid=3` | Retrieve via query parameter |
| POST | `/api/v1/todo/create` | Create resource |
| PUT | `/api/v1/todo/{id}` | Update resource |
| DELETE | `/api/v1/todo/{id}` | Delete resource |

---

# 🧠 Key Concept

Spring Boot simplifies backend development by providing:

- Embedded server (Tomcat)
- Dependency management via Maven
- Rapid REST API development
- Minimal configuration

---

**Tags:**  
#springboot #java #backend #restapi #maven #codeio