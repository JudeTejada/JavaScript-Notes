### JavaScript types

1. Primitive Data Types

   - number
   - string
   - Boolean
   - undefined - The Absence of the definition
   - null - The Absence of the Value(NO VALUE)
   - Symbol

   The difference of undefined and null is that Null

2. Non -primitive

   - Objects {}
   - functions function()
   - arrays []

### Pass By Value

Copies **values** of the variables that you **pass** to a function into local variables. Any changes that you make to the local variables inside the function does not affect the arguments that you passed in.

```javascript
var a = 5;
var b = a;

b++
console.log(b)
// 6

```



### Pass By Reference

Function is called by directly **passing** the **reference**/address of the variable as the argument. Changing the argument inside the function affect the variable passed from outside the function. In **JavaScript** objects and arrays follows **pass by reference**.

```javascript
let obj1 = {name: 'Jude', email:'MyEmail@email.me'};
let obj2 = obj1;
obj2.email = 'newEmail@test.com';

console.log(obj1)
console.log(obj2);
// { name: 'Jude', email: 'newEmail@test.com' } 
// { name: 'Jude', email: 'newEmail@test.com' } 

/*SOLUTION*/

// Cloning the data won't change the data inside of the clone
let obj1 = {name: 'Jude', email:'MyEmail@email.me'};
let clone = Object.assign({}, obj1);
let colone 2 = {...obj1}

obj1.name = 'Peter';
console.log(clone);
```



**How To Compare Two Objects**

```javascript
let obj1 = {name: 'Jude', email:'MyEmail@email.me'};
let obj2 = {name: 'Jude', email:'MyEmail@email.me'};

//t	urns obj into a string
let final = JSON.stringify(obj1) === JSON.stringify(obj2);
console.log(final);
//true
```



### Type coercion

is the process of converting value from one **type** to another such as string to number, object to boolean, and so on. For comparing value always use triple equal for comparison.

```javascript
1 == '1'
true

1 === '1'
false
```

### Dynamic vs  Static Typing Language

Dynamic Language allow us  to not have to say what type of variable the data will be while Static Typing have to say what type the variable will be. JavaScript is a Dynamic Language and it already  knew what type it is on the runtime.

```
//Dynamic
var a = 100;

//static
int a = 100;
```

