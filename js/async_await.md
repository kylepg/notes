<title>javascript - async await</title>

# Javascript - Async/await

```javascript

    function breathe(amount) {
      return new Promise((resolve, reject) => {
        if (amount < 500) {
          reject('That is too small of a value');
        }
        setTimeout(() => resolve(`Done for ${amount} ms`), amount);
      });
    }
    function catchErrors(fn) {
      return function (...args) {
        return fn(...args).catch((err) => {
          console.error('Ohhhh nooo!!!!!');
          console.error(err);
        });
      }
    }
    async function go(name, last) {
      console.log(`Starting for ${name} ${last}!`);
      const res = await breathe(1000);
      console.log(res);
      const res2 = await breathe(300);
      console.log(res2);
      const res3 = await breathe(750);
      console.log(res3);
      const res4 = await breathe(900);
      console.log(res4);
      console.log('end');
    }
    const wrappedFunction = catchErrors(go);
    wrappedFunction('Wes', 'Bos');

```
Waiting on multiple promises
```javascript
<!DOCTYPE html>
<html lang="en">

<head>
  <title>Async Await</title>
</head>

<body>
  <script>
    // async function go() {
    //   const p1 = fetch('https://api.github.com/users/wesbos');
    //   const p2 = fetch('https://api.github.com/users/stolinski');
    //   // Wait for both of them to come back
    //   const res = await Promise.all([p1, p2]);
    //   const dataPromises = res.map(r => r.json());
    //   const [wes, scott] = await Promise.all(dataPromises);
    //   console.log(wes, scott);
    // }
    // go();
    async function getData(names) {
      const promises = names.map(name => fetch(`https://api.github.com/users/${name}`).then(r => r.json()));
      const people = await Promise.all(promises);
      console.log(people);
    }
    getData(['wesbos', 'stolinski', 'darcyclarke']);
  </script>
</body>

</html>
```