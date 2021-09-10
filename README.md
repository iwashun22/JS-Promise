# JS-Promise

### this is a note of the Promise in JavaScript

A lot of Node.js functions return the _Promise_ , because we usually use the asynchronous functions.
There's a function that returns a _Promise_ itself such as
```js
fetch()
```

but we also can create it.

To create, we can use the code below
```js
function myPromise(){
  return new Promise();
}

/// or ///

const myPromise = new Promise();
```

### Now, the _Promise_ need two types of return.
- fulfill : meaning that the operation succeed
- reject : meaning that the operation failed or had an error

Note: There's one more state called _pending_ which is an initial state.

#### Therefore you need to include those two parameters in your _Promise_ function
```js
// You can name whatever you want inside the parameters
new Promise((fulfill, reject) => {
  // code
})
```

And that's how you create a new function that return the _Promise_.

### Uses of `then()` and `catch()`

`then()` will get executed when the promise was fulfilled, in the opposite `catch()` will get executed when the promise was rejected.

But this function will only run when the promise had a return. It's hard to explain, so maybe it will be better to look at the code below.

```js
///// Bad Example /////
function badFunction(){
   return new Promise((fulfill, reject) => {
      console.log('Hello');
   })
}

badFunction()
  .then(msg => console.log(meg))
  .catch(err => console.log(err));
```

The code `then()` and `catch` won't get executed because there's nothing to return in its parameter.
So you will only see the 'Hello' on the console.

Instead of using that it's better to callback
```js
function myPromise(){
  return new Promise((resolve, reject) => {
    resolve('Hello');
  })
}

myPromise()
  .then(msg => console.log(msg))
  .catch(err => console.log(err));
 
// now, then() will get execute
```
This code seems to be good, but there's better way to do it. Because this code will never execute catch() function.

### Here is better way to code.
```js
function sayHi(name){
   return new Promise((resolve, reject) => {
      if(typeof(name) === 'string') resolve(name);
      else reject(new Error('Name needs to be a type of string'));
   })
}

sayHi('Michael')
   .then(name => {return `Hello ${name}, Nice to meet you!`})
   .then(msg => console.log(msg))
   .catch(err => console.log(err));
```

### Now you can wrap them in one function to make it shorter. Also can add delay too see if it runs as asynchronous function
```js
function sayHi(name, delay){
   return new Promise((fulfill, reject) => {
      if(typeof(name) === 'string' && !isNaN(delay)) setTimeout(() => { fulfill(name) }, delay);
      else if(isNaN(delay)) reject(new Error('Delay requires a valid number'));
      else reject(new Error('Name needs to be a type of string'));
   })
}

function runAsync(person, delay){
   console.log(person);
   sayHi(person, delay)
      .then(name => {return `Hello ${name}, Nice to meet you!`})
      .then(msg => console.log(msg))
      .catch(err => console.log(err));
}

runAsync('David', 2000); // console seccessfully
runAsync(['Hello', 'world'], 3000); // console the error
runAsync(28, 80) // console the error
runAsync('John', 'Cena') // console the error
```

#### You can try it yourself, and hopefully it makes you understand little more.
