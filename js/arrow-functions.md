<title>javascript - arrow functions</title>

# Javascript - Arrow functions

The arrow syntax is a shortform for anonymous functions. Named functions are defined with the function keyword.

## Benefits

### 1. Shorter syntax

Lets take a look at a regular function.

```javascript
function funcName(params) {
  return params + 2;
}
funcName(2); // 4
```

This above code indicates one of the two reasons for creating arrow functions: shorter syntax.

The exact same functions can be expressed as an arrow function with only one line of code:

```javascript
var funcName = params => params + 2;
funcName(2); // 4
```

Pretty cool. This example is obviously an extreme simplification, but hopefully illustrates my point. Lets take a look at the syntax of arrow functions a little more in-depth.

```javascript
parameters => {
  statements;
};
```

If we have no parameters, we express an arrow function like this.

```javascript
() => {
  statements;
};
```

When you only have one parameter, the opening parenthesis are optional.

```javascript
parameters => {
  statements;
};
```

Finally, if you are returning an expression, you remove the brackets.

```javascript
	parameters => expression
	// is equivalent to:
	function (parameters){
 	 return expression;
	}
```

### Examples

```javascript
const arr = [1, 2, 3];
const squares = arr.map(x => x * x);

// Traditional function expression:
const squares = arr.map(function(x) {
  return x * x;
});
```

```javascript
function () { return 1; }
() => { return 1; }
() => 1

function (a) { return a * 2; }
(a) => { return a * 2; }
(a) => a * 2
a => a * 2

function (a, b) { return a * b; }
(a, b) => { return a * b; }
(a, b) => a * b

function () { return arguments[0]; }
(...args) => args[0]

() => {} // undefined
() => ({}) // {}
```
