# Class 02 Reading 

## Questions

1. Name 3 advantages to Test Driven Development
    * Fast feedback
    * further consideration of what you want the code to accomplish
    * esily identifiable errors
2. In what case would you need to use beforeEach() or afterEach() in a test suite?
    * beforeEach() - used when there is global state that needs to be used by other tests 
    * afterEach() - used for other tests 
3. What is one downside of Test Driven Development
    * If you haven't understood the problem you need to solve, writing tests most probably doesn't help.
4. What’s the primary difference between ES6 Classes and Constructor/Prototype Classes?
    * "The most important difference between class- and prototype-based inheritance is that a class defines a type which can be instantiated at runtime, whereas a prototype is itself an object instance." 
5. Name a use case for a static method
    * to create utility functions for an app
6. Write an example of a Higher Order function and describe the use case it solves
    * ``` function greaterThan(n) {```
    ```return function(m) { return m > n; };```
    ```}```
    ```var greaterThan10 = greaterThan(10);```
    ```console.log(greaterThan10(11));```
    ```// → true```
    * This was an example on a discussion thread in Eloquent Javascript that describes how to create functions that create new functions and to abstract over actions, and not just values. 

## Vocab Terms 

* **functional programming** - the process of building software by composing pure functions, avoiding shared state, mutable data, and side-effects. 
* **pure function** - a function given the same input, will always return the same output and produces no side effects.
* **higher-order function** - a function that takes another function as an argument or returns a function 
* **immutable state** - state that cannot be changed 
* **object** - a data type that has properites and methods, and may contain othr objects. 
* **object-oriented programming (OOP)** - a computer programming model that organizes software design around data, or objects, rather than functions and logic.
* **class** - a class is a blueprint for creating objects (a particular data structure), providing initial values for state (member variables or attributes), and implementations of behavior (member functions or methods)
* **prototype** - internal property of an object that can reference another object and contains common attributes/properities across all instances of the object 
* **super** - built in function used to call/refer to the Parent class without explicitly naming them. 
* **inheritance** - a mechanism where you can derive a class from another class for a hierarchy of classes that share a set of attributes and methods 
* **constructor** - a special method of a class or structure in object-oriented programming that initializes an object of that type
* **instance** -  is a specific realization of any object. An object may be varied in a number of ways. Each realized variation of that object is an instance. The creation of a realized instance is called instantiation.
* **context** - OOP enables us to work at the levels of a context (a set of related units) and of a single unit (that is, an object). 
* **this** - having various uses: 
    * In a method, this refers to the owner object.
    * Alone, this refers to the global object.
    * In a function, this refers to the global object.
    * In a function, in strict mode, this is undefined.
    * In an event, this refers to the element that received the event.
    * Methods like call(), and apply() can refer this to any object.
* **Test Driven Development (TDD)** - a software development process that relies on the repetition of a very short development cycle: requirements are turned into very specific test cases, then the code is improved so that the tests pass.
* **Jest** - a delightful JavaScript Testing Framework with a focus on simplicity that works with Babel, TypeScript, Node, React, Angular, Vue etc. 
* **Continuous Integration (CI)** - In software engineering, continuous integration is the practice of merging all developers' working copies to a shared mainline several times a day.
* **unit test** - a level of software testing where individual units/ components of a software are tested.

## Resources/Helpful Articles: 
1. https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0
2. https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-pure-function-d1c076bec976
3. https://medium.com/javascript-scene/higher-order-functions-composing-software-5365cf2cbe99
4. https://softwareengineering.stackexchange.com/questions/235558/what-is-state-mutable-state-and-immutable-state#:~:text=Immutable%20state%20is%20state%20that,object%20at%20the%20same%20time.
5. https://searchapparchitecture.techtarget.com/definition/object-oriented-programming-OOP
6. https://brilliant.org/wiki/classes-oop/
7. https://arvimal.blog/2016/07/01/inheritance-and-super-object-oriented-programming/#:~:text=super()%20helps%20to%20specifically,class%20without%20explicitly%20naming%20them.&text=In%20case%20you%20need%20to,parent%20class%2C%20use%20super().
8. https://stackify.com/oop-concept-inheritance/
9. https://whatis.techtarget.com/definition/instance#:~:text=An%20instance%2C%20in%20object%2Doriented,specific%20realization%20of%20any%20object.&text=The%20creation%20of%20a%20realized,an%20instantiation%20of%20a%20class.
10. http://www.complang.tuwien.ac.at/anton/euroforth/ef98/gassanenko98a.pdf
11. https://jestjs.io/
12. http://softwaretestingfundamentals.com/unit-testing/
13. https://dzone.com/articles/20-benefits-of-test-driven-development 
14. https://jestjs.io/docs/en/api#aftereachfn-timeout
15. https://subscription.packtpub.com/book/application_development/9781785880735/1/ch01lvl1sec12/disadvantages-of-tdd
16. https://www.toptal.com/javascript/es6-class-chaos-keeps-js-developer-up#:~:text=Prototypes%20vs.,Classes&text=A%20child%20of%20an%20ES6,t%20implemented%20on%20the%20child.
