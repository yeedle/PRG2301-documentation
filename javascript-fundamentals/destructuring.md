# Destructuring

Arrays and objects are was in which we can collect data to store them as one unit. For example, instead of having a `firstName` and a `lastName` variable, we can have a `person` object `{ firstName: "Chaim", lastName: "Klein" }`. Instead of having multiple variables `person1`, `person2` and so forth, we can use an array `[person1, person2]`.

But sometimes we find ourselves wanting to "destructure" (take apart) an object or an array to pull out a field or an element. In JavaScript, destructuring is the syntax we can use to do it.

Let's sa we have a person object, and we want to pull out individual fields into their own variable:

```javascript
const person = {
  firstName: "Chaim",
  lastName: "Klein",
  age: 21,
};
```

We can use the destrucuring syntax for objects to do that:

```javascript
const { firstName, lastName } = person;

console.log(firstName);
// "Chaim"
```

Similarly, we can destructure an array

```javascript
const people = ["Chaim", "Moshe", "Duvid", "Shlomo"];

const [chaim, moshe] = people;

console.log(chaim);
// "Chaim"
```

This comes in super handy in functions, when we want to take an object as an argument, but we don't want to have to repeatedly use the object to get the fields. For example, consider the following function:

```javascript
function printReport(person) {
  console.log(`${person.firstName} ${person.lastName} is ${person.age} years old`);
}

printReport(person);
```

It can become a bit annoying! With destructuring we can do the following:

```javascript
function printReport({ firstName, lastName, age }) {
   console.log(`${firstName} ${lastName} is {age} years old`);
}

printReport(person);
```
