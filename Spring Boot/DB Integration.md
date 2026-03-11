## Three Layers
1. Presentation Layer 
2. Service Layer. (inbetween layer, connects presentation layer (TodoController) and persistance layer (TodoRepository), collects data from db and makes logic for the output,  (TodoService))
3. Persistance Layer  ( connects  relationship with data base,  (TodoRepository) )
###  Auto wiring and Bean Concepts
def : ____________________
1. Bean   (Managed by Spring)
   -  @Service  (TodoService)
   ```java
   package com.aswanth.helloworld;
	import org.springframework.beans.factory.annotation.Autowired;
	import org.springframework.stereotype.Service;
	//Been
	@Service
	public class TodoService {
	    //Autowiring
	    @Autowired
	    private TodoRepository todoRepository;
	
	    public void printTodos(){
	        System.out.println(todoRepository.getallTodos());
	    }
	}
   ```
   
   - @Component (TodoRepository)
   ```java
   package com.aswanth.helloworld;
   import org.springframework.stereotype.Component;
	@Component
	public class TodoRepository {
	    String getallTodos(){
	        return "got all todos";
	    }
	}
   ```

1. @Autowired is used to instance other class files in another class file to get the components (dependency injection)
```java
@RestController
@RequestMapping("/api/v1/todo")
public class TodoController {
    @Autowired
    private TodoService todoService;
    @GetMapping("/get")
    String todo(){
        todoService.printTodos();
        return "todo";
    }
```

- this type of spring usage for auto instantiate is known as "inversion of control"