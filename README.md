# promise-hash

In the current [Promises](https://www.promisejs.org/) implementation that Node.js uses, there exists the `Promise.all()` method, which resolves an array of promises. But what that implementation really misses is the way the [rsvp](https://github.com/tildeio/rsvp.js/) library allows you to pass an object to a promise and retain the data structure of that promise.

This library adds this functionality.

## Getting Started

```
npm install --save promise-hash
```

In your app, you can then do this:

```js
require('promise-hash');
```

Because it functions as a _polyfill_, all you need to do is include this in your code and the `Promise` object will be polyfilled to include the `#hash()` method.

## Usage Example

```js
require('promise-hash');

function dummyPromise(value) {
  return new Promise((resolve, reject) => {
    setTimeout(resolve, 100, value);
  });
}

const promises = {
  promise1: dummyPromise('this is the first promise'),
  promise2: dummyPromise('this is the second promise'),
  promise3: dummyPromise('this is the third promise')
};

Promise.hash(promises).then(results => {
  console.log(results);
});
```