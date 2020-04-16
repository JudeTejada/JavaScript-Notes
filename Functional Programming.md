

### What is Functional Programming

a *programming* paradigm where you mostly construct and structure your code using functions. The goal is to minify the side effects of the code

-  1 task
- predictable
- composable
- immutable state
- return statement
- pure
- no shared state

### Pure Functions

it always return the data and doesn't make changes or overwrite the existing data. No side effects

```javascript
const array = [1,2,3]

comst removeLastItem(arr){
	const newArray = [].concat(arr);
	newArray.pop();
	return new Array;
}

removeLastItem(array) // [1,2]
console.log(array) // [1,2,3];
```



### Idempotence

a function that returns always what  we expect to do

```javascript
function randomNum(num){
	return Math.random() * num
}
randomNum(5); //random num 
```



### Immutability

Not changing the state

```javascript
const human = {name:'Joe'};

function clone(obj) {
	return {...obj}
	}
}

function updateName(obj) {
    const obj2 = clone(obj)
    obj2.name = 'Jeakyl'
    return obj2
}

updateName(obj); // 'Jeakyl'
//doesn't modify the actual data
console.log(human) // joe
```



### Currying

is a technique of translating the evaluation of a function that takes multiple arguments  and into a *function* that takes just a single argument and returns another *function* which accepts further arguments.

```js
const multiply =(a,b) => a*b

const curriedMultiply = (a) => (b) => a*b
const curriedMultiplyBy5 = curriedMultiply(5);

curriedMultiplyBy5(2);
```



### Partial Application

It expects the arguments already

```js
//only calls the function once but its executed 3 times
function multiply = (a,b,c,) => a*b*c;
const partialMultiplyBy5 = multiply.bind(null,5)
partialMultiplyBy5(4,10) // 200

```



### Compose

A system design principle that deals with the relationships of the components.

```js
//The way this work is that first the var compose accepts two parameters and on the next line is accepts the data.  Initially the last thing is done by multiplying the number first and afterwards make it Positive;

const compose = (fn1, fn2) => (data) => fn1(fn2(data))
/*
const compose = function(fn1,fn2){
  return function(data){
      return fn2(fn1(data))
  }
}
*/

const multiplyBy3 = (num) => num*3;
const makePostiive =(num) => Math.abs(num)
const multiplyBy3AndAbsolute = compose(multiplyBy3, makePositive)

multiplyBy3AndAbsolute(-50) //150 
//multiplies the num and turn to postive num
```



### Pipe

```js

const compose = (fn1, fn2) => (data) => fn1(fn2(data))
//opposite order;
const pipe = (fn1,fn2) => (data) => fn2(fn1(data));

const multiplyBy3 = (num) => num*3;
const makePostiive =(num) => Math.abs(num)
const multiplyBy3AndAbsolute = compose(multiplyBy3, makePositive)


```



### Arity

The number the argument the function takes