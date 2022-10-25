# Objects and Object Constructors

In JavaScript there are multiple ways to do things. Many languages force you into using specific patterns and data structures in your code, but that is not true in JavaScript.

Thus when buliding more and complex code, you need to be careful that your choosing appriopriate code to build on.
The patterns we’ll be covering in this series are:

- Plain Old JavaScript Objects and Object Constructors
- Factory Functions and the Module Pattern
- Classes
- ES6 Modules

### To define objects, in most cases its best to use object literals

E.g)

```
const myObject = {
property: 'Value!',
otherProperty: 77,
"obnoxious property": function() {
// do stuff!
}
}
```

- There is also two ways to get information out of an object, dot notation and bracket notation.
  dot notation: myObject.property
  bracket notation: myObject['property']

### Objects as a Design Pattern

- **Object literals** are a great way to organize info. Better then having each property stored in its own variable...

- When you have a specific type of object that you need to duplicate like our player or inventory items, a better way to create them is using an **object constructor**, which is a function that looks like this:

```
function Player(name, marker) {
  this.name = name
  this.marker = marker
  }
```

- You can call this by using the new keyword...
  `const player = new Player('warsame','X');`
- Note: It is almost always best to return things rather than putting console.log() directly into the function. In this case, return the info string and log it after the function has been called:

### Exercise

- Write a constructor for making “Book” objects. We will revisit this in the project at the end of this lesson. Your book objects should have the book’s title, author, the number of pages, and whether or not you have read the book.

**Ans**

```
function theHobbit(title,author,pgnum,readBook) {
 this.title = title;
 this.author = author;
 this.pgnum = pgnum;
this.readBook = readBook;
this.info = function() {
}

}


```

### ProtoTypes

- Every JavaScript function has a prototype property
- All objects in JavaScript have a prototype. A prototype is another object your object inherits from. Giving access to all its methods and properties..
- prototype property is not enumerable; it isn’t accessible in loops
- All objects created with object literals and with the Object constructor inherits from Object.prototype.
- "**proto**" pseudotype property on browser to give you access to an objects prototype property
- If your using constructors to make your objects, its best to define the functions of the prototype of that object outside the constructor, so we dont create thousands of objects whenever we create a new object.
- When an object looks for a property it looks at its properties then its object prototype properties(father,grandfather)...This in essence is the prototype chain

```

function Student(name, grade) {
this.name = name
this.grade = grade
}

Student.prototype.sayName = function() {
console.log(this.name)
}
Student.prototype.goToProm = function() {
console.log("Eh.. go to prom?")
}

```

- Although, at the moment , the recommended way of setting the prototype of an object is to use Object.Create

```

EighthGrader.prototype = Object.create(Student.prototype)

const carl = new EighthGrader("carl")
carl.sayName() // console.logs "carl"
carl.grade // 8

```

`EighthGrader.prototype = Student.prototype` **never do this,can cause issues when you want to edit things in the future**

### Ways to set prototype...

```
let animal = {
  eats: true
};
let rabbit = {
  jumps: true
};

rabbit.__proto__ = animal;

```

- if we seek to use a rabbit property, and its not found there, it will look at its prototype.

- **note** **proto** is a historical getter/setter for [[Prototype]],not the prototype itself

- e **proto** property is a bit outdated. It exists for historical reasons, modern JavaScript suggests that we should use Object.getPrototypeOf/Object.setPrototypeOf functions instead that get/set the prototype. We’ll also cover these functions later.

```

let user = {
  name: "John",
  surname: "Smith",

  set fullName(value) {
    [this.name, this.surname] = value.split(" ");
  },

  get fullName() {
    return `${this.name} ${this.surname}`;
  }
};

let admin = {
  __proto__: user,
  isAdmin: true
};

alert(admin.fullName); // John Smith (*)

// setter triggers!
admin.fullName = "Alice Cooper"; // (**)


```

- rabbit.hasOwnProperty can be used to figure out has the property already, ultimately knowing if the object prototype should be accessed
- Set and get are accessor properties can be used by using the functions name...

Write an object constructor and instantiate the object.

Describe what a prototype is and how it can be used.
Explain prototypal inheritance.
Understand the basic do’s and don’t’s of prototypical inheritance.
Explain what Object.create does
How does this behave in different situations?

## the "this" keyword, what makes it unique?

- Java explaination, instance of the current object

### JavaScript Explaination

- Context(value of 'this') of a function invocation.
- The language has 4 function invocation/execution
  **4**
- Function invocation: `alert('Hello World')` another example of th

  - function object is followed by an open parenthesis (, a comma separated list of arguments expressions and a close parenthesis ). For example parseInt('18').

- **important**: strictmode makes "this" keyword to be undefined.

- Method invocation: `console.log('hello world')`
  - a method is a function stored in a object...

```
const calc = {
  num: 0,
  increment() {
    console.log(this === calc); // => true
    this.num += 1;
    return this.num;
  }
};
// method invocation. this is calc
calc.increment(); // => 1
calc.increment(); // => 2

```

We need to use the bind method to bind functions...
if there not apart of the initial object..., but a property of a function we use bind..

- ## Constructor invocation: `new RegExp('\\d')`
- Indirect invocation: `alert.call(undefined, 'hello world')`
  - Indirect invocation is performed when a function is called using myFun.call() or myFun.apply() methods. myCall calls context for first arg, and uses the others..
- Bound Function: ` `
- Arrow Function: ` `

Write an object constructor and instantiate the object.

```
- function cool(x) {
  return x;
}

cool("a");
```

Describe what a prototype is and how it can be used.

- A prototype is a property you can get from ancestor objects.

Explain prototypal inheritance.

- when you cant find the property at your current object.. you search all your ancestor prototypes to see if its there...

Understand the basic do’s and don’t’s of prototypical inheritance.

- If you plan on creating several instances of an object, you create one prototype outside the object, to reduce redundancy..
- Explain what Object.create does
  How does this behave in different situations?
  a method that creates a new object, using this object as the prototype of the newly created object.
