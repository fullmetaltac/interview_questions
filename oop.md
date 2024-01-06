# Table of Contents
- [Table of Contents](#table-of-contents)
  - [OOP Concepts](#oop-concepts)
    - [Encapsulation](#encapsulation)
    - [Inheritance](#inheritance)
    - [Polymorphism](#polymorphism)
    - [Abstraction](#abstraction)
  - [Quiz](#quiz)
  - [References](#references)

## OOP Concepts

### Encapsulation
Encapsulation is one of the fundamental concepts of object-oriented programming, which helps to protect the data and methods of an object from unauthorized access and modification. It is a way to achieve data abstraction, which means that the implementation details of an object are hidden from the outside world, and only the essential information is exposed.

In Python, encapsulation can be achieved by using access modifiers. Access modifiers are keywords that define the accessibility of attributes and methods in a class. The three access modifiers available in Python are public, private, and protected. However, Python does not have an explicit way of defining access modifiers like some other programming languages such as Java and C++. Instead, it uses a convention of using underscore prefixes to indicate the access level.

In the given code example, the class MyClass has two attributes, _protected_var and __private_var. The _protected_var is marked as protected by using a single underscore prefix. This means that the attribute can be accessed within the class and its subclasses but not outside the class. The __private_var is marked as private by using two underscore prefixes. This means that the attribute can only be accessed within the class and not outside the class, not even in its subclasses.

When we create an object of the MyClass class, we can access the _protected_var attribute using the object name with a single underscore prefix. However, we cannot access the __private_var attribute using the object name, as it is hidden from the outside world. If we try to access the __private_var attribute, we will get an AttributeError as shown in the code.

In summary, encapsulation is an important concept in object-oriented programming that helps to protect the implementation details of an object. In Python, we can achieve encapsulation by using access modifiers and using underscore prefixes to indicate the access level.

```python
# Define a class named MyClass
class MyClass:

    # Constructor method that initializes the class object
    def __init__(self):

        # Define a protected variable with an initial value of 10
        # The variable name starts with a single underscore, which indicates protected access
        self._protected_var = 10

        # Define a private variable with an initial value of 20
        # The variable name starts with two underscores, which indicates private access
        self.__private_var = 20

# Create an object of MyClass class
obj = MyClass()

# Access the protected variable using the object name and print its value
# The protected variable can be accessed outside the class but
# it is intended to be used within the class or its subclasses
print(obj._protected_var)   # output: 10

# Try to access the private variable using the object name and print its value
# The private variable cannot be accessed outside the class, even by its subclasses
# This will raise an AttributeError because the variable is not accessible outside the class
print(obj.__private_var)    # AttributeError: 'MyClass' object has no attribute '__private_var'
```

### Inheritance
Inheritance promotes code reuse and allows you to create a hierarchy of classes that share common attributes and methods. It helps in creating clean and organized code by keeping related functionality in one place and promoting the concept of modularity. The base class from which a new class is derived is also known as a parent class, and the new class is known as the child class or subclass.

In the code, we define a class named Animal which has a constructor method that initializes the class object with a name attribute and a method named speak. The speak method is defined in the Animal class but does not have a body.

We then define two subclasses named Dog and Cat which inherit from the Animal class. These subclasses override the speak method of the Animal class.

We create a Dog object with a name attribute “Rover” and a Cat object with a name attribute “Whiskers”. We call the speak method of the Dog object using dog.speak(), and it prints “Woof!” because the speak method of the Dog class overrides the speak method of the Animal class. Similarly, we call the speak method of the Cat object using cat.speak(), and it prints “Meow!” because the speak method of the Cat class overrides the speak method of the Animal class.

```python
# Define a class named Animal
class Animal:

    # Constructor method that initializes the class object with a name attribute
    def __init__(self, name):
        self.name = name

    # Method that is defined in the Animal class but does not have a body
    # This method will be overridden in the subclasses of Animal
    def speak(self):
        print("")

# Define a subclass named Dog that inherits from the Animal class
class Dog(Animal):

    # Override the speak method of the Animal class
    def speak(self):
        print("Woof!")

# Define a subclass named Cat that inherits from the Animal class
class Cat(Animal):

    # Override the speak method of the Animal class
    def speak(self):
        print("Meow!")

# Create a Dog object with a name attribute "Rover"
dog = Dog("Rover")

# Create a Cat object with a name attribute "Whiskers"
cat = Cat("Whiskers")

# Call the speak method of the Dog class and print the output
# The speak method of the Dog class overrides the speak method of the Animal class
# Therefore, when we call the speak method of the Dog object, it will print "Woof!"
dog.speak()   # output: Woof!

# Call the speak method of the Cat class and print the output
# The speak method of the Cat class overrides the speak method of the Animal class
# Therefore, when we call the speak method of the Cat object, it will print "Meow!"
cat.speak()   # output: Meow!
```

### Polymorphism
Polymorphism is an important concept in object-oriented programming that allows you to write code that can work with objects of different classes in a uniform way. In Python, polymorphism is achieved by using method overriding or method overloading.

Method overriding is when a subclass provides its own implementation of a method that is already defined in its parent class. This allows the subclass to modify the behavior of the method without changing its name or signature.

Method overloading is when multiple methods have the same name but different parameters. Python does not support method overloading directly, but it can be achieved using default arguments or variable-length arguments.

Polymorphism makes it easier to write flexible and reusable code. It allows you to write code that can work with different objects without needing to know their specific types.

```python
#The Shape class is defined with an abstract area method, which is intended to be overridden by subclasses.
class Shape:
    def area(self):
        pass

class Rectangle(Shape):
    # The Rectangle class is defined with an __init__ method that initializes
    # width and height instance variables.
    # It also defines an area method that calculates and returns
    # the area of a rectangle using the width and height instance variables.
    def __init__(self, width, height):
        self.width = width  # Initialize width instance variable
        self.height = height  # Initialize height instance variable

    def area(self):
        return self.width * self.height  # Return area of rectangle


 # The Circle class is defined with an __init__ method
 # that initializes a radius instance variable.
 # It also defines an area method that calculates and
 # returns the area of a circle using the radius instance variable.
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius  # Initialize radius instance variable

    def area(self):
        return 3.14 * self.radius ** 2  # Return area of circle using pi * r^2

# The shapes list is created with one Rectangle object and one Circle object. The for
# loop iterates over each object in the list and calls the area method of each object
# The output will be the area of the rectangle (20) and the area of the circle (153.86).
shapes = [Rectangle(4, 5), Circle(7)]  # Create a list of Shape objects
for shape in shapes:
    print(shape.area())  # Output the area of each Shape object
```

### Abstraction
Abstraction is an important concept in object-oriented programming (OOP) because it allows you to focus on the essential features of an object or system while ignoring the details that aren’t relevant to the current context. By reducing complexity and hiding unnecessary details, abstraction can make code more modular, easier to read, and easier to maintain.

In Python, abstraction can be achieved by using abstract classes or interfaces. An abstract class is a class that cannot be instantiated directly, but is meant to be subclassed by other classes. It often includes abstract methods that have no implementation, but provide a template for how the subclass should be implemented. This allows the programmer to define a common interface for a group of related classes, while still allowing each class to have its own specific behavior.

An interface, on the other hand, is a collection of method signatures that a class must implement in order to be considered “compatible” with the interface. Interfaces are often used to define a common set of methods that multiple classes can implement, allowing them to be used interchangeably in certain contexts.

Python does not have built-in support for abstract classes or interfaces, but they can be implemented using the abc (abstract base class) module. This module provides the ABC class and the abstractmethod decorator, which can be used to define abstract classes and methods.

Overall, abstraction is a powerful tool for managing complexity and improving code quality in object-oriented programming, and Python provides a range of options for achieving abstraction in your code.

```python
# Import the abc module to define abstract classes and methods
from abc import ABC, abstractmethod

# Define an abstract class called Shape that has an abstract method called area
class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

# Define a Rectangle class that inherits from Shape
class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    # Implement the area method for Rectangles
    def area(self):
        return self.width * self.height

# Define a Circle class that also inherits from Shape
class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius

    # Implement the area method for Circles
    def area(self):
        return 3.14 * self.radius ** 2

# Create a list of shapes that includes both Rectangles and Circles
shapes = [Rectangle(4, 5), Circle(7)]

# Loop through each shape in the list and print its area
for shape in shapes:
    print(shape.area())
```

## Quiz

* ***What is OOP, and why is it important in Python?***

OOP, or Object-Oriented Programming, is a programming paradigm used in many languages, including Python. In OOP, you can model real-world concepts using classes and objects. You can break down complex problems into smaller, more manageable parts. This makes the code reusable, maintainable, and scalable. 

In Python, OOP is vital because it allows you to write more structured and efficient code. OOP in Python supports code reusability through inheritance. Using OOP in Python can make your development process more efficient and your code more readable.

---
* ***What is a class in Python?***

A class in Python is like a blueprint for creating objects. A class defines properties and methods that are common to all objects created from it. 

In Python, you use the `class` keyword to define a class. 

Classes help organize code by grouping related attributes and functions, promoting reusability and modularity. For instance, if you’re creating a program to manage a library, you might have classes for books, authors, and borrowers, each with its specific attributes and methods.

---
* ***What is an object in Python?***

An object in Python is an instance of a class. You can think of it as a specific realization of the blueprint provided by the class. 

An object contains data in the form of attributes and code in the form of methods. When you create an object, you are essentially creating a variable that has all the properties and behaviors defined in the class. 

For example, if you have a class for cars, an object could represent a specific car, such as a Honda Civic, with attributes like color and speed, and methods like start and stop.

---
* ***How do you create an instance of a class in Python?***

In Python, you can create a class instance by calling the class as a function and providing necessary arguments. This process is known as instantiation. Once you create an instance, you can access the attributes and methods defined in the class using the instance. 

For example, if you have a class named `Dog`, you could create an instance of that class by writing` my_dog = Dog()`. Now, `my_dog` is an object of the `Dog` class, and you can access its attributes and methods through the `my_dog` variable. This allows you to represent specific real-world entities in your code.

---
* ***What is the constructor in a Python class?***

In Python, a constructor is a special method used to initialize objects. You can think of it as blueprint instructions for creating objects. 

When you create an instance of a class, the constructor method, __init__, is automatically called. It allows you to set up properties or execute any setup code needed for the object.

If you don’t define a constructor in your class, Python provides a default one. However, defining your own constructor gives you more control over the object initialization process.

---
* ***What is a decorator in Python? How is it related to OOP?***

A decorator in Python is a function that you can use to modify or extend the behavior of other functions or methods without changing their code. In the context of OOP, decorators can be used to add functionality to methods within classes, such as logging or access control. 

You can think of decorators as wrappers around a function or method. When you call a decorated function, the decorator’s code runs first, allowing you to perform actions before or after the original function. It helps keep the code clean and adhere to the OOP reusability principle.

---
* ***What is the purpose of the self keyword in methods?***

The self keyword in Python is used within a class to refer to the instance of the object itself. When you define a method inside a class, the first parameter is usually named self. It helps you access the attributes and methods of the class within the current object’s context. 

For example, you can use self.name to refer to the object’s name attribute. 

When calling a method, you don’t have to pass the self argument; Python automatically sends the current object reference to the method.

---
* ***How is inheritance implemented in Python?***

Inheritance allows a class to inherit attributes and methods from another class. You can create a new class – known as the child class – based on an existing class – known as the parent class – and add new features or modify existing ones. 

To implement inheritance in Python, you define the new class and put the name of the parent class in parentheses. 

For example, if you want a class Dog to inherit from a class Animal, you would write class Dog(Animal):. This way, the Dog class would have access to all the attributes and methods defined in Animal, allowing for code reusability and better organization.

---
* ***What is the use of the `super()` function?***

Python’s `super()` function is used within a class to call a method from a parent class, often within the context of method overriding. 

If you have a method in a child class with the same name as a method in the parent class, you can use super() to call the parent method within the child method. This is particularly useful when you want to extend or modify the behavior of the parent method in the child class. 

By using `super()`, you ensure that your code follows the inheritance hierarchy. It also makes the code more maintainable, as changes in the parent class can be easily propagated to child classes.

---
* ***What is the purpose of the `@property` decorator?***

In Python, the `@property` decorator allows you to treat a method as a property of the class. By using this, you can create a “getter” method, which enables you to access a class method as though it’s an attribute without needing to write parentheses when you call it. This means you can control how the attribute is accessed without directly exposing it. 

The `@property` decorator provides a way to implement encapsulation – a key concept in Object-Oriented Programming (OOP). It helps in managing the attributes of a class and making the code more readable.

---
* ***What are the different types of inheritance?***

- *Single Inheritance* – A single derived class acquires from on single superclass.
- *Multi-Level Inheritance* – At least 2 different derived classes acquire from two distinct base classes.
- *Hierarchical Inheritance* – A number of child classes acquire from one superclass
- *Multiple Inheritance* – A derived class acquires from several superclasses.

---
* ***How can you achieve multiple inheritance in Python?***

Multiple inheritance in Python means that a class can inherit characteristics and features from more than one parent class. You can achieve this by defining a class with more than one parent class inside parentheses in the class definition. This lets the derived class access attributes and methods from all its parent classes. 

While this can make code more flexible and powerful, you should use it cautiously. Multiple inheritance can lead to complex class structures.

---
* ***What is a static method and how is it different from a class method?***

A static method in Python belongs to a class rather than an instance of the class. You can define it using the `@staticmethod` decorator. It doesn’t require reference to the class or its instance and can be called on the class itself. Unlike regular instance methods, it doesn’t take a self parameter. 

A class method, on the other hand, is defined with the `@classmethod` decorator and takes a reference to the class itself as its first parameter – usually named `cls`. It can access and modify class-level attributes, while a static method can’t. 

A class method is more versatile as subclasses can override it, whereas a static method remains unchanged.

---
* ***How do you implement abstract classes and methods in Python?***

In Python, you can implement abstract classes and methods using the `ABC` module. You would first import the module and then create a class that inherits from `ABC`, which stands for abstract base class. 

Within this class, you can define abstract methods using the` @abstractmethod` decorator. These abstract methods serve as a blueprint for other classes, enforcing that the derived classes must provide a concrete implementation of these methods. 

If a derived class does not implement the abstract methods, an instantiation error will occur.

---
* ***How can you prevent method overriding in Python?***

In Python, method overriding is a common feature that allows a subclass to provide a different implementation of a method defined in its superclass. However, if you want to prevent method overriding, you can do so by defining the method as private. 

By prefixing the method’s name with a double underscore `__`, you make it private to the class, and it cannot be overridden in a subclass. 

Though not strictly enforced, this convention signals that the method should not be accessed or overridden outside the class, and it helps maintain the integrity of the original method within the hierarchy.

---
* ***How does polymorphism work in Python?***

Polymorphism in Python allows different objects to be treated as instances of the same class, even if they belong to different classes. You can achieve this through inheritance, where a subclass can have methods with the same name as the methods in the superclass. 

When you call a method on an object, Python will automatically use the correct method based on the object’s class, even if the object is referred to by a variable of the superclass type. 

This enables more flexible and reusable code, as you can write functions that work with different classes, provided they adhere to the same interface or method signature.

---

## References
- https://www.pythoncheatsheet.org/cheatsheet/oop-basics
- https://www.testgorilla.com/blog/python-oops-interview-questions/
- https://www.programiz.com/article/python-self-why