# Backend Development Notes

## Sources
    - s1. Node Design Patterns, 2nd Edition, Mario Casciaro, Luciano Mammino

## Programming

- Programming >  Principles
  - DRY - Don't Repeat Yourself
  
## Database

* SQL

## Javascript

* ES6

Const - Allows user to make constant variables. 
> const does not indicate that the assigned value will be constant, but that the binding with the value is constant. - s1
```javascript
const x = {};
x.name = 'John';
console.log(x.name)
>>  'John'
```

Let - 
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

Arrow Functions - ES6 syntax for writing functions
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

Classes
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


Node
Features
**Module**
> Node.js uses the concept of a module as a fundamental means to structure the code of a program. . It is the building block for creating applications and reusable libraries called packages (a package is also frequently referred to as a module since, usually, it has one single module as an entry point).  - s1


Vanilla
Concepts
Lexical Scoping - defines how variable names are resolved in nested functions: inner functions contain the scope of parent functions even if the parent function has returned. - https://stackoverflow.com/questions/1047454/what-is-lexical-scope

Features

