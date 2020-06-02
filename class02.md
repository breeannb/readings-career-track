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


# In Class 02 Notes: 

 1. There are 3 different ways to make objects: 
    - Object Literals
    - Constructor Functions (the old way )
        - a function that we construct key value pairs, can add functions 
        - Mostly replaced by classes for multi-use objects 
    - Factory Functions
        - useful when we want to have many objects 
    - Classes 
        - create a new class
        - has a constructor 
        - can add methods 
        - use it by calling new and applying what you need to the constructor 

2. Destructuring an Array 
    - const numbers = [1, 2, 3, 4, 5, 6];
    - const [one, two, three] = numbers 
        - this 'one' is grabbing the first value of the array, 'two' grabs the 2nd and so on
        - when you type in the console one the output will be 1, two will be 2 and so on 
    - const [,,,,five] = numbers
        - commas will skip the first 4 values so if you input five, it will output 5
    - const [anotherOne,,,anotherFour] = numbers 
        - output for anotherFour will be 4
        - output for anotherOne will be 1
    - if you try to do 7, it will be undefined as there is not a seventh value in the original numbers array 
    - can also have defaults: 
        - const [one, two, three, four = 100] = numbers; 
        - if undefined or not in the array, it will default to 100 instead 

3. Destructoring an Array of Objects 
    - Screen Shot 2020-06-02 at 10.26.05 AM 
    - const dogs = [{ name: 'spot' , age: 5 , weight: '20 lbs'}, { name: 'rover' , age: 10, weight: '}]

4. Rest 
    - const numbers = [1, 2, 3, 4, 5, 6]
    - const [one, two, ...rest] = numbers
        - you will get one and two, but rest will output the others that were not listed above, such as 3,4,5,6

5. Spread
    - const numbers = [1, 2, 3, 4, 5, 6]
    - const copyNumbers = [...numbers]
        - copyNumbers will output a copy this as well
    - const copyNumbers = [...numbers] to make a copy
        - can also do: prependedNumbers = [-2, -1, 0, ..numbers]
            - this says, take -2, -1 and 0 from the array, and then take the rest of the numbers in the other array 

6. Array(10)
    - will make an array of 10 empty spaces 
    - [...Array(10)] this will create undefined instead of empties that you can map over 

7. Destructuring with Objects 
    - const spot = { 
        name: 'spot',
        age: 5, 
        weight: '20lbs'
    }
    - const { name } = spot;
        - now you can type name in console and receive 'spot' as an output 
    - const { name, color = 'brown'} = 'spot'
        - this says grab name from spot, color from spot, but if color doesn't exist, default to brown 
    - const { name = 'rover', color = 'brown' } = spot 
        - name will output "spot"
        - color will output "brown" 
        - but original object will not change 
    - const { name: myDogsName } = spot;
        - name will output ""
        - myDogsName output "spot"

8. Object spreading 
    - const spot = { 
        name: 'spot',
        age: 5, 
        weight: '20lbs'
    }
    - const copySpot = { ...spot}
    - copySpot will output spot
    - copySpot.name = 'spotty' 
        - only the object that was copied will change 
    - const rover = { ...spot, name: 'rover'}
        - now this takes all the same things of spot except changes the name to rover 
    - const bing = { ...spot, name: `${bingosName} is a dog`}
        - const bingosName = 'bingo'
        - will output the name is 'bingo is a dog' 

9. Classes 
    - in House.js
        - class House { 
            //constructor is called when we call the new House
            constructor(location, bathrooms, bedrooms, floors) { 
                this.location = location; //this is also called self in other languages 
                this.bathrooms = bathrooms;
                this.bedrooms = bedrooms; 
                this.floors = floors; 
            }
        }

        module.exporsts = House; 

    - in House.test.js <- this needs to be capitalized if we're using a class
        - const House = require('./House');

        - describe('House class', () => {
            it('has a location, bathrooms, bedrooms, floors', () => {
                const house = new House('Portland', 1, 2, 1);

                expect(house.location).toEqual('Portland');
                expect(house.bathrooms).toEqual(1);
                expect(house.bedrooms).toEqual(2);
                expect(house.floors).toEqual(1);
            });
        }); 

        - In terminal: npm run test: watch 