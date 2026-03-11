## Three Layers
1. Presentation Layer 
2. Service Layer. (inbetween layer, connects presentation layer (TodoController) and persistance layer (TodoRepository), collects data from db and makes logic for the output,  (TodoService))
3. Persistance Layer  ( connects  relationship with data base,  (TodoRepository) )
###  Auto wiring and Bean Concepts
def : ____________________
1. Bean   (Managed by Spring)
   -  @Service  (TodoService)
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