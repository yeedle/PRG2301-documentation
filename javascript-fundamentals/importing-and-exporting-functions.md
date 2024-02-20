# Importing and exporting functions

Once your programs start getting big, you'd want to start splitting them up into separate files. However, you still want to be able to use code across files. \
\
This is called importing and exporting and there are two ways to do it.\


## CommonJS (require)

The old way is by using the `require` function. For example

```javascript
// file utils.js
function add(num1, num2) { return num1 + num2; }
function subtract(num1, num2) { return num1 - num2 }

module.exports = { add: add, subtract: subtract }
```

```javascript
// file index.js
const { add } = require('./utils.js');

const result = add(1, 2);
// result = 3
```



## ES Modules

`ES` stands for ECMAScript which is the "official" name of JavaScript. In ECMAScript, if a file is a "module", you can import using the newer syntax using the keywords `import` and `export`. To make sure your files are modules, you can add `"type": "module"` to your project's `package.json` file.\


```javascript
// file utils.js
export function add(num1, num2) { return num1 + num2; } 
export function subtract(num1, num2) { return num1 - num2 }
```

```javascript
// file index.js
import { add } from './utils.js';

const result == add(1, 2);
// result = 3
```



The above approach is called "named exports", because you are naming each function (or object) that you export. With ES Modules you can also export a single object (similar to `module.exports` in CommonJS):\
\
\`\`\`javascript

```javascript
// file utils.js
function add(num1, num2) { return num1 + num2; }
function subtract(num1, num2) { return num1 - num2 }

export default { add: add, subtract: subtract }
```

```javascript
import utils from './utils.js'

const result = utils.add(1, 2)
// result = 3
```
