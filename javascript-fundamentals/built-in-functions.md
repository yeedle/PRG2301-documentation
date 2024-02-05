# Built-in Functions

Javascript comes with a lot of pre-define functions. Here are the ones we covered in class (I've added a link to the MDN documentation for each function):

* [`Math.random`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Math/random) generates a random number between 0 and 1
* [`Math.abs`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Math/abs) removes the negative sign from a number if it's negative
* [`Math.round`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Math/round) rounds a number with a decimal point to the closes integer
* [`Math.ceil`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Math/ceil) rounds a number up to the next integer
* [`Math.floor`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Math/floor) rounds a number down to the previous integer
* [`Object.keys`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Object/keys) gives you a string array of an object's keys
* [`Object.values`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Object/values) gives you an array of an object's values
* [`Object.entries`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Object/entries) gives you an array where each item is an array of \["key", value]
* [`console.log`](https://developer.mozilla.org/en-US/docs/Web/API/console/log\_static) prints output to the console
* [`console.table`](https://developer.mozilla.org/en-US/docs/Web/API/console/table\_static) prints output to the console as a table
* [`console.time`](https://developer.mozilla.org/en-US/docs/Web/API/console/time\_static) starts a timer
* [`console.timeEnd`](https://developer.mozilla.org/en-US/docs/Web/API/console/timeend\_static) ends the timer and prints the total amount of time between start and end in milliseconds

We also covered "methods" (function that you can call on values) for strings and arrays

* [`"string".charAt`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/charAt) returns the character at an index
* [`"string".startsWith`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/startsWith) returns `true` if a string starts with a value
* [`"string".endsWith`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/endsWith) returns `true` if a string ends with a value
* [`"string".replace`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/replace) replaces a substring with a different string
* [`"string".includes`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/includes) returns `true` if a substring is found within a string
* [`"string".trim`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String/trim) removes whitespace from the start and end of a string
* [`[1, 2, 3].filter`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/filter) filters an array with a filter function
* [`[1, 2, 3].map`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/map) transforms each element in an array with a function
* [`[1, 2, 3].forEach`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array/forEach) like a for loop, but the body of the for loop is a function

It's worth taking a look at the MDN pages for [String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/String) and [Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/Array) functions to see what other methods exist (things like `.sort`, `.reverse` and more).
