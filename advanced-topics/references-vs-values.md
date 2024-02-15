# References vs Values

When we assign a value to a variable in JavaScript, it does different things depending on whether the value is a primitive value or not. A variable is basically an address for a place [in the computer's memory (RAM).](#user-content-fn-1)[^1] Think of memory as a big apartment building with a lot of empty apartments. When you create a variable, let's say `let age`, javascript will reserve a specific place in RAM in which you can store data. In our apartment building analogy, javascript just writes down in his book "Apartment 4b is leased to Mr. Age". You call it `age` and javascript translates that to an actual memory address (when mail comes in for Mr. Age, javascript knows to send it to apartment 4b...).

When you assign a value, javascript will put something in that place in memory. But what is that "something" that javascript puts in memory?&#x20;

For primitive values (numbers, strings, booleans), javascript will store the value itself. For example, when you write`let age = 32` javascript finds an empty place in memory, and records the value of `32` in that place. When you do `console.log(age)` javascript will take out its internal address book, look up the memory address for `age`, and then go visit that place in memory and read what's in there. And what javascript will find there is the actual number `32`. Same thing goes for strings, booleans, undefined and null.

However, for complex data types, the story is different. [Javascript has an internal place where it stores objects, arrays, functions, etc (this is called "the heap")](#user-content-fn-2)[^2].  When you create a variable, Javascript doesn't put the actual object or array in there. Instead, it creates the actual object in a different location, and puts a reference (the address) of that object's internal location into the memory location of the variable.&#x20;

To use our above analogy, when the mailman arrives at apartment 4B, he doesn't find an actual person, but a "forwarding address" where he needs to go to find the actual person.

So lets consider the following cod

```javascript
let age = 32;
let otherAge = age;
otherAge += 5;
console.log(age) // still 32
```

in the first line, javascript creates a space in memory, gives it an address (lets say address #1), and puts the value of `32` in it. Now when you use `age`, javascript goes to address #1, looks whats inside and sees the number 32. On the second line, javascript goes to address #1, takes what is inside (the number 32) and copies it over to a new place in memory (let's say address #2). Now when you do `otherAge +=5`, javascript looks up the address of `otherAge`, reads the value at that address (it's 32), adds 5 to it, and stores it back into that same address (address #2). Meanwhile, the value that lives at the other address (address #1, where `age` lives) is completely unchanged. It doesn't even now that it's "clone" that's living at address #2 has been updated.

the story is different with complex objects. lets consider the following code

```javascript
let student = { age: 32 }
let otherStudent = student;
otherStudent.age += 5
console.log(student.age) // prints 37!!!
```

In the first line, javascript creates the `student` object in the heap (lets say address #500), and then at the address of `student` (lets say address #1) it puts the address of the `student` object. Now when you do `let otherStudent = student`, javascript goes to the first address (address #1), and copies whats inside (a reference, or forwarding address) into `otherStudent` (address #2). Both of them now have the same value in them (address #500), but the value is just an address (a "reference") to somewhere else.&#x20;

Now when you do `otherStudent.age += 5`, javascript goes to `otherStudent` and sees that it's an address, so it goes to that address where it finds an object that looks like this `{age: 32}` so it takes the literal value of age, adds 5 to it, and then puts it back into memory at the same address. But think about it! both `student`and `otherStudent` are unchanged. Their value is still address #500 for both of them! So when you print `student.age` it goes to address #1, finds the forwarding address #500, goes there, looks inside, finds `{ age: 37 }` and prints that.

To actually copy an complex data type in JavaScript is complicated. There's `Object.assign` or the "rest" operator (`...`), but they make "shallow" copies (only top level primitives get copied, nested complex types are still copied by reference). There are of course many third party libraries that implement deep cloning functionality. A quick and dirty heck is to do this `let deep copy = JSON.parse(JSON.stringify(object))`. This turns your complex data type into a string and then turns the string back into a completely brand new deeply cloned object that lives in its entirety in a different place in memory completely unrelated to the original object. The trick works because once it's a string all references ro the original is lost.

[^1]: Whenever a program runs on the computer, the computer dedicates a portion of RAM where the program can store data while the program is running. When the program stops running, the computer deletes that memory. This is called "memory allocation".

[^2]: The reason for this is because the size (number of bytes) of primitives are known before hand so javascript doesn't have to do anything special with them. Complex data types don't have a predetermined size. An array of one item is small, but an array of 50 items is much bigger. The heap is a place where javascript can dynamically allocate memory as the size of your object or array shrinks or grows.
