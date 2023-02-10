# IIFE - Immediately-Invoked Function Expression

* Pronounced "Iffy" by Ben Alman who introduced the acronym
* 3 Variations
* 3 Reasons to use an IFFE: 
  - It does not pollute the global object namespace. 
  - Private Variables and Methods from Closure.
  - The Module Pattern 
  - [Markdown - Link](#Link)

## Variations

### with anonymous arrow functions inside: 
```
(() => {
// do stuff
})();

(() -> {
// When the arrow function is contained by Paranthesis that is what makes it an IIFE
})

The Paranthesis at the end (), this is the operator that calls it into action.
so when the function has no name like this it is immediately invoked. 

```

### second variation you may see: with the functions keyword: 
```
(function (){
// essentially the same but not an arrow function, it just uses the function keyword.
})();

```

### third variation you may see: with a function name (allows for recursion: where the function calls itself):
```
// Immediately invoked

(function myIIFE(num = 0){
  num++
  console.log(num)
  return num !== 5 ? myIIFE(num) : console.log('finished')
})(); 

// passing in a parameter and giving it a value in case the parameter is not provided. 
This enables us to call the function (allows for recursion) again. So if we need an IIFE with recursion 
where the function actually calls itself, we can refer to the function by name within.

After, it is executed outside the function scope, you can not call it again. It can only be called once. 
It would only be referred to by the name of the function inside the IIFE, because after it is invoked,
the IIFE is no longer available. 


```

### Why use IIFE: Reason 1) Does not pollute the global object namespace
```
// global
const x = 'whatever'

const helloWorld = () => 'Hello World!'

// isolate declarations within the function
(() => {
  const x = 'life whatever'
  const helloWorld = () => 'Hello IIFE!'
  console.log(x)
  console.log(helloWorld())
})()

the IFFE is immediately invoked, but you can how the functions outside the IFFE are waiting to be called. so, lets now lets console.log() them.

// global
const x = 'whatever'

const helloWorld = () => 'Hello World!'

// isolate declarations within the function
(() => {
  const x = 'life whatever'
  const helloWorld = () => 'Hello IIFE!'
  console.log(x)
  console.log(helloWorld())
})()

console.log(x)
console.log(helloWorld())

// Now you return the the two functions outside the IFFE, and this creates a namespace.
```

### Why use IIFE: Reason 2) Private Variables and Methods from Closure.
```
const increment = (() => {
let counter = 0;
console.log(counter)
const credits = (num) => console.log(`I have ${num} credits`); // Credits function
return () => { counter++; credits(counter); } // Anonymous function
})()

You will see the immediately invoked expression is called once: returning '0' and now it is complete.
But now lets call the function increment

const increment = (() => { 
  let counter = 0;
  console.log(counter);
  const credits = (num) => console.log(`I have ${num} credits`); // Credits function
  return () => { counter++; credits(counter); } // Anonymous function
})()

increment(); // Call function

Now it calls our anonymous function into action, and it still has lexible scope to 
refer to the counter variable.  And if you call increment() again you can see 
it adding to the num count.

However, if you try to access the counter var directly or the credits function 
directly you will get a ref error because they are not availabe in the global scope

credits(3); // ref error

```

### Why use IIFE: Reason 3) The Module Pattern (Modules were introduced ES6)#real-cool-heading
```
// Creating an Object that will be returned 
const score = (() => {
  let count = 0; // private variable

// return object
  return {
    current: () => { return count },
    increment: () => { count++ },
    reset: () => { count = 0 }
  }
})();

You will see that when you run it just like this, it returns nothing. 
But, 'Score' will now have access to the methods returned in the Object.

So, lets look at an example of that by calling 'Score' with a dot notation:

// Creating an Object that will be returned 
const Score = (() => {
  let count = 0;

  return {
    current: () => { return count },
    increment: () => { count++ },
    reset: () => { count = 0 }
  }
})();

Score.increment();
console.log(Score.current());

```
# Link
