### **Closures**

is the combination of a  function bundled together (enclosed) with references to its surrounding  state (the lexical environment). In other words, a **closure** gives you access to an outer function's scope from an inner function.

```js
//normally callme should be undefined but with closures we still manage to get the data because the data were already declared before the setTimeOut was executed.
function callMeMaybe(){
	setTimeout(function() {
		console.log(callme)
	},4000)
	const callMe = 'Hi I am now here!';
}

callMeMaybe();
```



Closures Examples

Initially what the code does  is to  make the function to be called once.

```js
let view;

const initialize = () => {
  let executed = false;
  
  return function() {
    if(!executed){
      executed = true;
      console.log('initialize')
    }
  }
}
const func = initialize()
func();
func();
func();
func();
// would only execute one time no matter what

/* ANOTHER SOLUTION */
let view;
function initialize(){
    let called = 0;
    
    return function(){
        if(called > 0){
            return;
        } else{
          called++;
          console.log('initialize')

        }
  }
}

const start = initialize();
start();
start();

```





