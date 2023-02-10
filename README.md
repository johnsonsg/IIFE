# IIFE - Immediately-Invoked Function Expression

* Pronounced "Iffy" by Ben Alman who introduced the acronym
* Why use an IFFE: It does not pollute the global object namespace. 

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

increment();

```
