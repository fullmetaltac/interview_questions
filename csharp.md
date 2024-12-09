# Table of Contents
- [Table of Contents](#table-of-contents)
  - [General](#general)
    - [What is the difference between a method and a function in C#?](#what-is-the-difference-between-a-method-and-a-function-in-c)
    - [What is object-oriented programming?](#what-is-object-oriented-programming)
    - [What is an abstract class in C# and when is it used?](#what-is-an-abstract-class-in-c-and-when-is-it-used)
    - [What is an interface in C# and what is its purpose?](#what-is-an-interface-in-c-and-what-is-its-purpose)
    - [Can you explain the difference between an abstract class and an interface in C#?](#can-you-explain-the-difference-between-an-abstract-class-and-an-interface-in-c)
    - [What is a constructor in C# and what are its different types?](#what-is-a-constructor-in-c-and-what-are-its-different-types)
    - [What is a sealed class in C# and why is it used?](#what-is-a-sealed-class-in-c-and-why-is-it-used)
    - [What is the difference between a value type and a reference type in C#?](#what-is-the-difference-between-a-value-type-and-a-reference-type-in-c)
    - [Can you explain the use of the "this" keyword in C#?](#can-you-explain-the-use-of-the-this-keyword-in-c)
    - [What is a delegate in C# and how is it used?](#what-is-a-delegate-in-c-and-how-is-it-used)
    - [What is an event in C# and how is it different from a delegate?](#what-is-an-event-in-c-and-how-is-it-different-from-a-delegate)
    - [What is an anonymous method in C# and how is it used?](#what-is-an-anonymous-method-in-c-and-how-is-it-used)
    - [Can you explain the difference between a static and an instance method in C#?](#can-you-explain-the-difference-between-a-static-and-an-instance-method-in-c)
  - [References](#references)


## General

### What is the difference between a method and a function in C#?

In C#, both methods and functions are terms used to describe executable code blocks that can be called to perform specific tasks. However, there's a subtle distinction between the two:

* **Method**: A method is a code block associated with a class or struct. It defines a set of instructions that can be executed on an instance of the class or struct, or it can be a static method that is associated with the class itself rather than instances of the class. Methods are used to perform actions, manipulate data, or provide functionality related to the class.

```cs
public class MathOperations
{
    public int Add(int a, int b)
    {
        return a + b;
    }
}

class Program
{
    static void Main(string[] args)
    {
        MathOperations math = new MathOperations();
        int result = math.Add(5, 3); // Calling the method
        Console.WriteLine(result);   // Output: 8
    }
}
```

* **Function**: In C#, the term "function" is commonly used interchangeably with "method." However, in a broader context, a function is a self-contained block of code that performs a specific task and can return a value. This term is often used in languages that support both procedural programming and object-oriented programming. Since C# is primarily an object-oriented language, the concept of "function" is usually referred to as "method."
---

### What is object-oriented programming?

Object-Oriented Programming (OOP) is a programming paradigm that focuses on organizing code into objects, which are instances of classes. It promotes the idea of encapsulating data (attributes) and behavior (methods) related to a specific entity into a single unit. C# is a language that fully supports OOP concepts.

In C#, classes serve as blueprints for creating objects.

* **Class and Object Creation**: A class is a template that defines the structure and behavior of objects. An object is an instance of a class.
 
```cs
class Person
{
    public int Age;
    public string Name;

    public void Introduce()
    {
        Console.WriteLine($"Hi, I'm {Name} and I'm {Age} years old.");
    }
}

class Program
{
    static void Main()
    {
        Person person1 = new Person();
        person1.Name = "Alice";
        person1.Age = 30;
        person1.Introduce(); // Output: Hi, I'm Alice and I'm 30 years old.
    }
}
```

* **Encapsulation**: Encapsulation ensures that the internal details of an object are hidden from the outside world. It helps maintain data integrity and allows controlled access to data through methods.

```cs
class BankAccount
{
    private double balance;

    public void Deposit(double amount)
    {
        if (amount > 0)
            balance += amount;
    }

    public void Withdraw(double amount)
    {
        if (amount > 0 && amount <= balance)
            balance -= amount;
    }

    public double GetBalance()
    {
        return balance;
    }
}
```
* **Inheritance**: Inheritance allows you to create a new class based on an existing class, inheriting its attributes and methods. It promotes code reusability and hierarchy.

```cs
class Animal
{
    public string Species;

    public void MakeSound()
    {
        Console.WriteLine("Animal makes a sound.");
    }
}

class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Woof woof!");
    }
}
```

* **Polymorphism**: Polymorphism allows objects of different classes to be treated as objects of a common base class through inheritance. It enables dynamic method binding and flexibility in handling different object types.

```cs
class Shape
{
    public virtual void Draw()
    {
        Console.WriteLine("Drawing a shape.");
    }
}

class Circle : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a circle.");
    }
}

class Square : Shape
{
    public override void Draw()
    {
        Console.WriteLine("Drawing a square.");
    }
}
```

### What is an abstract class in C# and when is it used?
In C#, an abstract class is a class that cannot be instantiated directly and must be inherited by a subclass. It is a way to provide a common interface and shared implementation for a group of related classes, while also allowing for individual implementation in each subclass.

An abstract class is defined using the abstract keyword before the class keyword. It can have abstract methods, which are declared without implementation, as well as non-abstract methods with implementation. Subclasses that inherit from the abstract class must implement all abstract methods or else they will also be abstract.

```cs
public abstract class Shape
{
    public abstract double GetArea();
    public abstract double GetPerimeter();
}

public class Rectangle : Shape
{
    private double length;
    private double width;
    
    public Rectangle(double length, double width)
    {
        this.length = length;
        this.width = width;
    }
    
    public override double GetArea()
    {
        return length * width;
    }
    
    public override double GetPerimeter()
    {
        return 2 * (length + width);
    }
}
```
---

### What is an interface in C# and what is its purpose?
In C#, an interface is a contract that defines a set of methods, properties, events, or indexers without implementing them. An interface does not contain any code for the behavior; it only specifies what can be done, not how it is done. Classes or structs that implement an interface are responsible for providing the concrete implementation for each member defined in the interface.

**Purpose of Interfaces in C#**  

The primary purpose of interfaces is to achieve abstraction and separation of concerns. Interfaces help in:

* **Defining a contract**: They force implementing classes to follow a certain structure, ensuring consistency across multiple types.
* **Loose coupling**: By depending on interfaces rather than concrete implementations, we reduce dependencies between parts of the code. This promotes better maintainability and flexibility.
* **Multiple inheritance**: C# does not support multiple class inheritance but allows a class to implement multiple interfaces.
* **Testability**: Interfaces make unit testing easier because they allow us to substitute real implementations with mock objects.

Let’s consider a scenario where we are designing a payment system for an e-commerce platform. The system needs to support multiple payment methods such as Credit Card, PayPal, and Bank Transfer.

```cs
public interface IPaymentProcessor
{
    void ProcessPayment(decimal amount);
    bool ValidatePaymentDetails();
}
```

```cs
public class CreditCardPaymentProcessor : IPaymentProcessor
{
    public void ProcessPayment(decimal amount)
    {
        Console.WriteLine($"Processing credit card payment of {amount}...");
        // Logic to process credit card payment
    }

    public bool ValidatePaymentDetails()
    {
        Console.WriteLine("Validating credit card details...");
        // Logic to validate credit card information
        return true;
    }
}
```
```cs
public class PayPalPaymentProcessor : IPaymentProcessor
{
    public void ProcessPayment(decimal amount)
    {
        Console.WriteLine($"Processing PayPal payment of {amount}...");
        // Logic to process PayPal payment
    }

    public bool ValidatePaymentDetails()
    {
        Console.WriteLine("Validating PayPal account...");
        // Logic to validate PayPal account
        return true;
    }
}
```
---

### Can you explain the difference between an abstract class and an interface in C#?

**Abstract Class:**  

An abstract class is a blueprint for other classes. It can contain both abstract members (without implementation) and concrete members (with implementation). Abstract classes serve as base classes and are used to provide common functionality to derived classes.

**Key Features:**  

* **Inheritance**: Supports single inheritance; a class can inherit from only one abstract class.
* **Members**: Can include fields, properties, methods, events, and constructors. Both abstract and concrete members are allowed.
* **Access Modifiers**: Members can have access modifiers (e.g., `public`, `protected`, `private`).
* **Purpose**: Used when there is a "is-a" relationship and shared implementation logic.

```cs
public abstract class Animal
{
    public abstract void MakeSound();

    public void Sleep()
    {
        Console.WriteLine("Sleeping...");
    }
}
```


**Interface:**  

An interface defines a contract for classes to implement. It contains only the signatures of methods, properties, events, or indexers without any implementation.

**Key Features:**  

* **Multiple Inheritance**: A class can implement multiple interfaces.
* **Members**: Cannot include fields or concrete members; all members are implicitly public and abstract.
* **Access Modifiers**: Members cannot have access modifiers; they are always public.
* **Purpose**: Used when there is a "can-do" relationship or when you want to define a strict contract.

```cs
public interface IAnimal
{
    void MakeSound();
    void Sleep();
}
```

**Key Differences**

| Feature                   | Abstract Class                          | Interface                         |
|---------------------------|-----------------------------------------|-----------------------------------|
| **Implementation**         | Can include concrete methods and fields. | Cannot include concrete methods or fields. |
| **Inheritance**            | Single inheritance allowed.            | Multiple inheritance allowed.     |
| **Access Modifiers**       | Members can have any access modifier.   | All members are implicitly `public`. |
| **Constructors**           | Can have constructors.                 | Cannot have constructors.         |
| **Usage Scenario**         | Use for shared behavior or base class.  | Use for defining a contract.      |

---

### What is a constructor in C# and what are its different types?

In C#, a constructor is a special method that is called when an object of a class is created. The purpose of a constructor is to initialize the state of an object with some initial values.

C# supports two types of constructors:

* **Instance Constructors**: An instance constructor is used to initialize the instance variables of a class. It is called when an object of the class is created using the new keyword. An instance constructor has the same name as the class and does not have a return type. Here is an example of an instance constructor:

```cs
public class MyClass {
    public int x;
    public int y;

    public MyClass(int x, int y) {
        this.x = x;
        this.y = y;
    }
}
```

* **Static Constructors**: A static constructor is used to initialize the static variables of a class. It is called only once, when the class is first used. A static constructor has the same name as the class and does not have any parameters. Here is an example of a static constructor:

```cs
public class MyClass {
    public static int x;
    public static int y;

    static MyClass() {
        x = 10;
        y = 20;
    }
}
```

 > Note that a class can have multiple constructors, but they must have different signatures (i.e., different parameter lists). This is known as constructor overloading.

---

### What is a sealed class in C# and why is it used?

In C#, a sealed class is a class that cannot be inherited by other classes. When a class is marked as sealed, it means that it is complete and cannot be extended further.

The main reason to use a sealed class is to prevent the class from being modified or extended by other developers. This is useful when you want to ensure that the class works as intended and cannot be altered in unexpected ways. Sealed classes are also useful for performance reasons, as they can be optimized more effectively by the compiler.

```cs
sealed class MySealedClass
{
    // class members
}
```
---

### What is the difference between a value type and a reference type in C#?

In C#, data types are categorized into two main categories: value types and reference types. The distinction between these two types is crucial because it affects how data is stored and manipulated in memory.

* **Value Types**:  
  
Value types directly store the value itself, and they are usually stored in the stack memory. When you assign a value type to a new variable or pass it as a parameter to a method, a copy of the value is made. As a result, changes made to the copied value do not affect the original value.

```cs
// Numeric Types:
int x = 5;
int y = x; // y gets a copy of the value in x
y = 10;    // Changing y does not affect x
```

```cs
// Enumerations:
enum Color { Red, Green, Blue }
Color color1 = Color.Red;
Color color2 = color1; // color2 gets a copy of color1
color2 = Color.Green;  // Changing color2 does not affect color1
```

```cs
// Structures:
struct Point { public int X; public int Y; }
Point p1 = new Point { X = 2, Y = 3 };
Point p2 = p1;         // p2 gets a copy of p1
p2.X = 5;              // Changing p2 does not affect p1
```

* **Reference Types**:  
  
Reference types store a reference to the memory location where the data is actually stored, usually on the heap. When you assign a reference type to a new variable or pass it as a parameter to a method, you're passing a reference to the same memory location. This means changes made to the data are reflected wherever that data is referenced.

```cs
// Classes:
class Person { public string Name; }
Person person1 = new Person { Name = "Alice" };
Person person2 = person1;  // person2 references the same object as person1
person2.Name = "Bob";      // Changing person2 also changes person1
```
```cs
// Arrays:
int[] arr1 = new int[] { 1, 2, 3 };
int[] arr2 = arr1;      // arr2 references the same array as arr1
arr2[0] = 5;            // Changing arr2 also changes arr1
```
```cs
// Strings:
string str1 = "Hello";
string str2 = str1;     // str2 references the same string as str1
str2 = "Hi";            // Changing str2 does not affect str1
```
---

### Can you explain the use of the "this" keyword in C#?

In C#, the "this" keyword is a reference to the current instance of a class or struct. It is commonly used to:

* Distinguish between instance variables and local variables with the same name.

```cs
class MyClass {
   int num;

   public void SetNum(int num) {
      this.num = num; // use "this" to refer to the instance variable
   }
}
```

* Pass the current object as an argument to another method or constructor. 

```cs
class MyClass {
   int num;

   public MyClass(int num) {
      this.num = num; // pass "this" as an argument to set the instance variable
   }

   public void DoSomething() {
      OtherClass.Method(this); // pass "this" as an argument to another method
   }
}
```

* Return the current object from a method. This is useful for chaining method calls.

```cs
class MyClass {
   public MyClass DoSomething() {
      // do something
      return this; // return the current object
   }

   public MyClass DoSomethingElse() {
      // do something else
      return this; // return the current object
   }
}
```

---

### What is a delegate in C# and how is it used?

In C#, a delegate is a type that represents a method with a specific signature. It can be used to reference a method and invoke it indirectly, which provides a flexible way of decoupling the caller from the callee.

A delegate declaration defines the signature of the method that it can reference. For example, the following delegate declaration defines a delegate type named MyDelegate that can reference a method that takes two integers as parameters and returns an integer:

```cs
delegate int MyDelegate(int x, int y);
```

A delegate object can be created by instantiating a delegate type with a method name or a lambda expression that matches the signature of the delegate type. For example, the following code creates a delegate object that references a method named Add
```cs
MyDelegate myDelegate = Add;
```
or with a lambda expression:
```cs
MyDelegate myDelegate = (x, y) => x + y;
```
Once a delegate object is created, it can be invoked like a method. The following code invokes the delegate object created above:
```cs
int result = myDelegate(1, 2); // result == 3
```

Delegates can also be used as event handlers in C# programs. When an event occurs, the delegate associated with the event is invoked, which can trigger the corresponding event handling code.

---

### What is an event in C# and how is it different from a delegate?

>**Delegates in C#**:  
  
A delegate is essentially a type-safe function pointer. It holds references to methods with a specific signature and return type, allowing methods to be passed as arguments or assigned to variables. Delegates enable dynamic method invocation, meaning that the methods they point to can be changed at runtime.

**Key Features of Delegates**:  

* **Type-Safety**: Delegates ensure that the methods they reference have the correct signature (input parameters and return type).
* **Multicasting**: A single delegate can reference multiple methods. When invoked, it calls each method in the order they were added.
* **Flexibility**: Delegates allow methods to be passed as parameters, useful for callback implementations, and facilitate decoupling of method logic from the caller.

```cs
public delegate void ProcessEvent(string message);

public class EventProcessor
{
    public void ProcessLog(string message)
    {
        Console.WriteLine($"Logging: {message}");
    }

    public void ProcessAlert(string message)
    {
        Console.WriteLine($"Alert: {message}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        EventProcessor processor = new EventProcessor();
        
        // Instantiate the delegate
        ProcessEvent processDelegate = processor.ProcessLog;
        
        // Multicast - add another method
        processDelegate += processor.ProcessAlert;

        // Invoke the delegate
        processDelegate("Critical system error");
    }
}
```

> Events in C#

An event is a specialized form of a delegate designed to enable safe and structured communication between objects, adhering to the publish-subscribe pattern. Events are used when one or more subscribers are interested in being notified when something occurs within a class.

**Key Features of Events**:

* **Encapsulation**: Unlike delegates, events add an additional layer of security by restricting the invocation of the event to the declaring class. Subscribers can only register or unregister from the event but cannot invoke it.
* **Publish-Subscribe Model**: Events allow objects to subscribe to specific events (e.g., when a button is clicked), and the event is raised when the triggering condition occurs.
* **Loose Coupling**: Events decouple the sender of the event from its subscribers. This means the class raising the event doesn’t need to know which specific methods will handle the event, which promotes a modular and maintainable design.

```cs
public delegate void Notify(string message);

public class Publisher
{
    // Declare the event using the delegate
    public event Notify OnPublishEvent;

    public void Publish(string message)
    {
        // Raise the event if there are subscribers
        OnPublishEvent?.Invoke(message);
    }
}

public class Subscriber
{
    public void HandleEvent(string message)
    {
        Console.WriteLine($"Subscriber received: {message}");
    }
}

class Program
{
    static void Main(string[] args)
    {
        Publisher publisher = new Publisher();
        Subscriber subscriber = new Subscriber();

        // Subscribe to the event
        publisher.OnPublishEvent += subscriber.HandleEvent;

        // Trigger the event
        publisher.Publish("New event occurred!");
    }
}
```
---

### What is an anonymous method in C# and how is it used?

In C#, an anonymous method is a method that does not have a name and is defined inline within the code of another method or expression. It can be used in place of a named method anywhere a delegate is expected. A delegate is an object that can refer to a method and can be passed as a parameter or returned as a value.

Anonymous methods can be defined using the delegate keyword, followed by the argument list and body of the method. 

```cs
delegate (int x, int y) {
    return x + y;
};
```
```cs
int result = myDelegate(3, 4); // result = 7
```

Alternatively, C# also introduced lambda expressions, which are a shorter and more readable syntax for creating anonymous methods. For example, the anonymous method above can be expressed as a lambda expression like this:

```cs
(x, y) => x + y
```

Anonymous methods are commonly used in event handling and LINQ queries, among other places, where they allow for concise and flexible code.

---

### Can you explain the difference between a static and an instance method in C#?

---


---
  ## References
   - https://github.com/rcallaby/CSharp-Interview-Questions
    