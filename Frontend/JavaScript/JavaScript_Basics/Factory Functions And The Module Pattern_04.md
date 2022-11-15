# Factory Functions And The Module Pattern_04

- Factory functions are like constructors but they dont use the new keyword to create new objects. They set up and return the new object when you call the function. An example of this would be ..

```
const personFactory = (name, age) => {
  const sayHello = () => console.log('hello!');
  return { name, age, sayHello };
};

const jeff = personFactory('jeff', 27);

console.log(jeff.name); // 'jeff'

jeff.sayHello(); // calls the function and logs 'hello!'

```

vs using an object constructor

```
const personFactory = function(name,age) {
this.name = name;
this.age = age;
};

const jeff = new personFactory('jeff',27);
```

- Object Shorthand:(in 2015)
  return {name: name, age: age, sayHello: sayHello};

- But now we can do, like we did in the prev factory function return code bc those obj properties and variables you are referring has the exact same name..
  return {name, age, sayHello};

- console.log(name, color, number, food);//logs four variables
- console.log({name, color, number, food}); // logs like its an object

### Scope and Closure

- Scope == means what variables I have access to
- this == context
  this by default means the window object...

- window.object == root scope

```
var a = 1;
//parent scope
function foo() {
//child scope
var b = 2;
}
foo();
console.log(b);

```

- window.object == root scope thus if i do window.a I get 1. if i do a i get 1 aswell

**scope conflict..not illegal but conflict**

```
var a = 1;
//parent scope
function foo() {
//child scope
var a = 2;
}

foo();
console.log(b);
```

//get back to this example, its a bit confusing...
**pecuilar example in a this/scope context**

```
- var nav = document.querySelector('.nav'); // <nav class="nav">
  var toggleNav = function () {
  console.log(this); // <nav> element
  setTimeout(function () {
  console.log(this); // [object Window]
  }, 1000);
  };
  nav.addEventListener('click', toggleNav, false);
```

- So what’s happened here? We’ve created new scope which is not invoked from our event handler, so it defaults to the window Object as expected. There are several things we can do if we want to access the proper this value which isn’t affected by the new scope. You might have seen this before, where we can cache a reference to the this value using a that variable and refer to the lexical binding:

```
var nav = document.querySelector('.nav'); // <nav class="nav">
var toggleNav = function () {
  var that = this;
  console.log(that); // <nav> element
  setTimeout(function () {
    console.log(that); // <nav> element
  }, 1000);
};
nav.addEventListener('click', toggleNav, false);
```

- problem solved

### Changing scope with .call(), .apply() and .bind()

```
var links = document.querySelectorAll('nav li');
for (var i = 0; i < links.length; i++) {
  console.log(this); // [object Window]
}
```

- In this code the this value doesnt refer our elements

- We can use call and apply methods to bind the correct this value..

```

var links = document.querySelectorAll('nav li');
for (var i = 0; i < links.length; i++) {
  (function () {
    console.log(this);
  }).call(links[i]);
}

```

- It’s important to remember that using .call() or .apply() actually invokes your function, so instead of doing this:

- myFunction(); // Invoke myFunction
- myFunction.call(scope); // Invoke myFunction

- call and apply are like the upgraded version of bind, bind just gives values before its called while the later gives values and invokes the function

### Private Variables and Functions

```
const counterCreator = () => {
  let count = 0;
  return () => {
    console.log(count);
    count++;
  };
};

const counter = counterCreator();

counter(); // 0
counter(); // 1
counter(); // 2
counter(); // 3

```

- In this scenario the variable counter is a **closure** because we cant accesss the variable itself, we and only increment and console.log it..

- Closures allow us to crate private variables and functions.

```
onst Player = (name, level) => {
  let health = level * 2;
  const getLevel = () => level;
  const getName  = () => name;
  const die = () => {
    // uh oh
  };
  const damage = x => {
    health -= x;
    if (health <= 0) {
      die();
    }
  };
  const attack = enemy => {
    if (level < enemy.getLevel()) {
      damage(1);
      console.log(`${enemy.getName()} has damaged ${name}`);
    }
    if (level >= enemy.getLevel()) {
      enemy.damage(1);
      console.log(`${name} has damaged ${enemy.getName()}`);
    }
  };
  return {attack, damage, getLevel, getName};
};

const jimmie = Player('jim', 10);
const badGuy = Player('jeff', 5);
jimmie.attack(badGuy);

```

- In this scenario we only have access to the methods and variables in the return brackets
- THis we cant do jimmie.die() or we will get an error

Instead of applying prototypes and inheritance we can do this..

```
const Person = (name) => {
const sayName = () => console.log(`my name is ${name}`);
return {sayName};
}

const Nerd = (name) => {
// simply create a person and pull out the sayName function with destructuring assignment syntax!
const {sayName} = Person(name);
const doSomethingNerdy = () => console.log('nerd stuff');
return {sayName, doSomethingNerdy};
}

const jeff = Nerd('jeff');

jeff.sayName(); //my name is jeff
jeff.doSomethingNerdy(); // nerd stuff
```

- This is a great way to lump all of another object to one object..
- we can also use Object.assign for that aswell
  e.g)
  const Nerd = (name) => {
  const prototype = Person(name);
  const doSomethingNerdy = () => console.log('nerd stuff');
  return Object.assign({}, prototype, {doSomethingNerdy});
  }

- Describe common bugs you might run into using constructors.

- Write a factory method that returns an object.
  const person = (name,age) => {
  const sayName = () => {
  console.log(`hello my name is ${name} `)
  }
  return {name,age,sayName}
  }

- Explain how scope works in JavaScript (bonus points if you can point out what ES6 changed!).
  theres a global scope for code that all can reach, and local scope for only those that can reach locally.
- Explain what Closure is and how it impacts private functions & variables.
  closure makes variables unaccessible to the client to manipulate, their only given certain abilities at the owners risk.

- Describe how private functions & variables are useful.
- Use inheritance in objects using the factory pattern.
  const person = (name,age) => {
  const sayName = () => {
  console.log(`hello my name is ${name} `)
  }
  return {name,age,sayName}
  }

- Explain the module pattern.
  Quick sidenote: ES6 introduced a new feature in JavaScript called ‘modules’. These are essentially a syntax for importing and exporting code between different JavaScript files. They’re very powerful and we WILL be covering them later. They are not, however, what we’re talking about here.

- Describe IIFE. What does it stand for?
  invokes a function immediately.
- Briefly explain namespacing and how it’s useful.

### NameSpacing

- A useful side-effect of encapsulating the inner workings of our programs into objects is namespacing. Namespacing is a technique that is used to avoid naming collisions in our programs. For example, it’s easy to imagine scenarios where you could write multiple functions with the same name. In our calculator example, what if we had a function that added things to our HTML display, and a function that added numbers and operators to our stack as the users input them? It is conceivable that we would want to call all three of these functions add which, of course, would cause trouble in our program. If all of them were nicely encapsulated inside of an object, then we would have no trouble: calculator.add(), displayController.add(), operatorStack.add().
