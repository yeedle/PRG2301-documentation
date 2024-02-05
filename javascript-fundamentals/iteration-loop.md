# Iteration (loop)

The word "iteration" means repition (חזרה). In javascript there are multiple ways to repeat a code block multiple times.

### While loops

A `while` loop is used when we don't know beforehand how many times we will need to run the loop or if we want to run the loop infinitely. It runs so long the condition we set at the beginning is true.

```javascript
let runTheLoop = true
// this loop will run as long as runTheLoop is true
// each time it runs, it generates a random number between 0 and 1
// if the number is greater than 0.9, the loop will stop running
while (runTheLoop) {
  console.log("I'm still running")
  const randomNumber = Math.random()
  if (randomNumber > 0.9) {
    runTheLoop = false
  }
}
```

### Do ... while loops

Do ... while loops are similar to while loops with one difference: The evaluate the condition at the **end** of the loop, instead of at the beginning.

```javascript
let runTheLoop = true
// this loop will run as long as runTheLoop is true
// when runTheLoop becomes false, it will run one last time and then stop
do {
  console.log("I'm still running")
  const randomNumber = Math.random()
  if (randomNumber > 0.9) {
    runTheLoop = false
  }
} while (runTheLoop)
```

### For loops

If we do know how many times we want to run the loop, we can use a `for` loop instead:

```javascript
// this loop will run ten times
for (let step = 0; step < 10; step++) {
   console.log(`I'm running time number # ${step}`)
}
// this will print:
// I'm running time number # 0
// I'm running time number # 1
// I'm running time number # 2
// I'm running time number # 3
// I'm running time number # 4
// I'm running time number # 5
// I'm running time number # 6
// I'm running time number # 7
// I'm running time number # 8
// I'm running time number # 9
```

A for loop consists of 4 parts

```
for (initialization; condition; afterthought) {
  code block
}
```

The initialization is where we declare a loop counter (in the above example `let step = 0;` but oftentimes you'll see `let i = 0` instead. `i` stands for index).

Then, we declare the condition when the loop will continue running. In the above example, as long as `step < 10` is true, the loop will run.&#x20;

The afterthought is a statement which javascript will run at the end of each time the loop runs. In javascript `step = step + 1` has a shorthand: `step++`. the `++` operator increments[^1] a number by 1.  So in our example above, after every run of the loop, `step` will be incremented by 1.&#x20;

Finally, the code block is what will get repeatedely run every time the loop repeats.

### For ... of loops

The vast majority of times, we use a loop to iterate over an array. When we deal with arrays, we often want to do something to each item in the array. We can accomplish that with a for..of loop;

```javascript
const students = ["chaim", "moshe", "yankel"]

for (let student of students) {
  console.log(`In this iteration, we are dealing with ${student}`)
}
// this will print:
// In this iteration, we are dealing with chaim
// In this iteration, we are dealing with moshe
// In this iteration, we are dealing with yankel;
```

### forEach

Another way to iterate over an array is with `Arrray.forEach`. It uses a function as the code block that gets repeats:

```javascript
const students = ["chaim", "moshe", "yankel"]

students.forEach((student) => console.log(`In this iteration, we are dealing with ${student}`)
// this will print the exact same thing as the for...of example
```

### map

The `Array.map` function is a special case of `forEach` because it lets us do two things at once: loop over an array, **and** transform it one element at a time. The result is a copy of the original array, but transformed according to the function we use:

```javascript
const students = [
  { name: "chaim", age: 21 }, 
  { name: "moshe", age: 18 },
  { name: "yankel", age: 40 }
]

const namesOnly = students.map((student) => student.name))
// namesOnly = ["chaim", "moshe", "yankel"]

const studentsAndDrinkingStatus = students.map((student) => {
   return {
     name: student.name,
     canDrink: student.age >= 21
  }
}
// studentsAndDrinkingStatus = [{
//  { name: "chaim", canDrink: true }, 
//  { name: "moshe", canDrink: false },
//  { name: "yankel", canDrink: true }
// ]
```

[^1]: Increments is a fancy way of saying "increases" or "adding"
