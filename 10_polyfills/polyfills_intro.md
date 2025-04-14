### What is a Polyfill? Why are Polyfills important?
- A `Polyfill` is a piece of JS code that replicates the behaviour of a newer feature in older browsers that don't support it.

```javascript
let arr = [1,2,3,4,5];
```

- Default `map()` working
```javascript
let result1 = arr.map((item,index,arr) => {
  return {item,index,arr}
});

console.log("Default result :- ", result1);
/*
[
  { item: 1, index: 0, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 2, index: 1, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 3, index: 2, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 4, index: 3, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 5, index: 4, arr: [ 1, 2, 3, 4, 5 ] } 
]
*/
```

- Polyfill `map()` implementation
```javascript
Array.prototype.myMap = function (cb) {
  let output = [];
  for (let i = 0; i < this.length; i++) {
    output.push(cb(this[i], i, this));
  }
  return output;
};

let result2 = arr.myMap((item,index,arr) => {
  return {item,index,arr}
})

console.log("Polyfill result :- ", result2);
/*
[
  { item: 1, index: 0, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 2, index: 1, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 3, index: 2, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 4, index: 3, arr: [ 1, 2, 3, 4, 5 ] },
  { item: 5, index: 4, arr: [ 1, 2, 3, 4, 5 ] } 
]
*/
```

- `Polyfills` are important because they allow modern web features to work in older browsers, ensuring consistent UX across different platforms.
- `For Example` Your app uses promises but users on older browsers face errors. A Promise Polyfill fixes that instantly.

### When should you & should you not write your own polyfill? 
- Do it if the feature is small and specific. `e.g a missing method`
- Avoid if its complex or already covered by a trusted library. `like core-js`

### How do polyfills affect bundle size & performance?
- They increase the bundle size and may `slow down` runtime performance.
- The best practice is to use polyfills selectively or load them conditionally based on user's browser.

```javascript
if(!window.fetch) {
  // Avoid modifying global state unnecessarily & only load polyfill script here
}
```

### Why are polyfills needed?
- `Browser Compatibility` Different browsers and different versions of the same browser may not support all the latest web standards. Polyfills help ensure that all users have a consistent experience regardless of the browser they use.
- `Future-Proofing` As web standards evolve, using polyfills allows developers to write code that conforms to modern practices, knowing that it will still work in older environments.
- `Development Convenience` Polyfills enable developers to use new features and syntax without waiting for full support across all browsers.

### Why are polyfills tested in isolation?
- To avoid `breaking` with existing native implementations and third-party code.
- `For Example` You wouldn't test a car's brakes while driving on the highway - test in a controlled area first.