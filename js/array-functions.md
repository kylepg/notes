<title>javascript - array functions</title>

# Javascript - Array functions

### Array.find

```javascript
// EXAMPLE 1
let arr = ["a", "b", "c"];
arr.find(k => k == "b");
// 'b'

// EXAMPLE 2
let arr = [2, 4, 6, 8, 9, 10, 12];
function isOdd(i) {
  return i % 2 !== 0;
}
arr.findIndex(isOdd);
// 4
```

### Array.findIndex

```javascript
// EXAMPLE 1
let arr = ["a", "b", "c"];
arr.findIndex(k => k == "b"); // 1
// EXAMPLE 2
arr.findIndex(k => k == "z"); // -1
// FIND ODD NUMBER
let arr = [2, 4, 6, 8, 9, 10, 12];
function isOdd(i) {
  return i % 2 !== 0;
}
arr.findIndex(isOdd); // 4
```

Array.prototype.indexOf() expects a value as first parameter. This makes it a good choice to find the index in arrays of primitive types.

Array.prototype.findIndex() expects a callback as first parameter. Use this if you need the index in arrays with non-primitive types (e.g. objects) or your find condition is more complex than just a value
