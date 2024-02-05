# Passing Functions

The most straightforward way to use functions is to call them. But sometimes we don't call our functions directly, we just pass them to another function. This is particularly useful when we use array methods. For example, if we have a list of students `const students = ["Chaim Stern", "Moshe Weiss", "Duvid Stern", "Yakov Klein"]` and we want to filter them to get only the ones that are named "Stern". We can define our filter in a function, and then use `Array.filter` to filter the list;

```javascript
const students = ["Chaim Stern", "Moshe Weiss", "Duvid Stern", "Yakov Klein"]

function studentFilter(student) {
    return student.endsWith("Stern")
}

const studentsNamedStern = students.filter(studentFilter)
// studentsNamedStern = ["Chaim Stern", "Duvid Stern"]
```

Javascript also lets us define the filter function "inline" by using the function expression syntax

```javascript
const studentsNamedStern = students.filter((student) => { return student.endsWith("Stern") })
```

Remember how one-line function expressions don't need the `return` keyword? We can make the above even shorter:

```javascript
const studentsNamedStern = students.filter((student) => student.endsWith("Stern"))
```



Similarly, we can use the `map` array method to transform
