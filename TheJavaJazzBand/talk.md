#Intro
* Lambda Expressions in Java 8
* By: Austin Russell, Aubree Lytwyn, Matthew Uhlar, Ryan Smith

#Intro to Lambdas
* Lambda also Known as closures is a new expression introduced in JDK 8 using Netbeans 7.4 IDE
* Lambda: Clear and concise way to represent a method interface using an expression
* Closures: Strictly speaking a closure is a Lambda implementation that has all free variables bound to an environment giving them a value. Lambda expressions are implemented using closures and therefore the terms are used interchangeably.

#Proposal
* Java has a form of closures: anonymous inner classes
* Reasons for proposal
    + Bulky syntax -> Addressed substantially for improvements
    + Inability to capture non-final local variables -> Allow compiler capture of effectively final local variables
    + Transparency issues surrounding the meaning of return, break, continue and ‘this’ -> Making ‘this’ lexically scoped
    + No nonlocal control flow operators -> Not Addressed
    
#Proposal
* Lambda Expressions
    + Aimed at correcting the vertical problem with API classes and anonymous inner functions
    + Disadvantages
        + Mixing structural and nominal types
        + Divergence of library styles from callback objects to function types
        + Generic types are erased, which would expose additional places where developers are exposed to erasure

#What is Lambda used for?
* Improve libraries to make iterations, filtering and data extraction easier
    + Main Example:  Collection Library
        + Concurrency features improve performance in a multicore environment
        + lambdas can be understood as a kind of anonymous method with a more compact syntax that also allows the omission of modifiers, return type, and in some cases parameter types as well.

#Lambda Type
* What is the type
    + Functional interface
    + Lambda can be used recursively, specifically static variable assignment.
#Where can you use lambda Expressions
* Any context that has a target type
    + Ex: Variable Declarations and array initializers
   ```Java
    Callable<Runnable> c = () ->
     () -> system.out.println(“hi”);};
    ```
     + The expression does not allow for ambiguity example
    ```Java
    Object o = () -> {system.out.println(“hi”);};
    Object o = (Runnable) () -> 
    {system.out.println(“hi”);};
    ```

#Scoping Rules
* Follow the same rules as method parameters for shadowing class
* Example
    + Can do:
    ```Java
    Class Bar { int i; Foo foo = i -> i*4; };
    ```
    + Can’t do:
    ``Java
         Void bar() {int i; Foo foo = i -> i *4; };
    ```
    
#Functional Interfaces previously/currently known as Single Abstract Method (SAM)
* Type can be used for a method parameter when a lambda is supplied as the argument
* One explicitly declared abstract method, can omit the name of method when you implement it
* Example 
```java
public interface Runnable { void run(); }
```

# Expression Syntax
* Lambda expressions address the bulkiness of anonymous inner classes 
* Basic syntax
    + (parameters) -> expression
    ```Java
    (int x, int y) -> x+y 
    ```

#Anonymous Inner Class (AIC)
* What is it?
    + Can be used to create a subclass of an abstract class or a concrete class
    + Can provide a concrete implementation of an interface
        + including the addition of fields
    + AIC's introduce a new scope
* When is it used?
    + An instance of an AIC can be referred to using this in it's method bodies
    + Further methods can be called on it
        + State can be mutated over time
    + Majority of the time its used to provide stateless implementations of simgle functions
* Many instances like those above can be replaced with lambdas but some cannot

# Evolution of a Lambda (Naive)

* Naive long form variation

```Java
List<T> someList = ...

class compareElements implements comparator<T> {
  @override
  Public bool compare(T elem1, T elem2) {
    return elem1.getField().compareTo(
     elem2.getField())
  }
}

Collections.sort(someList, new compareElements())
```
# Evolution of a Lambda (Final)

```Java
List<T> someList = ...


Collections.sort(someList, (T elem1, T elem2){ 
  return elem1.getField().compareTo(
   elem2.getField());})
collect.sort(someList, (T e1, T e2){ return e1.field().compareTo(e2.field());})
```
* Better, more concise. However still room for improvement
```Java
List<T> someList = ...

Collections.sort(someList, (elem1, elem2) -> 
 getField().compareTo(elem2.getField()))
```

# Runnable Lambda
* The runnable lambda expression converts five lines of code into one statement
* Anonymous runnable Ex:
```’Java
Runnable r1 = new Runnable(){
    @Override
    Public void run(){
    System.out.println(“Hello world one!”);
    }
};
```
```Java
Runnable r2 = () -> 
 System.out.println(“Hello world two!”);
```

# Comparator Lambda
* used for sorting collections
```java
collections.sort(personList, (p1, p2) -> 
 p2.getSurName().compareTo(p1.getSurName()));
```

# Listener Lambda
* Lambdas offer simple solutions to event driven programming paradigms
* Listener lambdas can listen/ handle events inline 
    + JButtons
    + RadioButtons
    + print alert / send message


#API's (Problems)
* Problems with API's
    + API classes like CallBackHandler, Runnable, Callable, EventHandler or Comparator use single abstract method
    + To utilize these you often have to write an anonymous inner class like so:
    ```Java
    foo.doSomething(new CallBackHandler()) {
        Public void callback(Context c) {
            System.out.println("Success");
        }
    }
    ```
    + These are very bulky. Creates what is often a vertical problem using 5 lines of source code for single idea

#API's (Solution)
* Lambda expression solution
    + Replace machinery of anonymous inner classes with a simpler mechanism by adding function types to the language
    + Simplified to 
    ```Java
    CallBackHandler cd = #{ c -> 
     System.out.println("success")};
    ```

#Summary
* Lambda expressions in Java allow functions to be passed and stored like data
* Lambdas are a powerful feature that work directly with SAM types.
* Previously complex syntax that utilizes anonymous inner classes has been drastically simplified 
* For the first time in Java’s history we find something that cannot be assigned to a reference of type object

#References
* References
    + http://www.oracle.com/webfolder/technetwork/tutorials/
       obe/java/Lambda-QuickStart/index.html
    + http://www.lambdafaq.org/
    + https://www.jcp.org/en/jsr/proposalDetails?id=335
    + http://openjdk.java.net/projects/lambda/
    + http://cr.openjdk.java.net/~briangoetz/lambda/lambda-state-3.html
    + http://stackoverflow.com/questions/22637900/java8-lambdas-vs-anonymous-classes
* Useful links
    + https://www.youtube.com/watch?v=a450CqNXFgs
