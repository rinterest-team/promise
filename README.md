@ promise from KISSY

# promise
---

ES6-compatible promise library. Promise/A+ implementation.

## example

### nodejs
```javascript
var Promise = require('modulex-promise');
readFilePromisified('config.json')
.then(function (text) { // (A)
    var obj = JSON.parse(text);
    console.log(JSON.stringify(obj, null, 4));
})
.catch(function (reason) { // (B)
    // File read error or JSON SyntaxError
    console.error('An error occurred', reason);
});
```