# Defining Functions

There are two syntaxes for functions. The basic syntax is as follows:

<pre class="language-javascript"><code class="lang-javascript">/**
 * <a data-footnote-ref href="#user-content-fn-1">A simple function to add two numbers.</a>
 * @param {number} num1 - The first number.
 * @param {number} num2 - The second number.
 * @return {number} The sum of the two numbers
 */
<a data-footnote-ref href="#user-content-fn-2">function</a> <a data-footnote-ref href="#user-content-fn-3">addNumbers</a>(<a data-footnote-ref href="#user-content-fn-4">num1, num2</a>) {
  // body of the function goes in here
  <a data-footnote-ref href="#user-content-fn-5">return</a> num1 + num2
}
</code></pre>

The other syntax, which is called "function expression" syntax (or fat arrow, anonymous syntax, callback, or lambda) is as follows:

```javascript
const addNumbers = (num1, num2) => {
  return num1 + num2
}
```

When we use a function expression, and there's only one statement in it, we can skip the curly braces and the `return` keyword:

```javascript
const addNumbers = (num1, num2) => num1 + num2
```

[^1]: This comment style is called a "JSDoc" and using it  automatically creates documentation for your function which Visual Studio Code will show you when you use it.

[^2]: This is a keyword, and it describes the code block as a function.

[^3]: This is the name of your function, and it can be anything you want. The same rules that apply to variable names, apply to function names.

[^4]: these are called "function parameters. They are the list of variables which can be passed in to the function when it is called. A function can also have zero paramteres, in which case you will simply have an set of parentheses () with nothing between them.

[^5]: the return keyword marks the end of the function, and the expression following the return keyword is what the caller of the function gets when the function completes running. If a function has no return statement, it returns `undefined` .
