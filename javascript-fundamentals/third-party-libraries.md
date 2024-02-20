# Third-Party Libraries

A big rule in programming is to keep code DRY (Don't Repeat Yourself). This is why having reusable functions is so useful. Many times, people publish their code as a library/package. You can search for millions of packages on [npm](https://npmjs.com) (Node Package Manager). If you find a package you want to use, you can install it in your project by running the following command:\
\
`npm install <package name>`

Your project must have a file named `package.json` in order for this to work. If it doesn't, you can generate one by running

`npm init`

Packages along with all of the packages they are dependent on (called "dependencies") get installed in a folder that is called node\_modules, and the also get added to the "dependencies" key in your package.json file.
