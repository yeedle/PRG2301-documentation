# Making HTTP requests on the frontend

Once you have a server up and running, you'll want to be able to communicate with the server from the frontend. Sending requests to it, and receiving response. There are many ways to send and receive HTTP requests on the frontend, but the primary one is using the built-in `fetch` method. `fetch` returns a promise, so it always has to be awaited, or used in a chain with `.then`.\
\
To make an http requests, you need to know some basic information about the kind of request you want to make. What is the URL of the request? What HTTP verb (`GET`, `POST`, `PATCH` etc) are you using? Does the request have a body? Once you have all your information, making the request is simple:

```javascript
await fetch('http://localhost:3000/tasks?user=yeedle', {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json'
    },
    body: JSON.stringify({hello: 'world'})
})

// or using then


```

The above code makes a `POST` requests to the `/tasks` endpoint, and passes in a query parameter `user=yeedle`. It also sends a body `{ hello: "world" }` as a string, but the `Content-Type` header tells the server that this request can be safely parsed as JSON.\
\
If the server responds with data, we can use another method to parse the data. For example:\


```javascript
const result = await fetch('http://localhost:3000/tasks') // by default, the method is `GET` so we don't need to specify it
const data = await result.json() // this will parse the response into JSON
console.log(data) // this will print the data the server returned

// or using .then
fetch('http://locahost:3000/tasks')
  .then(result => result.json())
  .then(data => console.log(data));
```
