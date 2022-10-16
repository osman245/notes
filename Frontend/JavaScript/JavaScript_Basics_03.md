# Objects and Object Constructors

    In JavaScript there are multiple ways to do things. Many languages force you into using specific patterns and data structures in your code, but that is not true in JavaScript.

Thus when buliding more and complex code, you need to be careful that your choosing appriopriate code to build on.
The patterns we’ll be covering in this series are:

- Plain Old JavaScript Objects and Object Constructors
- Factory Functions and the Module Pattern
- Classes
- ES6 Modules

### To define objects, it most cases its best to use object literals

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
