# pg-promise

`pg-promise` is a NodeJS library used to communicate with PostgreSQL databases.\
\
To use it, you first need to install it by running `npm install pg-promise`

You first need to connect to the database when your program starts.\
\
\


```javascript
import pgPromise from 'pg-promise';

const pgp = pgPromise() // this creates a pg-promise object

// this creates a database connection
const db = pgp({
    host: '', // the url of your database
    port: 5432, // by convention postgresql databases are open on port 5432
    database: '', // this is the database name
    user: '', // this is the username
    password: '', // and this is the password
    ssl: true
})
```

Once the connection with the database is established, you can use it to run SQL queries and receive the results as javascript objects\


```javascript
const result = await db.one('select * from task limit 1')
// result will be a task object, for example { title: 'title', done: false })

const result = await db.many('select * from task')
// result will be a list of tasks, e.g. [{title: 'title1', done: false}, {title: 'title2', done: true}]
```

You can also make queries dynamic by "templating" parts of the query and passing in values at runtime. For example, if you want a query that looks up a task by ID, but you get the ID from the user when the make a request, your query will look as follows:\


```javascript
app.patch('/tasks/:id', (req, res) => {
    const result = await db.none("update task set status = 'done' where id = ${id}", { id: req.params.id })
    res.json({ok: true})
});
```

Make sure not to use template strings (strings that start with \` and end with \` because that will leave your code open to SQL injection where the user can run any SQL they want on your database. Instead use regular strings, and pass in the data as shown, so that pg-promise will handle sanitization for you.\
\
