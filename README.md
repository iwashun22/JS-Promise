# JS-Promise

### this is a note of the Promise in JavaScript

Most of Node.js functions return the _Promise_ , because we usually use the asynchronous functions.
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

Now, the _Promise_ need two types of return.
- fulfill : meaning that the operation succeed
- reject : meaning that the operation failed or had an error

Note: There's one more state called _pending_ which is an initial state.

Therefore you need to include those two parameters in your _Promise_ function
```js
// You can name whatever you want inside the parameters
new Promise((fulfill, reject) => {
  // code
})
```

And that's how you create a new function that return the _Promise_.

### Uses of `then()` and `catch()`

`then()` is 
