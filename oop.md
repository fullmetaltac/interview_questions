# Table of Contents
- [Table of Contents](#table-of-contents)
  - [Class](#class)
  - [Objects](#objects)
  - [self](#self)
  - [init](#init)
  - [Creating Classes and objects with methods](#creating-classes-and-objects-with-methods)
  - [Inheritance](#inheritance)
  - [Polymorphism](#polymorphism)
  - [Encapsulation](#encapsulation)
  - [Quiz](#quiz)
  - [References](#references)

In Python, object-oriented Programming (OOPs) is a programming paradigm that uses objects and classes in programming. It aims to implement real-world entities like inheritance, polymorphisms, encapsulation, etc. in the programming. The main concept of OOPs is to bind the data and the functions that work on that together as a single unit so that no other part of the code can access this data.

## Class 
A class is a collection of objects. A class contains the blueprints or the prototype from which the objects are being created. It is a logical entity that contains some attributes and methods. 

To understand the need for creating a class let’s consider an example, let’s say you wanted to track the number of dogs that may have different attributes like breed, and age. If a list is used, the first element could be the dog’s breed while the second element could represent its age. Let’s suppose there are 100 different dogs, then how would you know which element is supposed to be which? What if you wanted to add other properties to these dogs? This lacks organization and it’s the exact need for classes. 

**Some points on Python class:**

- Classes are created by keyword class.
- Attributes are the variables that belong to a class.
- Attributes are always public and can be accessed using the dot (.) operator. Eg.: Myclass.Myattribute

```python
class ClassName:
   # Statement-1
   # ...
   # Statement-N
```
Creating an Empty Class in Python
In the above example, we have created a class named Dog using the class keyword.

```python
# a class definition
 
class Dog:
    pass
```

## Objects
The object is an entity that has a state and behavior associated with it. It may be any real-world object like a mouse, keyboard, chair, table, pen, etc. Integers, strings, floating-point numbers, even arrays, and dictionaries, are all objects. More specifically, any single integer or any single string is an object. The number 12 is an object, the string “Hello, world” is an object, a list is an object that can hold other objects, and so on. You’ve been using objects all along and may not even realize it.

**An object consists of**
- State: It is represented by the attributes of an object. It also reflects the properties of an object.
- Behavior: It is represented by the methods of an object. It also reflects the response of an object to other objects.
- Identity: It gives a unique name to an object and enables one object to interact with other objects.

To understand the state, behavior, and identity let us take the example of the class dog (explained above). 

- The identity can be considered as the name of the dog.
- State or Attributes can be considered as the breed, age, or color of the dog.
- The behavior can be considered as to whether the dog is eating or sleeping.

```python
# creating an object
obj = Dog()
```

##  self  
In object-oriented programming, whenever we define methods for a class, we use `self` as the first parameter in each case. Let's look at the definition of a class called `Cat`.

```python
class Cat:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def info(self):
        print(f"I am a cat. My name is {self.name}. I am {self.age} years old.")

    def make_sound(self):
        print("Meow")
```
In this case all the methods, including `__init__`, have the first parameter as `self`.

We know that class is a blueprint for the objects. This blueprint can be used to create multiple numbers of objects. Let's create two different objects from the above class.

```python
cat1 = Cat('Andy', 2)
cat2 = Cat('Phoebe', 3)
```

The self keyword is used to represent an instance (object) of the given class. In this case, the two `Cat` objects `cat1` and `cat2` have their own `name` and `age` attributes. If there was no `self` argument, the same class couldn't hold the information for both these objects.

However, since the class is just a blueprint, `self` allows access to the attributes and methods of each object in python. This allows each object to have its own attributes and methods. Thus, even long before creating these objects, we reference the objects as `self` while defining the class.

## init 
The `__init__` method is similar to constructors in C++ and Java. It is run as soon as an object of a class is instantiated. The method is useful to do any initialization you want to do with your object. Now let us define a class and create some objects using the self and `__init__` method.

Creating a class and object with class and instance attributes

```python
class Dog:
 
    # class attribute
    attr1 = "mammal"
 
    # Instance attribute
    def __init__(self, name):
        self.name = name
 
# Driver code
# Object instantiation
Rodger = Dog("Rodger")
Tommy = Dog("Tommy")
 
# Accessing class attributes
print("Rodger is a {}".format(Rodger.__class__.attr1))
print("Tommy is also a {}".format(Tommy.__class__.attr1))
 
# Accessing instance attributes
print("My name is {}".format(Rodger.name))
print("My name is {}".format(Tommy.name))
```

```python
# Output
Rodger is a mammal
Tommy is also a mammal
My name is Rodger
My name is Tommy
```

## Creating Classes and objects with methods
Here, The Dog class is defined with two attributes:

- attr1 is a class attribute set to the value “mammal”. Class attributes are shared by all instances of the class.
- __init__ is a special method (constructor) that initializes an instance of the Dog class. It takes two parameters: self (referring to the instance being created) and name (representing the name of the dog). The name parameter is used to assign a name attribute to each instance of Dog.
The speak method is defined within the Dog class. This method prints a string that includes the name of the dog instance.

The driver code starts by creating two instances of the Dog class: Rodger and Tommy. The __init__ method is called for each instance to initialize their name attributes with the provided names. The speak method is called in both instances (Rodger.speak() and Tommy.speak()), causing each dog to print a statement with its name.

```python
class Dog:
 
    # class attribute
    attr1 = "mammal"
 
    # Instance attribute
    def __init__(self, name):
        self.name = name
         
    def speak(self):
        print("My name is {}".format(self.name))
 
# Driver code
# Object instantiation
Rodger = Dog("Rodger")
Tommy = Dog("Tommy")
 
# Accessing class methods
Rodger.speak()
Tommy.speak()
```
```python
# Output
My name is Rodger
My name is Tommy
```

## Inheritance
Inheritance is the capability of one class to derive or inherit the properties from another class. The class that derives properties is called the derived class or child class and the class from which the properties are being derived is called the base class or parent class. The benefits of inheritance are:

- It represents real-world relationships well.
- It provides the reusability of a code. We don’t have to write the same code again and again. Also, it allows us to add more features to a class without modifying it.
- It is transitive in nature, which means that if class B inherits from another class A, then all the subclasses of B would automatically inherit from class A.

**Types of Inheritance**

- Single Inheritance: Single-level inheritance enables a derived class to inherit characteristics from a single-parent class.
 - Multilevel Inheritance: Multi-level inheritance enables a derived class to inherit properties from an immediate parent class which in turn inherits properties from his parent class. 
- Hierarchical Inheritance: Hierarchical-level inheritance enables more than one derived class to inherit properties from a parent class.
- Multiple Inheritance: Multiple-level inheritance enables one derived class to inherit properties from more than one base class.

**Inheritance in Python**

In the above article, we have created two classes i.e. Person (parent class) and Employee (Child Class). The Employee class inherits from the Person class. We can use the methods of the person class through the employee class as seen in the display function in the above code. A child class can also modify the behavior of the parent class as seen through the details() method.

```python 
# Python code to demonstrate how parent constructors
# are called.

# parent class
class Person(object):
 
    # __init__ is known as the constructor
    def __init__(self, name, idnumber):
        self.name = name
        self.idnumber = idnumber
 
    def display(self):
        print(self.name)
        print(self.idnumber)
         
    def details(self):
        print("My name is {}".format(self.name))
        print("IdNumber: {}".format(self.idnumber))
     
# child class
class Employee(Person):
    def __init__(self, name, idnumber, salary, post):
        self.salary = salary
        self.post = post
 
        # invoking the __init__ of the parent class
        Person.__init__(self, name, idnumber)
         
    def details(self):
        print("My name is {}".format(self.name))
        print("IdNumber: {}".format(self.idnumber))
        print("Post: {}".format(self.post))
 
 
# creation of an object variable or an instance
a = Employee('Rahul', 886012, 200000, "Intern")
 
# calling a function of the class Person using
# its instance
a.display()
a.details()
```
```python
# Output
Rahul
886012
My name is Rahul
IdNumber: 886012
Post: Intern
```
## Polymorphism
Polymorphism simply means having many forms. For example, we need to determine if the given species of birds fly or not, using polymorphism we can do this using a single function.

**Polymorphism in Python**

This code demonstrates the concept of inheritance and method overriding in Python classes. It shows how subclasses can override methods defined in their parent class to provide specific behavior while still inheriting other methods from the parent class.

```python
class Bird:
   
    def intro(self):
        print("There are many types of birds.")
 
    def flight(self):
        print("Most of the birds can fly but some cannot.")
 
class sparrow(Bird):
   
    def flight(self):
        print("Sparrows can fly.")
 
class ostrich(Bird):
 
    def flight(self):
        print("Ostriches cannot fly.")
 
obj_bird = Bird()
obj_spr = sparrow()
obj_ost = ostrich()
 
obj_bird.intro()
obj_bird.flight()
 
obj_spr.intro()
obj_spr.flight()
 
obj_ost.intro()
obj_ost.flight()
```
```python
# Output
There are many types of birds.
Most of the birds can fly but some cannot.
There are many types of birds.
Sparrows can fly.
There are many types of birds.
Ostriches cannot fly.
```

## Encapsulation
Encapsulation is one of the fundamental concepts in object-oriented programming (OOP). It describes the idea of wrapping data and the methods that work on data within one unit. This puts restrictions on accessing variables and methods directly and can prevent the accidental modification of data. To prevent accidental change, an object’s variable can only be changed by an object’s method. Those types of variables are known as private variables.

A class is an example of encapsulation as it encapsulates all the data that is member functions, variables, etc.

**Encapsulation in Python**

In the above example, we have created the c variable as the private attribute. We cannot even access this attribute directly and can’t even change its value.

```python
# Python program to
# demonstrate private members
# "__" double underscore represents private attribute. 
# Private attributes start with "__".
 
# Creating a Base class
class Base:
    def __init__(self):
        self.a = "GeeksforGeeks"
        self.__c = "GeeksforGeeks"
 
# Creating a derived class
class Derived(Base):
    def __init__(self):
 
        # Calling constructor of
        # Base class
        Base.__init__(self)
        print("Calling private member of base class: ")
        print(self.__c)
 
 
# Driver code
obj1 = Base()
print(obj1.a)
 
# Uncommenting print(obj1.c) will
# raise an AttributeError
 
# Uncommenting obj2 = Derived() will
# also raise an AtrributeError as
# private member of base class
# is called inside derived class
```
```python
# Output
GeeksforGeeks
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
- https://www.testgorilla.com/blog/python-oops-interview-questions/
- https://www.programiz.com/article/python-self-why