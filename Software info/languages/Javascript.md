### How does JS code runs???
When the Javascript engine runs your code it creates:

- a Global Execution context
- a Global M
- emory (also called Global Scope or Global Variable Environment)

Simply put, an execution context is an abstract concept of an environment where the Javascript code is evaluated and executed. Whenever any code is run in JavaScript, it’s run inside an execution context.

The Global Memory contains global variables and function declarations for later use.

Execution stack, also known as “calling stack” in other programming languages, is a stack with a LIFO (Last in, First out) structure, which is used to store all the execution context created during the code execution.

When the JavaScript engine first encounters your script, it creates a global execution context and pushes it to the current execution stack. Whenever the engine finds a function invocation, it creates a new execution context for that function and pushes it to the top of the stack.

The engine executes the function whose execution context is at the top of the stack. When this function completes, its execution stack is popped off from the stack, and the control reaches to the context below it in the current stack.

Let’s understand this with a code example below:

```javascript
let a = 'Hello World!';function first() {  
  console.log('Inside first function');  
  second();  
  console.log('Again inside first function');  
}function second() {  
  console.log('Inside second function');  
}first();  
console.log('Inside Global Execution Context');
```

![](https://miro.medium.com/v2/resize:fit:1500/1*ACtBy8CIepVTOSYcVwZ34Q.png)

An Execution Context Stack for the above code.

When the above code loads in the browser, the Javascript engine creates a global execution context and pushes it to the current execution stack. When a call to `first()` is encountered, the Javascript engines creates a new execution context for that function and pushes it to the top of the current execution stack.

When the `second()` function is called from within the `first()` function, the Javascript engine creates a new execution context for that function and pushes it to the top of the current execution stack. When the `second()` function finishes, its execution context is popped off from the current stack, and the control reaches to the execution context below it, that is the `first()` function execution context.

When the `first()` finishes, its execution stack is removed from the stack and control reaches to the global execution context. Once all the code is executed, the JavaScript engine removes the global execution context from the current stack.

### Primitive and Non-primitive data types

#### Primitive:
**1.** [**Number**](https://www.geeksforgeeks.org/javascript-numbers/)**:** Number data type in javascript can be used to hold decimal values as well as values without decimals.
**2.** [**String**](https://www.geeksforgeeks.org/javascript-strings/)**:** The string data type in javascript represents a sequence of characters that are surrounded by single or double quotes.
**3.** [**Undefined**](https://www.geeksforgeeks.org/javascript-undefined-property/)**:** The meaning of undefined is ‘value is not assigned’.
**4.** [**Boolean**](https://www.geeksforgeeks.org/javascript-boolean/)**:** The boolean data type can accept only two values i.e. true and false.
**5.** [**Null**](https://www.geeksforgeeks.org/null-in-javascript/)**:** This data type can hold only one possible value that is null.
**6.** [**BigInt**](https://www.geeksforgeeks.org/bigint-in-javascript/)**:** This data type can represent numbers greater than 253-1 which helps to perform operations on large numbers. The number is specified by writing ‘n’ at the end of the value
**7.** [**Symbol**](https://www.geeksforgeeks.org/javascript-symbol-method/)**:** This data type is used to create objects which will always be unique. these objects can be created using Symbol constructor.

#### Non-Primitive:
**1.** [**Object**](https://www.geeksforgeeks.org/javascript-objects/)**: An object** in Javascript is an entity having properties and methods. Everything is an object in javascript.
**2.** [**Array**](https://www.geeksforgeeks.org/arrays-in-javascript/)**:** With the help of an array, we can store more than one element under a single name.

### Value vs Reference 

Javascript has 5 data types that are passed by **_value_**: `Boolean`, `null`, `undefined`, `String`, and `Number`. We’ll call these **primitive types**.

Javascript has 3 data types that are passed by **_reference_**: `Array`, `Function`, and `Object`. These are all technically Objects, so we’ll refer to them collectively as **Objects**.

==Variables that are assigned a non-primitive value are given a== ==_reference_== ==to that value. That reference points to the object’s location in memory. The variables don’t actually contain the value.==

When there are no references to an object remaining, the Javascript engine can perform garbage collection. This just means that the programmer has lost all references to the object and can’t use the object any more, so the engine can go ahead and safely delete it from memory.
### Conditional branching: if, '?'

```javascript
let result = condition ? value1 : value2;
```

### Nullish coalescing operator '??'

As it treats `null` and `undefined` similarly, we’ll use a special term here, in this article. For brevity, we’ll say that a value is “defined” when it’s neither `null` nor `undefined`.

The result of `a ?? b` is:

- if `a` is defined, then `a`,
- if `a` isn’t defined, then `b`.
In other words, `??` returns the first argument if it’s not `null/undefined`. Otherwise, the second one.

We can rewrite `result = a ?? b` using the operators that we already know, like this:

``` javascript
result `=` `(`a `!==` `null` `&&` a `!==` `undefined``)` `?` a `:` b`;`
```

The important difference between them is that:

- `||` returns the first _truthy_ value.
- `??` returns the first _defined_ value.

### Arrow functions, the basics

```javascript
let sum = (a,b) => a + b;
same as
let sum = function (a,b)
{
return a+b
}
```



### Basic js built in functions
1. `map()`: The `map()` method creates a new array by applying a function to each element in the original array. It doesn't modify the original array.
    
```javascript
    const numbers = [1, 2, 3, 4, 5]; 
    const doubledNumbers = numbers.map((num) => num * 2);
     // doubledNumbers is now [2, 4, 6, 8, 10]
```

    
2. `find()`: The `find()` method returns the first element in an array that satisfies a provided testing function.
```javascript
const users = [   { id: 1, name: 'Alice' },   { id: 2, name: 'Bob' },   { id: 3, name: 'Charlie' }, ];  
const user = users.find((user) => user.id === 2); 
// user is { id: 2, name: 'Bob' }
```
    
3. `filter()`: The `filter()` method creates a new array with all elements that pass a provided testing function.
```javascript
const numbers = [1, 2, 3, 4, 5]; 
const evenNumbers = numbers.filter((num) => num % 2 === 0); // evenNumbers is now [2, 4]
```
    
4. `forEach()`: The `forEach()` method iterates over the elements of an array and executes a provided function for each element.
```javascript
const fruits = ['apple', 'banana', 'cherry'];
fruits.forEach((fruit) => console.log(fruit));
// Outputs: 'apple', 'banana', 'cherry'

```
    
5. `reduce()`: The `reduce()` method reduces an array to a single value by applying a function to each element and accumulating the result.
```javascript
const numbers = [1, 2, 3, 4, 5];
const sum = numbers.reduce((accumulator, current) => accumulator + current, 0);
// sum is 15

```
6. `Object.keys()`: This method returns an array of a given object's property names.
```javascript
const person = { name: 'John', age: 30, job: 'developer' };
const keys = Object.keys(person);
// keys is ['name', 'age', 'job']

```
7. `Object.values()`: This method returns an array of a given object's property values.
```javascript
const person = { name: 'John', age: 30, job: 'developer' };
const values = Object.values(person);
// values is ['John', 30, 'developer']

```