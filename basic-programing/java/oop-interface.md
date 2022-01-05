## Interface

An interface is a description of the actions that an object can do.
Example, Animals (Cow, Dog, Cat...) have actions `eat` and `sound`. In this case of Animal, an Interface will define the actions, and other classes (Cow, Cat...) will decrible how is these actions.

Interface allows the users to create programs, specifying the public methods that a class must implement.


> Notes on Interfaces:

- Like abstract classes, interfaces cannot be used to create objects (in the example above, it is not possible to create an "Animal" object in the MyMainClass)
- Interface methods do not have a body - the body is provided by the "implement" class
- On implementation of an interface, you must override all of its methods
- Interface methods are by default abstract and public
- Interface attributes are by default public, static and final
- An interface cannot contain a constructor (as it cannot be used to create objects)

> Why And When To Use Interfaces?
1) To achieve security - hide certain details and only show the important details of an object (interface).

2) Java does not support "multiple inheritance" (a class can only inherit from one superclass). However, it can be achieved with interfaces, because the class can implement multiple interfaces. Note: To implement multiple interfaces, separate them with a comma

**Creating an Interface**

Following is an example of how to define an interface using the interface keyword.

```java
<?java

interface MyInterfaceName { 
   public void methodA(); 
   public void methodB(); 
}
?> 
```

Few characteristics of an Interface are:

- An interface consists of methods that have no implementations, which means the interface methods are abstract methods.
- All the methods in interfaces must have public visibility scope.
- Interfaces are different from classes as the class can inherit from one class only whereas the class can implement one or more interfaces.

To implement an interface, use the implements operator as follows:

```java
class MyClassName implements MyInterfaceName{ 
   public void methodA() {  
     // method A implementation 
   }  

   public void methodB(){  
     // method B implementation 
   }  
} 
```

**Concrete Class**: The class which implements an interface is called the Concrete Class. It `must implement all` the methods defined in an interface. Just like any class, an interface can be extended using the extends operator as below:

```java
interface MyInterfaceName1{ 
	public function methodA(); 
} 

interface MyInterfaceName2 extends MyInterfaceName1 { 
	public function methodB(); 
} 

```

## Interface Example

```java
// Interface
interface Animal {
  public void sound(); // interface method (does not have a body)
  public void eat(); // interface method (does not have a body)
}

// Cow "implements" the Animal interface
class Cow implements Animal {
  public void sound() {
    // The body of sound() is provided here
    System.out.println("The cow says cow cow");
  }
  public void eat() {
    // The body of eat() is provided here
    System.out.println("The cow eats vegetables");
  }
}

// Cat "implements" the Animal interface
class Cat implements Animal {
  public void sound() {
    System.out.println("The cat says meow meow");
  }
  public void eat() {
    System.out.println("The cat eats beefsteak");
  }
}

public class Main {
    public static void main(String args[]) {
        Cow cow = new Cow();
        Cat cat = new Cat();

        Animal[] animals = new Animal[] { cow, cat };

        for (int i = 0; i < animals.length; i++) {
            animals[i].sound();
            animals[i].eat();  
        }
    }
}
```

Output:

```
The cow says cow cow
The cow eats vegetables
The cat says meow meow
The cat eats beefsteak
```

[Try it](https://repl.it/@ohralathe/java-interface)
