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
function func(){
  return new Promise();
}
```

Now, the _Promise_ needs two types of return.
- fulfill
- reject

Therefore you need to include those two parameter in your _Promise_ function
```js
new Promise((fulfill, reject) => {
  // code
})
```
