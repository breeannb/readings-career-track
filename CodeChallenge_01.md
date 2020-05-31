# Code Challenge 01 

## Objects 

### [Intializing Objects on MD](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Object_initializer)
*  Objects can be initialized using ```new Object```, ```Object.create()``` called initializer notation and is comma-delimited enclosed in curly braces.  
* Example: ```const object2 = { a: a, b: b, c: c }; ```
* Practice Sites: 
    * [Basics](https://tddbin.com/#?) 
    * [Computed Properties](https://tddbin.com/#?)

## Classes 

### [Inheritance](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
*  Each object has a property that holds a link to another object, which we call prototype, and that also has a prototype and so on until we reach ```null```. This series of links is a **prototype chain**. 

### [Classes](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)
*  Classes are 'special functions' with two components: class expressions and class declarations. 
### Practice Sites: 
* [Creation](https://tddbin.com/#?)
* [Statics](https://tddbin.com/#?)
* [Extends](https://tddbin.com/#?)

## Destructuring 

### [MDN Destructoring](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)
*  Destructoring makes it possible to unpackvalues from arrays, properties and distinct variables
* Practice Links: 
    * [Array Destructuring](https://tddbin.com/#?)
    * [String Destructuring](https://tddbin.com/#?)
    * [Object Destructuring](https://tddbin.com/#?)
    * [Destructuring with Defaults](https://tddbin.com/#?)
    * [Destructuring Function Parameters](https://tddbin.com/#?)
    * [Destructuring with Alias](https://tddbin.com/#?)

## Rest 
### [Rest MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/rest_parameters)
* Rest Parameter allows us to represent an indefinite number of arguments as an array and can be prefixed with ```...``` which will cause all remaining arguments to be placed within 'standard' Javascript array
* Example: 
 ```function f(a, b, ...theArgs) { // ... }```
* Practice Links:   
    * [Rest as a Parameter](https://tddbin.com/#?)
    * [Rest while Destructuring](https://tddbin.com/#?)

## Spread

### [MDN Spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)
*  Allows an iterable, such as an array or string, to be expanded to places where zero or more arguments and elements are expected.  
* Example:  

    * For function calls:
        ```myFunction(...iterableObj);```
    * For array literals or strings:
        ```[...iterableObj, '4', 'five', 6];```
    * For object literals (new in ECMAScript 2018):
    ```let objClone = { ...obj };```
* Practice Links: 
    * [Array Spread](https://tddbin.com/#?)

## Function Defaults 

### [MDN Function Defaults](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)
*  Function Default parameters allow named parameters to be initialized with default values if no value or ```undefined``` is passed. They default to undefined, but is useful to set a different default value
* Example: ```function [name]([param1[ = defaultValue1 ][, ..., paramN[defaultValueN ]]]) { statements} ```
* Practice Links: 
    *   [Function Defaults](https://tddbin.com/#?) 
