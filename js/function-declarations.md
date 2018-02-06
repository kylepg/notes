<title>javascript - function declarations</title>

# Javascript - Function declarations

An illustration of when to prefer the first method to the second one is when you need to avoid overriding a function's previous definitions.

With:

```javascript
if (condition) {
  function myfunction() {
    // Some code
  }
}
```

this definition of myfunction will override any previous definition, since it will be done at parse-time.

While:

```javascript
if (condition) {
  var myfunction = function() {
    // Some code
  };
}
```

does the correct job of defining myfunction only when condition is met.
