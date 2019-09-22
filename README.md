# Backend Development Notes

## Sources
    - s1. Node Design Patterns, 2nd Edition, Mario Casciaro, Luciano Mammino

## Programming

### Programming >  Principles

**DRY**
Don't Repeat Yourself
  
## Database

### SQL (Structured Query Language)

## Javascript

### JavaScript > Patterns

**Callback Pattern**
> In JavaScript, a callback is a function that is passed as an argument to another function and is invoked with the result when the operation completes. - s1
>  Callbacks are functions that are invoked to propagate the result of an operation and this is exactly what we need when dealing with asynchronous operations. They do replace the use of the return instruction that always executes synchronously. - s1
```javascript
function add(a, b, callback) {
 callback(a + b);
}
add(1, 2, result => console.log('Result: ' + result));
>> Result: 3
```

```javascript
const fs = require('fs');

function readFile(filename, callback) {
    // you pass readFile a file name, and it gives you a callback with the data as the first param when it gets it
    fs.readFile(filename, 'utf8', (err, data) => {
      callback(data);
 });
}

function createFileReader(filename) {
  const listeners = [];
  // The callback we are passing to readFile is a function definition with a param of value, and a body that calls each listener
  readFile(filename, value => {
    listeners.forEach(listener => {
      listener(value)
     });
  });
  return {
    onDataReady: listener => {
      // pushes onto the listeners array one or more function definitions, which are invoked when readFile returns data
      listeners.push(listener)
      listeners.push(() => console.log('The file has returned its data.'))
    }
  };
}

// returns an object with a property called 'onDataReady'. 
const reader1 = createFileReader('data.txt');

// calls the 'onDataReady' property with a function definition as a parameter. This function definition gets pushed onto the list of listeners. Each of these listeners is invoked when the readFile returns data
reader1.onDataReady(data => {
  console.log(data)
});

>> {data from data.txt}
>> The file has returned its data.
```

### Javascript > ES6

**Const**
* Allows user to make constant variables. 
> const does not indicate that the assigned value will be constant, but that the binding with the value is constant. - s1
```javascript
const x = {};
x.name = 'John';
console.log(x.name)
>>  'John'
```

**Template Literals**
> The main benefits are that template literal syntax can interpolate variables or expressions using ${expression}
inside the string (this is the reason why this syntax is called “template”) and that a single string can finally be easily written in multiple lines.  - s1
```javascript
const name = 'John';
const greeting = `Hi, my name is ${name}`;
console.log(greeting);
>>  Hi, my name is John
```

**Let**
> Historically, JavaScript only offered function scope and global scope to control the lifetime
and the visibility of a variable. ES2015 introduces the let keyword to declare variables that respect the block
scope - s1
```javascript
if (false) {
 let x = "hello";
}
console.log(x);
>>  ReferenceError: x is not defined 
```

**Arrow Functions**
* Updated syntax for writing functions
> But there is another important feature to know about arrow functions: arrow functions are
bound to their lexical scope. This means that inside an arrow function the value of this is
the same as in the parent block. - s1
```javascript
function Person(name) {
 this.name = name;
 this.species = 'person'
}

Person.prototype.greet = function() {
  console.log(this);
  return 'Hi ' + this.name;
};

Person.prototype.waitAndGreet = function() {
  setTimeout(function cb() {
    console.log(this);
    return 'Hi ' + this.name;
  }, 500)
};

Person.prototype.waitAndGreetTwo = function() {
  setTimeout(() => {
    console.log(this);
    return 'Hi ' + this.name;
  }, 500)
};

const person = new Person('John');
person.greet();
>> Person { name: 'John', species: 'person' }
>> 'Hi John'

person.waitAndGreet();
>> undefined
>> Timeout {
  _called: true,
  _idleTimeout: 500,
  
person.waitAndGreetTwo();  
>> undefined
>> Person { name: 'John', species: 'person' }
  
```

**Classes**
- super
- constructor
- class
- extends
- static
```javascript
class Person {
 constructor (name, surname, age) {
 this.name = name;
 this.surname = surname;
 this.age = age;
 }
 getFullName () {
 return this.name + ' ' + this.surname;
 }
 static older (person1, person2) {
 return (person1.age >= person2.age) ? person1 : person2;
 }
}

class PersonWithMiddlename extends Person {
 constructor (name, middlename, surname, age) {
 super(name, surname, age);
 this.middlename = middlename;
 }
 getFullName () {
   return this.name + ' ' + this.middlename + ' ' + this.surname;
 }
}

const person1 = new Person('John', 'Smith', 47);
const person3 = new PersonWithMiddlename('Juan', 'James', 'Smythe', 49);

person3.getFullName()
>> 'Juan James Smythe'

PersonWithMiddlename.older(person3, person1).name
>> Juan
```


**Enhanced object literals**
- get
- set
>  This
syntax offers a shorthand to assign variables and functions as members of the object, allows
us to define computed member names at creation time, and also handy setter and getter
methods. - s1
```javascript
const person = {
  name : 'George',
  surname : 'Boole',
  greet(x) {
    return `${x}, ${this.name}`;
  },
  get fullname () {
    return this.name + ' ' + this.surname;
  },
  set fullname (fullname) {
    let parts = fullname.split(' ');
    this.name = parts[0];
    this.surname = parts[1];
  }
};

console.log(person.fullname);
 >> "George Boole"
console.log(person.fullname = 'Alan Turing'); 
>> "Alan Turing"
console.log(person.name); 
>> "Alan"
person.greet('Howdy')
>> "Howdy, Alan"
```

### Javascript > Node

### Javascript > Node > Concepts

**Asynchronous vs. Synchronous**

* A synchronous callback
``` javascript
function add(a, b, callback) {
 callback(a + b);
}

console.log('before');
add(1, 2, result => console.log('Result: ' + result));
console.log('after');

>> before
>> Result: 3
>> after
```
* An asynchronous callback
``` javascript
function additionAsync(a, b, callback) {
 setTimeout(() => callback(a + b), 100);
}
console.log('before');
additionAsync(1, 2, result => console.log('Result: ' + result));
console.log('after');

>> before
>> after
>> Result: 3
```
> Since setTimeout() triggers an asynchronous operation, it will not wait for the callback to
be executed, but instead, it returns immediately, giving the control back to
additionAsync(), and then back to its caller. This property in Node.js is crucial, as it gives
control back to the event loop as soon as an asynchronous request is sent, thus allowing a
new event from the queue to be processed.

### Javascript > Node > Features

**module**
> Node.js uses the concept of a module as a fundamental means to structure the code of a program. . It is the building block for creating applications and reusable libraries called packages (a package is also frequently referred to as a module since, usually, it has one single module as an entry point).  - s1

**process.nextTick()**
>  which defers the execution of a function until the next pass of the event loop. Its functioning is very simple; it takes a callback as an argument and pushes it to the top of the event queue, in front of any pending I/O event, and returns immediately. The callback will then be invoked as soon as the event loop runs again. - s1
``` javascript
const fs = require('fs');

function readFile(filename, callback) {
    fs.readFile(filename, 'utf8', (err, data) => {
      process.nextTick(() => callback(data));
 });
}

readFile('data.txt', data => {
  console.log(data)
});
```

### Javascript > Vanilla
### Javascript > Vanilla > Concepts

** Lexical Scoping **
> defines how variable names are resolved in nested functions: inner functions contain the scope of parent functions even if the parent function has returned. - https://stackoverflow.com/questions/1047454/what-is-lexical-scope

**Closures**
> closure is the combination of a function and the lexical environment within which that function was declared.
> Closures are useful because they let you associate some data (the lexical environment) with a function that operates on that data. This has obvious parallels to object-oriented programming, where objects allow us to associate some data (the object's properties) with one or more methods. - https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures
> With closures, we can in fact reference the environment in which a function was created; we can always maintain the context in which the asynchronous operation was requested, no matter when or where its callback is invoked. - s1
```javascript
function makeFunc() {
  var name = 'Mozilla';
  function displayName() {
    console.log(name);
  }
  return displayName;
}

var myFunc = makeFunc();
myFunc();
>> Mozilla
```

### JavaScript > Vanilla > Features

**setTimeOut**
Can be used to simulate an asynchronous event
```javascript
setTimeout(function(){
  console.log('I waited'), 1000);
}
>> I waited
```
