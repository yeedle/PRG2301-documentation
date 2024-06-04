# ExpressJS

Express is a node.js library/framework that gives you utilites to build a backend server using Javascript and NodeJS. A server is a program that is connected to the internet and can receive and respond to HTTP requests. Usually, a frontend ("client") will be the program the user interacts with it, and the backend ("server") will be a single program running on a computer handling any business logic and communicating with the database and other APIs (APIs are also servers).

### Hello World

Setting up a server with express is really simple. The following code creates a server with a single endpoint. Once you start your server (by running `node index.js`), you can go to `localhost:3000` in your browser and you'll see the data sent from your server

```javascript
import express from 'express';

const app = express();
const port = 3000;

app.get('/', (req, res) => {
  res.json({ hello: "world" })
});

app.listen(port, () => {
  console.log(`the app is running and listening on port ${port}`)
});
```

We can set up endpoints that only respond to specific HTTP requests using express' functions

```javascript
// this will handle requests sent as GET requests to the /tasks endpoint
app.get('/tasks', (req, res) => {
  res.json(["task1", "task2"])
})

// this will handle requests sent as POST requests to the /users endpoint
app.post('/users', (req, res) => {
  const body = req.body
  res.json({ ok: true })
});

```

Using the HTTP protocol, we can send data to the server in 3 ways: path parameters, query parameters, and a body. A path parameter is a part of the URL itself. For example `GET /tasks/1`, or `GET /tasks/42`.  1 and 42 are considered a path parameter. Path parameters are usually required. \
\
Query paramters are additional data that we can send after the path. It usually looks as follows `GET /tasks?status=done&tags=work` - This URL has two query parameters: `status` and `tags`. \
\
A body is where we send larger sizes of data. In the header of the request we have to specify what type of data we're sending the body, using the header `Content-Type`. For JSON bodies, `Content-Type` should be set to `application/json`.\
\
Express lets us get all these different data using the `req` object.

```javascript
app.use(express.json()) // this instructs express to transform data into json if the `Content-Type` is set to `application/json`

app.patch('/tasks/:id', (req, res) => {
  // :id is a path parameter, and we can get it using `req.params`
  console.log(req.params.id) // this will print whatever :id is when the request is sent
  console.log(req.body) // this will print the entire body.
  console.log(req.query.status) // this will print the value of status, if the path had a query parameter called status (for example GET /tasks?status=done, this will print "done")
  res.send("bye")
});
```
