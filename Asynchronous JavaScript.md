### How JavaScript Works

*JavaScript is a single thread language because it can only do one at a time.* 

*JavaScript is a Synchronous language that  reads the code line by line and executes one time*

**Stack overflow** - When the call stack just keep getting bigger bigger hence its overflowing.

```js
function foo(){
	foo()
}

foo()
//InternalError: too much recursion 
```

**Memory Heap** - contains where memory are allocated

**Call Stack** -  tracks where we are at the code , it keeps track of what function is currently being run and what functions are called from within that function, etc.

```javascript
const one = () => {
	two = () => {
		console.log('2')
	}
	two();
}

// CALL STACk
2. TWO() // when its done, pops out from the call stack
1.ONE() // when its done, pops out from the call stack
```



Although JavaScript read the code line by line and execute it..... it would still be executed later because by default they aren't part of the JavaScript but rather from the WEB API.

When the engine runs set Timeout, the call stack doesn't know this code and it will then be pops out  from the call stack and refers to the Web API. the Web API then runs this method for 2 seconds and after its done executed it then sends to the callback queue where its saying "Hey its done do something". the event loops then runs and sends back to the call stack.

```javascript
console.log('1');
setTimeout(() => {
	console.log('2')
},2000)
console.log('3');
1
3
2


```



### Promises

is an object that may produce a single value that's either a resolve value, or a reason that its not resolved(rejected)

- pending
- resolve
- rejected

```javascript
const promise = new Promise((resolve, reject) => {
    if(true) {
    resolve('its worked')
   }
    reject('error!')
})
//when its resolved or reject
promise
//if it resolves
.then(result => console.log(result))
//catch the err if return reject
.catch(err => console.log(err));

// calls all the promises
// the way it work is that it always wait all promises and log all the values at the same time
Promise.all(promise1,promise2)
.then(datas => console.log(datas));
```



### Async/Await

a function that returns a promise. It makes code easier to read compare to Promises. it makes the code look asynchronously in synchronous. It pauses the function  until it returns a response

```javascript
//EXAMPLE 1
async function playerStart(){
const firstMove = await movePlayer(100, 'left');
    await movePlayer(400,'right')
    await movePlayer(400,'right');
    await movePlayer(400,'right');   
}

//EXAMPLE 2
async getData(){
    const response = await fetch('yahoo.com');
    const data = response.data
    console.log(data);
}

```



### ES8(2018)

#### 	Object Spread operator

it works at array and objects

```javascript
// EXAMPLE 1
const array = [1,2,3,4,5]

function sum(a,b,c,d,e){
    return a+b+c+d+e
}
// OLD WAY
sum(1,2,3,4,5);
// NEW WAY
sum(...array);
//15


//EXAMPLE 2
const animals = {
    tiger: 25,
    lion: 5,
    elephant:20,
    monkey: 50,
    birds: 1
}

function spread(anim1,anim2,anim3){
    console.log(anim1)
    console.log(anim2)
}
//wraps everything in the rest variable and let tiger have its own var
//whenever we use destructuring it must has the same name
const { tiger, ...rest} = animals;
spread(tiger, rest)
```



### ES9(2019) 

####  Async

finally- will always runs even if the promise returns resolve,reject

```javascript
Promise.resolve({ some: 'data' })
.then((data) => console.log(data));
.catch((err) => console.log(err))
.finally(() => console.log('extra'))
```



#### For await of

that takes each item from an array of promises that returns to us in the correct order of all the responses

```js
//several URLS
const urls = [
    'https://jsonplaceholder.typicode.com/posts',
 	'https://jsonplaceholder.typicode.com/comments',
    'https://jsonplaceholder.typicode.com/users'
] 

const loopThroughUrls = async function(){
    //loop through all url and fetch
    const arrayOfPromises =  urls.map(url => fetch(url));
    //loop throuch each request
    for await (let request of arrayOfPromises) {
        	const data = await request.json();
        	console.log(data);
    }
}
loopThroughUrls()
//returns data of Array
```

