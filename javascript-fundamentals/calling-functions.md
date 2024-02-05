# Calling Functions

To call a function, we use the name of the function followed by parantheses:

```javascript
function addNumbers(num1, num2) {
  return num1 + num2
}

const result = addNumbers(1, 2) // result = 3
```

If a function doesn't have the `return` keyword in it, it will return `undefined`

```javascript
function addNumbers(num1, num2) {
  const addition = num1 + num2
}

const result = addNumbers(num1, num2) // result = undefined
```
