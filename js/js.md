# Table of Contents
- [Table of Contents](#table-of-contents)
    - [What are the possible ways to create objects in JavaScript?](#what-are-the-possible-ways-to-create-objects-in-javascript)
    - [What is a prototype chain?](#what-is-a-prototype-chain)
    - [What is the difference between Call, Apply and Bind?](#what-is-the-difference-between-call-apply-and-bind)
  - [References](#references)


### What are the possible ways to create objects in JavaScript?

There are many ways to create objects in javascript as mentioned below:

1. **Object literal syntax**:  

The object literal syntax (or object initializer), is a comma-separated set of name-value pairs wrapped in curly braces.

```js
var object = {
     name: "John",
     age: 33
};
```  
Object literal property values can be of any data type, including array, function, and nested object.

2. **Object constructor**:  

The simplest way to create an empty object is using the `Object` constructor.
```js
var object = new Object();
```
The `Object()` is a built-in constructor function so "new" keyword is not required. The above code snippet can be re-written as:
```js
var object = Object();
```

3. **Object's create method**:  

The `create` method of Object is used to create a new object by passing the specified prototype object and properties  
as arguments, i.e., this pattern is helpful to create new objects based on existing objects. The second argument is  
optional and it is used to create properties on a newly created object.  

The following code creates a new empty object whose prototype is null.
```js
var object = Object.create(null);
```

The following example creates an object along with additional new properties.
```js
let vehicle = {
  wheels: '4',
  fuelType: 'Gasoline',
  color: 'Green'
}
let carProps = {
  type: {
    value: 'Volkswagen'
  },
  model: {
    value: 'Golf'
  }
}

var car = Object.create(vehicle, carProps);
console.log(car);
```

4. **Function constructor**:  

In this approach, create any function and apply the new operator to create object instances.

```js
function Person(name) {
  this.name = name;
  this.age = 21;
}
var object = new Person("John");
```

5. **Function constructor with prototype**:  

This is similar to function constructor but it uses prototype for their properties and methods,
```js
function Person() {}
Person.prototype.name = "John";
var object = new Person();
```

This is equivalent to creating an instance with Object.create method with a function prototype and then calling  
that function with an instance and parameters as arguments.

```js
function func() {}

new func(x, y, z);
```

OR

```js
// Create a new instance using function prototype.
var newInstance = Object.create(func.prototype)

// Call the function
var result = func.call(newInstance, x, y, z),

// If the result is a non-null object then use it otherwise just use the new instance.
console.log(result && typeof result === 'object' ? result : newInstance);
```

6. **Object's assign method**:

The `Object.assign` method is used to copy all the properties from one or more source objects and stores them  
into a target object.

The following code creates a new staff object by copying properties of his working company and the car he owns.

```js
const orgObject = { company: 'XYZ Corp'};
const carObject = { name: 'Toyota'};
const staff = Object.assign({}, orgObject, carObject);
```

7. **ES6 Class syntax**:  

ES6 introduces class feature to create objects.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
}

var object = new Person("John");
```

8. **Singleton pattern**":

A Singleton is an object which can only be instantiated one time. Repeated calls to its constructor return  
the same instance. This way one can ensure that they don't accidentally create multiple instances.

```js
var object = new (function () {
  this.name = "John";
})();
```

---

### What is a prototype chain?

**Prototype chaining** is used to build new types of objects based on existing ones. It is similar to inheritance in  
a class based language. i.e, When you create an object using a constructor function or a class, the created   
object inherits properties from a prototype object.

The prototype on object instance is available through **Object.getPrototypeOf(object)** or `__proto__` property  
whereas prototype on constructor function is available through **Object.prototype**.

![prototype-chain](images/prototype_chain.png)


### What is the difference between Call, Apply and Bind?

The difference between Call, Apply and Bind can be explained with below examples:


## References
   - https://github.com/sudheerj/javascript-interview-questions
   - https://github.com/yangshun/top-javascript-interview-questions
    