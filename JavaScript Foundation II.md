

### Syntactical Sugar

A term where a method or a code does the same thing but the code is done more prettier;

### Execution Context

Every time we run code in the JS engine a global execution context is created. all global code that aren't inside of the function is executed inside the global execution context.

### Lexical Environment

Lexical means where the code is written and functions that are declared in the global execution context which is in the window object. Every time we have a function it creates a new function and inside of that function we could do different things and communicate with each other.

- Lexical Scope - available data + variables where the function is defined (it determines the available of the data).

### Hoisting

the behavior moving the variables or function to the top of the respective environment.  If a variable is declared and initialized after using it, the value will be undefined.

```js

console.log('teddy')
var teddy = 'teddy';
//undefine
```



### Function Invocation

The term when we call the function that was declared at top



### Function Scope

are variables that are declared inside of a function. However if we declare variables inside of loops and if else they could still be accessed outside and are put into global scope.

**Block Scope**

Variables that are declared inside of opening and close brackets. using const and let will make our variables scope to the brackets  even if we use if else and loops.

### IIFE

**Immediately Invoke Function Expression**. An anonymous function that immediately calls itself.

```js
(function() {
	console.log('hello');
})()
```

### call()

A method that let us use  to copy an object method to another object. It lets another object borrow the function that's from another object. It has two  parameters (obj, values)

```javascript
const wizard = {	
health: 50,
heal(){
	return this.health += 100
 }
}	
const soldier = {
 health: 10
}

wizard.heal.call(soldier)
// { health: 110 }

```

### apply()

Same as the method call() but the only thing difference is that the last parameters are in an array.

```javascript
const wizard = {	
health: 50,
heal(num1, num2){
	return this.health += num1 + num2
 }
}	
const soldier = {
 health: 10
}

wizard.heal.apply(soldier, [50,100])
// { health: 160 }
```

### bind()

Works the same like call() but it returns us a method to call afterwards. Bind allows us to borrow a function from an object that is useful for reusable.

```javascript
const wizard = {	
health: 50,
heal(num1, num2){
	return this.health += num1 + num2
 }
}	
const soldier = {
 health: 10
}

const healSoldier = wizard.heal.bind(soldier, 50,150)
healSoldier();
// { health: 210 }
```



### function currying

 lets you create a new **function** out of an existing **function** by fixing some parameters.

```javascript
function multiply(a, b){
return a*b
}

let multiplyByTwo = multiply.bind(this,2);
console.log(multiplyByTwo(2));
```



**Context vs Scope**

Scope refers to the visibility of the variables where it was declared 

Context - refers to the value of the this object. Which reference to the object that owns that current execution code



[Link]: https://stackoverflow.com/questions/4616694/what-is-event-bubbling-and-capturing

**Event capturing**

When you use event capturing

```js
               | |
---------------| |-----------------
| element1     | |                |
|   -----------| |-----------     |
|   |element2  \ /          |     |
|   -------------------------     |
|        Event CAPTURING          |
-----------------------------------
```

the event handler of element1 fires first, the event handler of element2 fires last.

**Event bubbling**

When you use event bubbling

```js
               / \
---------------| |-----------------
| element1     | |                |
|   -----------| |-----------     |
|   |element2  | |          |     |
|   -------------------------     |
|        Event BUBBLING           |
-----------------------------------
```

the event handler of element2 fires first, the event handler of element1 fires last.