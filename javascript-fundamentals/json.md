# JSON

JSON (pronounced Jay Son) stands for JavaScript Object Notation. It's a format which is commonly used to pass data between programs, especially over the internet. NPM uses the JSON format to store information about your project, in a file called "package.json".

A JSON file will usually have something that looks just like a JavaScript object in it with the following restrictions: all keys will be strings, and the last item in an objeect or array can't have a trailing comma. For example

```json
{
  "name": "my-cool-package",
  "type": "module",
  "dependencies": {
     "@hebcal/core": "^5.0.1"
   },
   "authors": ["Chaim", "Moshe"]
}
```
