# Table of Contents
- [Table of Contents](#table-of-contents)
    - [What are the possible ways to create objects in JavaScript?](#what-are-the-possible-ways-to-create-objects-in-javascript)
    - [What is a prototype chain?](#what-is-a-prototype-chain)
    - [What is the difference between Call, Apply and Bind?](#what-is-the-difference-between-call-apply-and-bind)
    - [What is JSON and its common operations?](#what-is-json-and-its-common-operations)
    - [What is the purpose of the array slice method?](#what-is-the-purpose-of-the-array-slice-method)
    - [What is the purpose of the array splice method?](#what-is-the-purpose-of-the-array-splice-method)
    - [What is the difference between slice and splice?](#what-is-the-difference-between-slice-and-splice)
    - [How do you compare Object and Map?](#how-do-you-compare-object-and-map)
    - [What is the difference between == and === operators?](#what-is-the-difference-between--and--operators)
    - [What are lambda expressions or arrow functions?](#what-are-lambda-expressions-or-arrow-functions)
    - [What is a first class function?](#what-is-a-first-class-function)
    - [What is a first order function?](#what-is-a-first-order-function)
    - [What is a higher order function?](#what-is-a-higher-order-function)
    - [What is a unary function?](#what-is-a-unary-function)
    - [What is the currying function?](#what-is-the-currying-function)
    - [What is a pure function?](#what-is-a-pure-function)
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

---

### What is the difference between Call, Apply and Bind?

The difference between Call, Apply and Bind can be explained with below examples:

**Call**: The call() method invokes a function with a given `this` value and arguments provided one by one

```js
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.call(employee1, "Hello", "How are you?"); // Hello John Rodson, How are you?
invite.call(employee2, "Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

**Apply**: Invokes the function with a given `this` value and allows you to pass in arguments as an array
```js
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

invite.apply(employee1, ["Hello", "How are you?"]); // Hello John Rodson, How are you?
invite.apply(employee2, ["Hello", "How are you?"]); // Hello Jimmy Baily, How are you?
```

**Bind**: returns a new function, allowing you to pass any number of arguments
```js
var employee1 = { firstName: "John", lastName: "Rodson" };
var employee2 = { firstName: "Jimmy", lastName: "Baily" };

function invite(greeting1, greeting2) {
  console.log(
    greeting1 + " " + this.firstName + " " + this.lastName + ", " + greeting2
  );
}

var inviteEmployee1 = invite.bind(employee1);
var inviteEmployee2 = invite.bind(employee2);
inviteEmployee1("Hello", "How are you?"); // Hello John Rodson, How are you?
inviteEmployee2("Hello", "How are you?"); // Hello Jimmy Baily, How are you?
```

Call and Apply are pretty much interchangeable. Both execute the current function immediately. You need to decide whether it’s easier to send in an array or a comma separated list of arguments. You can remember by treating Call is for **comma** (separated list) and Apply is for **Array**.  

Bind creates a new function that will have this set to the first parameter passed to bind().

---

### What is JSON and its common operations?

**JSON** is a text-based data format following JavaScript object syntax, which was popularized by `Douglas Crockford`. It is useful when you want to transmit data across a network. It is basically just a text file with an extension of .json, and a MIME type of application/json

**Parsing**: Converting a string to a native object
```js
JSON.parse(text);
```

**Stringification**: Converting a native object to a string so that it can be transmitted across the network
```js
JSON.stringify(object);
```

---

### What is the purpose of the array slice method?

The **slice()** method returns the selected elements in an array as a new array object. It selects the elements starting at the given start argument, and ends at the given optional end argument without including the last element. If you omit the second argument then it selects till the end of the array. This method can also accept negative index which counts back from the end of the array.

Some of the examples of this method are,
```js
let arrayIntegers = [1, 2, 3, 4, 5];
let arrayIntegers1 = arrayIntegers.slice(0, 2); // returns [1,2]
let arrayIntegers2 = arrayIntegers.slice(2, 3); // returns [3]
let arrayIntegers3 = arrayIntegers.slice(4); //returns [5]
let arrayIntegers4 = arrayIntegers.slice(-3, -1); //returns [3, 4]
```

**Note**: Slice method doesn't mutate the original array but it returns the subset as a new array.

---

### What is the purpose of the array splice method?

The **splice()** method adds/removes items to/from an array, and then returns the removed item. The first argument specifies the array position/index for insertion or deletion whereas the optional second argument indicates the number of elements to be deleted. Each additional argument is added to the array.

Some of the examples of this method are:

```js
let arrayIntegersOriginal1 = [1, 2, 3, 4, 5];
let arrayIntegersOriginal2 = [1, 2, 3, 4, 5];
let arrayIntegersOriginal3 = [1, 2, 3, 4, 5];

let arrayIntegers1 = arrayIntegersOriginal1.splice(0, 2); // returns [1, 2]; original array: [3, 4, 5]
let arrayIntegers2 = arrayIntegersOriginal2.splice(3); // returns [4, 5]; original array: [1, 2, 3]
let arrayIntegers3 = arrayIntegersOriginal3.splice(3, 1, "a", "b", "c"); //returns [4]; original array: [1, 2, 3, "a", "b", "c", 5]
```
**Note:** Splice method modifies the original array and returns the deleted array.

---

### What is the difference between slice and splice?

Some of the major differences in a tabular form:
| Slice                                        | Splice                                       |
| -------------------------------------------- | -------------------------------------------- |
| Doesn't modify the original array(immutable) | Modifies the original array(mutable)         |
| Returns the subset of original array         | Returns the deleted elements as array        |
| Used to pick the elements from array         | Used to insert/delete elements to/from array |

---

### How do you compare Object and Map?

**Objects** are similar to **Maps** in that both let you set keys to values, retrieve those values, delete keys, and detect whether something is stored at a key. Due to this reason, Objects have been used as Maps historically. But there are important differences that make using a Map preferable in certain cases:

1. The keys of an Object can be Strings and Symbols, whereas they can be any value for a Map, including functions, objects, and any primitive type.

2. The keys in a Map are ordered while keys added to Object are not. Thus, when iterating over it, a Map object returns keys in the order of insertion.

3. You can get the size of a Map easily with the size property, while the number of properties in an Object must be determined manually.

4. A Map is an iterable and can thus be directly iterated, whereas iterating over an Object requires obtaining its keys in some fashion and iterating over them.

5. An Object has a prototype, so there are default keys in an object that could collide with your keys if you're not careful. As of ES5 this can be bypassed by creating an object(which can be called a map) using `Object.create(null)`, but this practice is seldom done.

6. A Map may perform better in scenarios involving frequent addition and removal of key pairs.

---

### What is the difference between == and === operators?

JavaScript provides both strict(===, !==) and type-converting(==, !=) equality comparison. The strict operators take type of variable in consideration, while non-strict operators make type correction/conversion based upon values of variables. The strict operators follow the below conditions for different types,

1. Two strings are strictly equal when they have the same sequence of characters, same length, and same characters in corresponding positions.
2. Two numbers are strictly equal when they are numerically equal, i.e., having the same number value. There are two special cases in this,
     1. NaN is not equal to anything, including NaN.
     2. Positive and negative zeros are equal to one another.
3. Two Boolean operands are strictly equal if both are true or both are false.
4. Two objects are strictly equal if they refer to the same Object.
5. Null and Undefined types are not equal with ===, but equal with == . i.e, `null===undefined --> false`, but `null==undefined --> true`

Some of the example which covers the above cases:
```js
0 == false   // true
0 === false  // false
1 == "1"     // true
1 === "1"    // false
null == undefined // true
null === undefined // false
'0' == false // true
'0' === false // false
NaN == NaN or NaN === NaN // false
[]==[] or []===[] //false, refer different objects in memory
{}=={} or {}==={} //false, refer different objects in memory
```

---

### What are lambda expressions or arrow functions?

An arrow function is a shorter/concise syntax for a function expression and does not have its own **this, arguments, super, or new.target**. These functions are best suited for non-method functions, and they cannot be used as constructors.

Some of the examples of arrow functions are listed as below,
```js
const arrowFunc1 = (a, b) => a + b; // Multiple parameters
const arrowFunc2 = a => a * 10; // Single parameter
const arrowFunc3 = () => {} // no parameters
```

---

### What is a first class function?

In Javascript, functions are first class objects. First-class functions means when functions in that language are treated like any other variable.

For example, in such a language, a function can be passed as an argument to other functions, can be returned by another function and can be assigned as a value to a variable. For example, in the below example, handler functions assigned to a listener

```js
const handler = () => console.log("This is a click handler function");
document.addEventListener("click", handler);
```

---

### What is a first order function?

A first-order function is a function that doesn’t accept another function as an argument and doesn’t return a function as its return value.

```js
const firstOrder = () => console.log("I am a first order function!");
```

---

### What is a higher order function?

A higher-order function is a function that accepts another function as an argument or returns a function as a return value or both. The syntactic structure of higher order function will be as follows,

```js
const firstOrderFunc = () => console.log("Hello, I am a First order function");
const higherOrder = (ReturnFirstOrderFunc) => ReturnFirstOrderFunc();
higherOrder(firstOrderFunc);
```
You can also call the function which you are passing to higher order function as callback function.

The higher order function is helpful to write the modular and reusable code.

---

### What is a unary function?

A unary function (i.e. monadic) is a function that accepts exactly one argument. It stands for a single argument accepted by a function.

Let us take an example of unary function,

```js
const unaryFunction = (a) => console.log(a + 10); // Add 10 to the given argument and display the value
```

---

### What is the currying function?

Currying is the process of taking a function with multiple arguments and turning it into a sequence of functions each with only a single argument. Currying is named after a mathematician **Haskell Curry**. By applying currying, an n-ary function turns into a unary function.

Let's take an example of n-ary function and how it turns into a currying function,

```js
const multiArgFunction = (a, b, c) => a + b + c;
console.log(multiArgFunction(1, 2, 3)); // 6

const curryUnaryFunction = (a) => (b) => (c) => a + b + c;
curryUnaryFunction(1); // returns a function: b => c =>  1 + b + c
curryUnaryFunction(1)(2); // returns a function: c => 3 + c
curryUnaryFunction(1)(2)(3); // returns the number 6
```

Curried functions are great to improve **code reusability** and **functional composition**.

---

### What is a pure function?

A **Pure function** is a function where the return value is only determined by its arguments without any side effects. i.e, If you call a function with the same arguments 'n' number of times and 'n' number of places in the application then it will always return the same value.

Let's take an example to see the difference between pure and impure functions,

```js
//Impure
let numberArray = [];
const impureAddNumber = (number) => numberArray.push(number);
//Pure
const pureAddNumber = (number) => (argNumberArray) =>
  argNumberArray.concat([number]);

//Display the results
console.log(impureAddNumber(6)); // returns 1
console.log(numberArray); // returns [6]
console.log(pureAddNumber(7)(numberArray)); // returns [6, 7]
console.log(numberArray); // returns [6]
```

As per the above code snippets, the **Push** function is impure itself by altering the array and returning a push number index independent of the parameter value, whereas **Concat** on the other hand takes the array and concatenates it with the other array producing a whole new array without side effects. Also, the return value is a concatenation of the previous array.

Remember that Pure functions are important as they simplify unit testing without any side effects and no need for dependency injection. They also avoid tight coupling and make it harder to break your application by not having any side effects. These principles are coming together with the **Immutability** concept of ES6: giving preference to **const** over **let** usage.


---


---

## References
   - https://github.com/sudheerj/javascript-interview-questions
   - https://github.com/yangshun/top-javascript-interview-questions
    