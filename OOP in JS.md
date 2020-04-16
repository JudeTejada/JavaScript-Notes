### Factory Functions

Factory functions just means that they create objects

```javascript
function createSoldier(name,weapon) {
	return {
		name,
		weapon,
		attack() {
		return 'attack with ' + weapon
	}
  }
}

const john = createSoldier('john', 'sword')
john.attack();

```



### Object.create

With using Object.create we can create a new object that's from an existing object

```javascript
const getWeapon  = {
 attack(){
	 return 'Attack with ' + this.weapon
 }	
}

function createSoldier(name,weapon){
    let newSoldier = Object.create(getWeapon);
	newSoldier.name = name;
    newSoldier.weapon = weapon;
    return newSoldier;
}

const joe = createSoldier('joe', 'bricks');
```



### Constructor Functions (Old way)

```javascript
function CreateSoldier(name,weapon){
   this.name = name;
   this.weapon = weapon;
}

const joe = new CreateSoldier('joe', 'bricks');
```



### ES6 Classes

```javascript
Class Soldier{
	constructor(name, weapon){
        this.name = name;
        this.weapon = weapon;
	}
	
	attack() {
	return 'Attack with' + this.weapon;	
	}
}

const joe = new Soldier('joe', 'bricks');
```





### This - 4 ways

```javascript
// new Binding
function Person(name,age){
    this.name = name;
    this.age = age;
}

const person1 = new Person('joe', '17');

//Implicit Binding -- it refers to the person ojb
const person = {
    name: 'Joe',
    age: '17',
    sayHello() {
        console.log('Im' + this.name;)
    }
}

//Explicit Binding -- it dictates what the keyword this
//uses bind,call,apply

const person = {
    name: 'Joe',
    age: '17',
	hi: function() {
        console.log('hi' + this.setTimeout)
    }.bind(window);
}

//arrow Function --the keyword is lexically scope
// using regular function would turn to the global context 
const person = {
  name: 'Joe',
  age: '17',
  hi: function() {
    const inner = () => {
          console.log('hi ' + this.name);
      }
      return inner();
  }
}

const joe = Object.create(person);
joe.hi()
```



### Inheritance in Classes

```javascript
class Character{
	constructor(name,age){
		this.name = name;
		this.age = age;
		
	}
}
// Use super whenever we extend from the main class and if we want to add new unique properties
class Human extends Character{
	constructor(name,age, mortal){
		super(name,age)
		this.mortal = mortal;
	}
}

```

