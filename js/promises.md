<title>javascript - promises</title>

# Javascript - Promises

Browsers have native promises, such as:
* fetch()


```javascript
    function breathe(amount) {
      return new Promise((resolve, reject) => {
        if (amount < 500) {
          reject('That is too small of a value');
        }
        setTimeout(() => resolve(`Done for ${amount} ms`), amount);
      });
    }
    breathe(1000).then(res => {
      console.log(res);
      return breathe(500);
    }).then(res => {
      console.log(res);
      return breathe(600);
    }).then(res => {
      console.log(res);
      return breathe(200);
    }).then(res => {
      console.log(res);
      return breathe(500);
    }).then(res => {
      console.log(res);
      return breathe(2000);
    }).then(res => {
      console.log(res);
      return breathe(250);
    }).then(res => {
      console.log(res);
      return breathe(300);
    }).then(res => {
      console.log(res);
      return breathe(600);
    }).catch(err => {
      console.error(err);
      console.error('YOU SCHREWED UP');
    })
```

### What's the difference between returning value or Promise.resolve from then()

The rule is, if the function that is in the then handler returns a value, the promise resolves/rejects with that value, and if the function returns a promise, what happens is, the next then clause will be the then clause of the promise the function returned, so, in this case, the first example falls through the normal sequence of the thens and prints out values as one might expect, in the second example, the promise object that gets returned when you do Promise.resolve("bbb")'s then is the then that gets invoked when chaining(for all intents and purposes). The way it actually works is described below in more detail.

Quoting from the Promises/A+ spec:

The promise resolution procedure is an abstract operation taking as input a promise and a value, which we denote as [[Resolve]](promise, x). If x is a thenable, it attempts to make promise adopt the state of x, under the assumption that x behaves at least somewhat like a promise. Otherwise, it fulfills promise with the value x.

This treatment of thenables allows promise implementations to interoperate, as long as they expose a Promises/A+-compliant then method. It also allows Promises/A+ implementations to “assimilate” nonconformant implementations with reasonable then methods.

The key thing to notice here is this line:

if x is a promise, adopt its state [3.4]

link: https://promisesaplus.com/#point-49