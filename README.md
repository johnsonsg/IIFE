# IIFE - Immediately-Invoked Function Expression

* Pronounced "Iffy" by Ben Alman who introduced the acronym

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

(function myIIFE(){
  num++
  console.log(num)
  return num !== 5 ? myIIFE(num) : console.log('finished')
})(num = 0); // passing in a parameter and giving it a value in case the parameter is not provided. 
This enables us to call the function (allows for recursion) again. So if we need an IIFE with recursion 
where the function actually calls itself, we can refer to the function by name within.

After, it is executed outside the function scope, you can not call it again. It can only be called once. 
It would only be referred to by the name of the function inside the IIFE, because after it is invoked,
the IIFE is no longer available. 


```
