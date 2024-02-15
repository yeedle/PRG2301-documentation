# for..in vs. for..of

In JavaScript, there are two syntaxes for looping over individual elements in an array. One is `for ... in` and the other is `for .. of`. But there are some important differences between the two.

{% hint style="info" %}
There's a lot of historical and technical details behind the two syntaxes, but the bottom line is: You almost always want to use `for..of`. Only use `for..in` if you have a specific need for it and you know what you're doing.
{% endhint %}

\
JavaScript initially only had the `for...in` keyword and its purpose is to loop over the properties (keys) of objects - not to loop over arrays. The reason why JavaScript  had this is because it made more sense for the purpose of JavaScript (which was in the beginning designed specifically as a scripting language for the web and not as a general purpose programming language). With an object, if you use `for ... in`, it'll loop over every[^1] key in the object&#x20;

initially this was fine for arrays as well for a surprising reason. Arrays in javascript are actually specialized objects! (if you type `typeof array` in a javascript console the result will be `'object'`). The array object has keys, but the keys are `"0"`, `"1"` and so forth, (yes, the quotation marks are not a mistake, the keys are strings, not numbers). Let's demonstrate this:

```javascript
const array = [5,6,7]
array.age = 32 // we can assign custom properties just like with regular objects
for (const i in array) {
    console.log(i, typeof i); 
}
// this will print
// "0 string"
// "1 string"
// "2 string"
// "age string"
```

In the 90s and early 00s, a concept called "iterables" and "iterators" became popular in programming languages (first Java and C++ in the 90s, then python, C#, and PHP in the 2000s all implemented their version of this concept). Again, this is a broad and complex topic, but the basic idea is that an object can define itself as a collection of items, and the language will then allow you to use special syntax to access individual items in a loop. At the same time, JavaScript was rising in popularity as a general purpose language (NodeJS which was the first runtime to let you use javascript outside the browser was first released in 2009). It quickly became clear that enumerating over properties is just not good enough. Why not?

First of all, enumeration (the technical term for `for...if`) only gives you access to the _keys_ of the object. so for an array, you still need to do `array[i]` inside the loop to get access to the value itself.&#x20;

```javascript
for (const i in array) {
    console.log(array[i])
}
// prints
// 5
// 6
// 7
```

Second, enumeration has no guaranteed order. In 99% of the cases, you want to loop over an array in order of index starting from 0. Third, as the code above demonstrates, you can add custom properties to an array, and in most cases you definitely _do not_ want them in your loop. Let's look at an extreme example (you can jump ahead to the next paragraph if you just want to get to the for...of bit but read on if you want to learn something that might be useful in the future. Javascript has something called "sparse" arrays. Say you have a billion items, but only about a million have actual values. One way to represent missing values in JavaScript is by using `undefined` or `null`. But when you have a billion items, even if they are all `null` it still takes up a significant amount of space. One way to deal with this problem is to create a sparse array, which means that you don't even specify null or undefined. A sparse array looks like this:

```javascript
let array = [1, , , 4]
console.log(array)
// this prints [1, empty × 2, 3]
```

The above array technically has a length of 4, but internally javascript only allocates memory for 2 items. The second and third item are "empty" - literally no memory (except of keeping track of their positions) is kept in memory. But what happens when we use `for...in` on a sparse array? Since the object only has two keys, it'll only loop over the first and last element and completely ignore the empty ones. Not exactly what we need when we use sparse arrays.

Back to `for...of`. Because `for...in` was good for enumeration and not iteration (the technical term for looping over collections), javascript added support for iterators and iterables in 2015. Since the `for...in` keyword was already taken, they had to come up with a new keword for it, and `for...of` was chosen. When you use for...of, javascript doesn't treat an array as an object with keys. instead it treats it as an ordered collection of values. Inside the loop, you will have access directly to the element, and not just the index. All of the above mentioned problems with `for...in` are solved by `for..of`. You get access to the item directly (but also to the index if you need it), it ignores custom properties, it will iterate (loop) over empty items in a sparse array. There's also the added benefit that any object can become iterable (meaning it can act like an ordered collection of items) if set up correctly. Javascript itself now has a couple of other iterables besides for arras (like `Map` and `Set` - `Set` btw is extremely useful in many cases and we'll cover it in the advanced javascript portion of the course).

So to make a very long story short: When you loop over arrays, you almost always want to use `for...of` and not `for...in`. Even if none of the more complex reason apply, the fact that with `for..in` you need `array[i]` to access the value itself and with `for...of` i will be the element itself is already nicer, simpler, and cleaner syntax.

```javascript
let array = [1,2,3]
for (const i in array) console.log(array[i]) // too much code
for (const i of array) console.log(i) // much better 🙂
```

however, when dealing with objects, `for...of` is not gonna work at all. Because standard objects in javascript are not iterable. If you try to use `for...of` on an object you'll get an error `Uncaught TypeError: object is not iterable`. But even for an object, you usually don't want to use `for...in` even though it works because usually you want to iterate over the object in a specific way and not do enumerstion. Instead, you can use helper functions that javascript provides to turn an object into an iterable/array:

```javascript
let students = {
    'Chaim': 'absent',
    'Sholom': 'present',
    'Duvid': 'present'
}
// wrong way (causes an error, students is not iterable)
for (let student of students) console.log(i)
// simple way:
for (let student in students) console.log(i) // prints 'Chaim', 'Sholom', 'Duvid'
// better way
const keys = Object.keys(students) // this gives you an array ['Chaim', 'Sholom', 'Duvid']
const values = Object.values(students) // this gives you an array ['absent', 'present', 'present']
const entries = Object.entries(students) // this gives [['Chaim', 'absent'], ['Sholom', 'present'], ["Duvid", "present"]]
```

With `Object.keys`, `Object.values`, and `Object.entries` you can loop over an object in a safe and efficient way.

```javascript
// here I use Object.entries with array destructuring to get keys and values
for (let [name, attendance] of Object.entries(students)) {
   console.log(name + ' is ' + attendance)
}
// Chaim is absent
// Sholom is present
// Duvid is present
```

[^1]: technically, it's every "enumerable" key. In JavaScript, object can also have non-enumerable keys.
