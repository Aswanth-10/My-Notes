##  Terminal cmds:
1. while creating a java class file, use annotations (@RestController)
2. while creating call function, use annotation (@GetMapping("/path")), to store the root path (@RequestMapping("/api/v1/path")
```java
package com.aswanth.helloworld;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/todo")
public class TodoController {
	@GetMapping("/get")
	String todo(){
		return "todo";
	}
	@GetMapping("/id")
	String todobyid(){
		return "id";
	}
}
```
1. using annotation(@PathVariable)
```java
package com.aswanth.helloworld;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@RequestMapping("/api/v1/todo")
public class TodoController {
    @GetMapping("/get")
    String todo(){
        return "todo";
    }
	
	//path variable:
    @GetMapping("/{id}")
    String todobyid(@PathVariable int id){
        return "id" + id;        
    }
}

```
1. mvn spring-boot:run     (to run)
2. ./mvnw clean  (to clear targets)
3. ./mvnw compile  (to compile targets)
4. ./mvnw clean compile  (to compile the changes made)
5. ./mvnw clean test  (to clear test)
6. ./mvnw clean verify (to verify testcases)
7. after changes => cd target - java -jar "jar file name" (all the files created will be converted into a single jar file by Maven and will be stored in a server (target))
8. ./mvnw clean install. (now that jar file will be installed in the device locally for further use)
9. POM.xml (project object Model) stores all dependencies, if etra dependencies needed => in "Maven Repositories" -> get dependencies and store them (ex: lombok)
10. Request Param:
     - syntax => (path = localhost:8081/api/v1/todo?(key) = (value) & (key) = (value))



