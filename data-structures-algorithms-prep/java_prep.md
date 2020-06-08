# LANGUAGE SPECIFIC CONCEPTS 
## 4 Fundamental OOPs Concepts
- ### Abstraction 
Means that an abstract method is ***only declared*** but not implemented. Another class will inherit all non abstract methods and will only have to implement funcitonality to the abstract methods.
  - **Example:**

        class abstract Employee {}          //can have non abstract methods that FullTime and ParTime will inherit
        class FullTime extends Employee {}  //need to implement abstract methods. For example, timeWorked()
        class PartTime extends Employee {}  //need to implement abstract methods. For example, timeWorked()

- ### Polymorphism 
***Override/Overload*** method. Means "many forms". Classes that inherit from another can have a different implementation of a method. Depending on how the object is created is which implementation is going to be called.
  - **Example:**
        
        class Person{ public void read(){...} }
        class Student extends Person{ public void read(){...} }

        Person p = new Person();
        Person s = new Student();
        p.read();
        s.read();                       //the methods called by p and s will be different since they are differently implemented

- ### Inheritance 
Lets us ***inherit attributes*** and methods from another class. A feature that represents the "is a" relationship between different classes.

  - **Example:**

        class Person {}
        class Student extends Person {} //Student will inherit all Person's attributes and methods
                                        //Student "is a" Person

- ### Encapsulation 
The process of wrapping the data (variables) and code acting on the data (methods) together as a single unit. In encapsulation, the variables of a class will be hidden from other classes, and can be accessed only through the methods of their current class. Therefore, it is also known as ***data hiding***.

    To achieve encapsulation in Java −
        Declare the variables of a class as private.
        Provide public setter and getter methods to modify and view the variables values.

## Concepts
**Function** = Method = Procedure

**Data** = Characteristics = Properties = Attributes  

**OOP:** Define data type or data structures which becomes an object by including both data and functions

**Unified Modeling Language (uml):** Standard for languages such as having classes

**Primitives:** Most basic data types available within the Java language. There are 8: boolean, byte, char, short, int, long, float and double

**Literals:** Any constant value which can be assigned to the variable is called as literal/constant

**Variables:** Reserved area allocated in memory. In other words, it is a name of memory location.
  - **Local Variable:** A variable declared ***inside the body of the method*** is called local variable. You can use this variable only within that method and the other methods in the class aren't even aware that the variable exists. A local variable cannot be defined with "static" keyword.
  - **Instance Variable:** A variable declared ***inside the class*** (outside of method), is called instance variable. It is not declared as static. It is called instance variable because its value is instance specific and is not shared among instances.
  - **Static Variable:** A variable which is ***declared as static*** is called static variable. It cannot be local. You can create a single copy of static variable and ***share among all the instances of the class***. Memory allocation for static variable happens only once when the class is loaded in the memory.

**Packages:** A package in Java is used to group related classes. Think of it as a folder in a file directory. We use packages to avoid name conflicts, and to write a better maintainable code. Packages are divided into two categories:
  - ***Built-in Packages*** (packages from the Java API)
  - ***User-defined Packages*** (create your own packages)

**Recursion:** Function calls itself

**Class:** Determines how an object will behave and what the object will contain. In other words, it is a blueprint or a set of instruction to build a specific type of object.
  - **Methods:** A method is a block of code which only runs when it is called.
  - **Modifiers:** A class can be public or has default access
  - **Class name:** The name should begin with a initial letter (capitalized by convention)
  - **Superclass(if any):** The name of the class’s parent (superclass), if any, preceded by the keyword extends. A class can only extend (subclass) one parent.
  - **Interfaces(if any):** A comma-separated list of interfaces implemented by the class, if any, preceded by the keyword implements. A class can implement more than one interface.
  - **Body:** The class body surrounded by braces, { }.
  - **Final:** Method/variable can't be override

**Data hiding:** The process of hiding details of an object or function. Information hiding is a powerful programming technique because it reduces complexity.

**Interface:** An interface is a completely "abstract class" that is used to group related methods with empty bodies. An abstract class is semi abstract

**Messaging:** Message passing is a form of communication used in parallel programming and object-oriented programming.

**Parallel programming:** Write code that utilizes multiple cores of computer to make the program run faster.

**Object:** Self-contained entity that consists of both data and methods to manipulate the data.

**Static:** Variables/fields and methods belongs to the class instead of the object (can be called without creating an object of the class). Only one copy of it and is shared across all objects declared from this class. Static class let us use a class within a class

**Immutable object:** Object whose internal state remains constant after it has been entirely created (no setter). Everything inside is private or final

Java negative values are **2's complement**

**Overloading:** When two methods have the same name but different input parameters

**Garbage collector:**
  - ***Benefits/Contraints*** of having vs C/C++ that don't
    - ***Automatically*** handles the deletion of unused objects or objects that are out of reach to free up vital memory resources.

**Heap vs stack:** stack memory is used to store local variables and function call 
                heap memory is used to store objects

**Nested classes:** The nested class architecture is divided into two:
  - Nested classes that are declared ***static*** are called static nested classes whereas,
  - Nested classes that are ***non-static*** are called inner classes
  - The main difference between these two is that the ***inner classes have access to all member*** of the enclosing class (including private), whereas the ***static nested classes only have access to static members*** of the outer class.

**Checked vs Unchecked Exceptions:** Checked exceptions are checked during ***compile time*** and uncheked during ***runtime***.
  - ***Checked Exceptions:***
    - SQLException
    - IOException
    - ClassNotFoundException
    - InvocationTargetException
  - ***Unchecked Exceptions:***
    - NullPointerException
    - ArrayIndexOutOfBoundsException
    - ArithmeticException
    - IllegalArgumentException
    - NumberFormatException

**Parameter Passing Conventions:** Java is always passed by value. However, when we pass the value we are passing the reference to it.

**Scope:** The part of the program where the variable is accessible. For example, a method variable only lives withing the method.

**JDK:** Java Development Kit
  - Is for Deveopment. 
  - Includes JRE.
  - Includes JVM.    

**JRE:** Java Runtime Environment
  - It has the everything needed for Running the java programs.
  - Includes JVM.

**JVM:** Java Virtual Machine
  - Included in both JDK and JRE.   
  - Converts byte code to machine specific code and provides platform independence. 

**Concurrency:** Ability to run several programs or several parts of a program in parallel.

**Processes:** Runs independently and isolated of other processes. Thread is subset of process. A process is a program in execution

**Threads:** A thread is an independent path of execution within a program.

**Multi Threading:** has multiple threads running concurrently within a program, each thread is performing some specific task to improve CPU performance

**Synchronized:** If we are executing something then we need to wait for it to finish before moving to another task

**Non synchronized:** Can execute multiple threads at the same time

## OO Design Pros:
- **Reuse code** with inheritance         (Inheritance)
- Flexibility by **overriding methods**   (Polymorphism)
- Break down solutions into bits of code by separating them into **objects**
- Easier to **maintain**


## OOP Design patterns
- ### Creational Patterns: 
  - **Abstract Factory** The Abstract Factory (A.K.A. Kit) is a design pattern which provides an interface for creating families of related or dependent objects without specifying their concrete classes. The Abstract Factory pattern takes the concept of the Factory Method Pattern to the next level. An abstract factory is a class that provides an interface to produce a family of objects.
  - **Builder** The intent of the Builder Pattern is to separate the construction of a complex object from its representation, so that the same construction process can create different representations. This type of separation reduces the object size. The design turns out to be more modular with each implementation contained in a different builder object. Adding a new implementation (i.e., adding a new builder) becomes easier.
  - **Factory Method** The Factory Method Pattern gives us a way to encapsulate the instantiations of concrete types. The Factory Method pattern encapsulates the functionality required to select and instantiate an appropriate class, inside a designated method referred to as a factory method. The Factory Method selects an appropriate class from a class hierarchy based on the application context and other influencing factors. It then instantiates the selected class and returns it as an instance of the parent class type.
  - **Prototype** The Prototype design pattern is used to specify the kinds of objects to create using a prototypical instance, and create new objects by copying this prototype. The concept is to copy an existing object rather than creating a new instance from scratch, something that may include costly operations. The existing object acts as a prototype and contains the state of the object.
  - **Singleton**	The Singleton pattern is used when there must be exactly one instance of a class, and it must be accessible to clients from a well-known access point or when the sole instance should be extensible by sub-classing, and clients should be able to use an extended instance without modifying their code.

- ### Structural Patterns: 
  - **Adapter**	Adapter works as a real world adapter which is used to connect two different pieces of equipment that cannot be connected directly. An adapter sits in-between these equipments, it gets the flow from the equipment and provides it to the other equipment in the form it wants, which otherwise, is impossible to get due to their incompatible interfaces. An adapter uses composition to store the object it is supposed to adapt, and when the adapter’s methods are called, it translates those calls into something the adapted object can understand and passes the calls on to the adapted object. The code that calls the adapter never needs to know that it’s not dealing with the kind of object it thinks it is, but an adapted object instead.
  - **Bridge** The Bridge Pattern’s intent is to decouple an abstraction from its implementation so that the two can vary independently. It puts the abstraction and implementation into two different class hierarchies so that both can be extend independently.
  - **Composite**	The Composite Pattern allows you to compose objects into a tree structure to represent the part-whole hierarchy which means you can create a tree of objects that is made of different parts, but that can be treated as a whole one big thing. Composite lets clients to treat individual objects and compositions of objects uniformly, that’s the intent of the Composite Pattern.
  - **Decorator** The intent of the Decorator Design Pattern is to attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative to sub-classing for extending functionality. The pattern is used to extend the functionality of an object dynamically without having to change the original class source or using inheritance. This is accomplished by creating an object wrapper referred to as a Decorator around the actual object.
  - **Façade** The Facade Pattern makes a complex interface easier to use, using a Facade class. The Facade Pattern provides a unified interface to a set of interface in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.
  - **Flyweight** The Flyweight Pattern is designed to control object creation where objects in an application have great similarities and are of a similar kind, and provides you with a basic caching mechanism. It allows you to create one object per type (the type here differs by a property of that object), and if you ask for an object with the same property (already created), it will return you the same object instead of creating a new one.
  - **Proxy** The Proxy Pattern provides a surrogate or placeholder for another object to control access to it. It comes up with many different variations. Some of the important variations are, Remote Proxy, Virtual Proxy, and Protection Proxy. In this lesson, we will know more about these variations and we will implement each of them in Java. But before we do that, let’s get to know more about the Proxy Pattern in general. You will learn how and when the Proxy design pattern should be used and how to structure your code in order to implement it.

- ### Behavioral Patterns
  - **Chain of Responsibility** The Chain of Responsibility pattern is a behavior pattern in which a group of objects is chained together in a sequence and a responsibility (a request) is provided in order to be handled by the group. If an object in the group can process the particular request, it does so and returns the corresponding response. Otherwise, it forwards the request to the subsequent object in the group.
  - **Command** The Command Design Pattern is a behavioral design pattern and helps to decouples the invoker from the receiver of a request. The intent of the Command Design Pattern is to encapsulate a request as an object, thereby letting the developer to parameterize clients with different requests, queue or log requests, and support undoable operations.
  - **Interpreter** The Interpreter Design Pattern is a heavy-duty pattern. It’s all about putting together your own programming language, or handling an existing one, by creating an interpreter for that language. Given a language, we can define a representation for its grammar along with an interpreter that uses the representation to interpret sentences in the language.
  - **Iterator** The intent of the Iterator Design Pattern is to provide a way to access the elements of an aggregate object sequentially without exposing its underlying representation. he Iterator pattern allows a client object to access the contents of a container in a sequential manner, without having any knowledge about the internal representation of its contents.
  - **Mediator** The Mediator Pattern defines an object that encapsulates how a set of objects interact. Mediator promotes loose coupling by keeping objects from referring to each other explicitly, and it lets you vary their interaction independently. Rather than interacting directly with each other, objects ask the Mediator to interact on their behalf which results in reusability and loose coupling. You will learn how and when the Mediator design pattern should be used and how to structure your code in order to implement it.
  - **Memento** Sometimes it’s necessary to record the internal state of an object. This is required when implementing checkpoints and “undo” mechanisms that let users back out of tentative operations or recover from errors. You must save state information somewhere, so that you can restore objects to their previous conditions. But objects normally encapsulate some or all of their state, making it inaccessible to other objects and impossible to save externally. Exposing this state would violate encapsulation, which can compromise the application’s reliability and extensibility. The Memento pattern can be used to accomplish this without exposing the object’s internal structure.
  - **Observer** The Observer Pattern is a kind of behavior pattern which is concerned with the assignment of responsibilities between objects. It should be used when an abstraction has two aspects, one dependent on the other, when a change to one object requires changing others, and you don’t know how many objects need to be changed or when an object should be able to notify other objects without making assumptions about who these objects are. In other words, you don’t want these objects tightly coupled.
  - **State** The State Design Pattern allows an object to alter its behavior when its internal state changes. The object will appear to change its class. The state of an object can be defined as its exact condition at any given point of time, depending on the values of its properties or attributes. The set of methods implemented by a class constitutes the behavior of its instances. Whenever there is a change in the values of its attributes, we say that the state of an object has changed.
  - **Strategy** The Strategy Design Pattern seems to be the simplest of all design patterns, yet it provides great flexibility to your code. This pattern is used almost everywhere, even in conjunction with the other design patterns. The Strategy Design Pattern defines a family of algorithms, encapsulating each one, and making them interchangeable. Strategy lets the algorithm vary independently from the clients that use it.
  - **Template Method** The Template Design Pattern is a behavior pattern and, as the name suggests, it provides a template or a structure of an algorithm which is used by users. A user provides its own implementation without changing the algorithm’s structure. The Template Pattern defines the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses to redefine certain steps of an algorithm without changing the algorithm’s structure.
  - **Visitor** The Visitor Design Pattern provides you with a way to add new operations on the objects without changing the classes of the elements, especially when the operations change quite often. The intent of the Visitor Design Pattern is to represent an operation to be performed on the elements of an object structure. Visitor lets you define a new operation without changing the classes of the elements on which it operates.