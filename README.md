# Express_JS
Express.js is a fast, minimal, and flexible web application framework for Node.js that helps you build web servers and APIs easily. 
Good shit good shit!!!

# FOLDER STRUCTURE 
**1. config**
This is where you keep settings.
Example: How to connect to the database, secret keys, or which port to run on.

**2. controller**
This is where the main logic goes.

Example: If someone wants to create a user, the controller decides how to do it.

**3. database**
This is where you manage the database setup.

Example: Files to connect to your database or create tables.

**4. helpers**
These are small tools or functions to help you.

Example: A function to format dates or hash passwords.

**5. middleware**
This is code that runs before the main logic.

Example: Checking if a user is logged in before allowing access.

**6. model**
This is where you define your data.

Example: What a "User" looks like in the database (name, email, password, etc).

**7. routes**
This is where you say which URL does what.

Example: If someone visits /login, send them to the login controller.

---
# Params 
`req.params` is an object that holds URL parameters.
`req.params.id` accesses a specific one — like a user ID from the URL.

### Explanation of Comments:
1. **Import and App Initialization**:
   - `const express = require("express")`: Importing Express.js for use in this application.
   - `const app = express()`: Creating an Express application instance.

2. **Routes**:
   - The `/` route is a basic route that sends a simple string response.
   - The `/products` route returns a list of sample products in JSON format.

3. **Server Setup**:
   - The `port` variable specifies the port number where the server will run.
   - `app.listen()` starts the server and logs a message to indicate it’s running.'
  
## Sample Routes

```javascript
const express = require('express');
const app = express();

app.use(express.json()); // Middleware to parse JSON

// GET
app.get('/user/:id', (req, res) => {
  res.send(`User ID: ${req.params.id}`);
});

// POST
app.post('/user', (req, res) => {
  res.send(`New user: ${req.body.name}`);
});

// PUT
app.put('/user/:id', (req, res) => {
  res.send(`User ${req.params.id} fully updated`);
});

// PATCH
app.patch('/user/:id', (req, res) => {
  res.send(`User ${req.params.id} partially updated`);
});

// DELETE
app.delete('/user/:id', (req, res) => {
  res.send(`User ${req.params.id} deleted`);
});

app.listen(3000, () => console.log('Server running'));
```

---

## Route Parameters

```js
// Route: /user/:id
req.params.id // grabs the 'id' from the URL
```

Example:
```
URL: /user/123
req.params = { id: '123' }
```

---

## express.json()

```js
app.use(express.json());
```

- Parses incoming JSON requests
- Makes data available in `req.body`

     

# MIDDLEWARE
Middleware in Express.js refers to functions that execute during the request-response cycle. These functions have access to the request (req) and response (res) objects, as well as the next function, which passes control to the next middleware in the stack.

Middleware in simple terms is like a helper function that sits between the request from the user and the response from the server in a web application. It can:

- Run code before your request is processed
- Modify the request or response
- End the request-response cycle
- Call the next middleware function

# Embedded Javasceript templating 
Embedded JavaScript templating is a way to insert dynamic content into HTML using JavaScript. Instead of writing static text, you use placeholders that get replaced with real data when the page loads.

Instead of writing:
```<h1>Hello, John!</h1>```
You can write:
```<h1>Hello, <%= name %>!</h1>```
Then, JavaScript fills in the <%= name %> with actual data, like "John".

Common templating tools include EJS, Handlebars, Pug, and template literals in JavaScript. This makes web pages more flexible and dynamic. 

# What is View Engine
A view engine is a software component that allows the rendering of dynamic content onto a web page, acting as a bridge between the server side and the client side. When a user accesses a webpage, the server responds with dynamic pages, which is possible only because of the view engine. View engines are used in web development to generate dynamic HTML content by filling in placeholders with actual data. They make it easier to manage and update web pages, especially when dealing with dynamic content.

## Common Express Methods

### Routing Methods

| Method        | Description                        | Example                          |
|---------------|------------------------------------|----------------------------------|
| `get()`       | Handle GET requests                | `router.get('/', handler)`       |
| `post()`      | Handle POST requests               | `router.post('/', handler)`      |
| `put()`       | Handle PUT requests (update)       | `router.put('/:id', handler)`    |
| `delete()`    | Handle DELETE requests             | `router.delete('/:id', handler)` |
| `patch()`     | Handle partial updates             | `router.patch('/:id', handler)`  |
| `all()`       | Handle all HTTP methods            | `router.all('*', handler)`       |

### Middleware Methods

| Method        | Description                                 | Example                          |
|---------------|---------------------------------------------|----------------------------------|
| `use()`       | Apply middleware to handle requests         | `app.use(middleware)`            |
| `next()`      | Pass control to the next middleware         | `next()`                         |

### Response Methods

| Method         | Description                               | Example                               |
|----------------|-------------------------------------------|---------------------------------------|
| `res.send()`   | Send a plain text, HTML, or basic object  | `res.send('Hello')`                   |
| `res.json()`   | Send a JSON-formatted response            | `res.json({ message: 'Hi' })`         |
| `res.status()` | Set HTTP status code                      | `res.status(404)`                     |
| `res.redirect()`| Redirect to a different URL              | `res.redirect('/login')`              |
| `res.render()` | Render a view using a template engine     | `res.render('home')`                  |

### Request Object (`req`) Properties

| Property        | Description                             | Example                              |
|-----------------|-----------------------------------------|--------------------------------------|
| `req.params`    | Route parameters (`/user/:id`)          | `req.params.id`                      |
| `req.query`     | Query string parameters (`?page=2`)     | `req.query.page`                     |
| `req.body`      | Body data (for POST/PUT requests)       | `req.body.name`                      |
| `req.headers`   | Request headers                         | `req.headers['authorization']`       |


# Parser and Topology
useNewUrlParser: true | To avoid bugs and correctly parse modern connection URIs.
useUnifiedTopology: true | To have stable, modern, auto-reconnecting connections.


# Example code of express js using POSTMAN
```javascript
const express = require('express');
const app = express();

app.use(express.json());

let books = [
    { title: "Harry Potter", id: 1 },
    { title: "Game of Thrones", id: 2 }
];

// Home section
app.get("/home", (req, res) => {
    res.json({
        message: "Welcome to our bookstore API which is using REST API for the tutorial"
    });
});

// All books section
app.get("/books", (req, res) => {
    res.json(books);
});

// Single book section
app.get("/books/:id", (req, res) => {
    const book = books.find(item => item.id === parseInt(req.params.id));
    if (book) {
        res.status(200).json(book);
    } else {
        res.status(404).json({
            message: "Book not found"
        });
    }
});

// Adding new book
app.post("/add", (req, res) => {
    const newbook = {
        title: `book ${books.length+1}`,
        id: books.length + 1
    };
    books.push(newbook);
    res.status(200).json({
        message: "The new book has been added successfully",
        data: newbook
    });
});

//Updating a new book
app.put("/update/:id", (req, res) => {
    const Updatedbook = books.find(BookItem => BookItem.id === parseInt(req.params.id));

    if (Updatedbook) {
        // Update title if new one is provided
        Updatedbook.title = req.body.title || Updatedbook.title;

        res.status(200).json({
            message: "The book has been updated successfully",
            data: Updatedbook
        });
    } else {
        res.status(404).json({
            message: "Book not found"
        });
    }
});


let PORT = 4000;
app.listen(PORT, () => {
    console.log("Your server is started");
});
```

# MongogoDB and Mongoose

**MongoDB** is a NoSQL database that stores data in a flexible, JSON-like document format instead of the traditional table-based relational databases. It is schema-less, meaning documents in the same collection can have different structures. MongoDB is designed for scalability, high performance, and ease of development.

Key Features of MongoDB:

- Document-oriented storage (JSON-like BSON format)
- Schema-less (flexible data models)
- High availability with replication
- Horizontal scalability with sharding
- Rich query language for filtering, sorting, and aggregations

**Mongoose** is an ODM (Object Data Modeling) library for MongoDB in Node.js. It provides a schema-based solution to model application data, making MongoDB easier to work with. Basically it acts as an intermediary.

Key Features of Mongoose:

Defines schemas for MongoDB collections
Provides built-in validation for data
Supports middleware (pre/post hooks for operations)
Enables relationships and virtuals between documents
Simplifies queries with powerful built-in methods

# MongoDB Basic Terms

## 1. Database  
A **database** in MongoDB is a container for collections. It is similar to a database in a relational database system.

## 2. Collection  
A **collection** is a group of MongoDB documents, similar to a table in relational databases.

## 3. Document  
A **document** is a single record in a MongoDB collection, stored in **BSON** (Binary JSON) format.

## 4. Field  
A **field** is a key-value pair in a document, similar to a column in SQL.

## 5. `_id`  
A special field that uniquely identifies each document in a collection. If not provided, MongoDB generates a unique **ObjectId** automatically.

## 6. BSON (Binary JSON)  
MongoDB stores data in **BSON** format, which extends JSON with additional data types like dates and binary data.

## 7. Schema-less Database  
Unlike relational databases, MongoDB is **schema-less**, meaning documents in the same collection can have different structures.

## 8. CRUD Operations  
The four main operations in MongoDB:

- **C**reate → `insertOne()`, `insertMany()`
- **R**ead → `find()`, `findOne()`
- **U**pdate → `updateOne()`, `updateMany()`
- **D**elete → `deleteOne()`, `deleteMany()`

## 9. Indexes  
Used to improve query performance. The default index is on the `_id` field.

## 10. Aggregation  
A framework for performing complex data processing, similar to SQL’s `GROUP BY` and functions like `SUM()`.

## 11. Replica Set  
A **replica set** is a group of MongoDB servers that maintain the same data for high availability.

## 12. Sharding  
The process of distributing data across multiple servers to handle large-scale applications.

## 13. MongoDB Compass  
A GUI tool to visually interact with MongoDB.

## 14. MongoDB Atlas  
A cloud-based managed MongoDB service.

## 15. Mongo Shell  
A command-line interface to interact with MongoDB.

---

# What is a Schema?

A **schema** is a blueprint or structure that defines the organization of data in a database. It specifies the fields, data types, constraints, and relationships between data.

## Schema in Different Contexts

### MongoDB (Without Mongoose)

- MongoDB is **schema-less**, meaning documents in a collection can have different structures.
- You can insert documents with varying fields without defining a strict schema.

#### Example (MongoDB without Schema):
```json
{ "name": "Alice", "age": 25 }
{ "name": "Bob", "email": "bob@example.com" }
```

--- 

### Mongoose Schema (Schema-Based Approach)

- Mongoose enforces a schema to provide **structure** to MongoDB collections.
- You define **fields, data types, and constraints** (e.g., required fields, default values).

Here’s your content formatted correctly in GitHub Markdown:  

```markdown
## Example: Defining a Schema in Mongoose

```javascript
const mongoose = require('mongoose');

// Define a schema
const userSchema = new mongoose.Schema({
    name: { type: String, required: true },
    email: { type: String, required: true, unique: true },
    age: { type: Number, min: 18, max: 100 },
    createdAt: { type: Date, default: Date.now }
});

// Create a model from the schema
const User = mongoose.model('User', userSchema);
```

The above code is used to define a schema in Mongoose.

## Some Common Methods

```javascript
const newuser = await user.create({
    Name: 'Shashank Goud', // Name of the user
    email: 'shashank10@gmail.com', // Email ID of the user
    Age: 25, // Age of the user
    isActive: false, // Boolean flag to check if the user is active
    tag: ['Developer', 'Designer', 'Manager'], // Array of roles/tags assigned to the user
});
```

**We created this query. Now, here are some common methods used:**

```javascript
// Logging the newly created user to the console
console.log("New user: ", newuser);
```

```javascript
// Finding all users where the 'isActive' field is true
const ActiveuserofTrue = await user.find({ isActive: true });
console.log("Active users: ", ActiveuserofTrue);
```

```javascript
// Finding a specific user by name (returns the first match if multiple exist)
const FindSpecific = await user.findOne({ Name: 'Shashank Goud' });
console.log("User found: ", FindSpecific);
```

```javascript
// To get the id of the user whose data has been made latest
const GetlatestUserbyID = await user.findById(newuser._id);
console.log("ID of the new user", GetlatestUserbyID);
```
```javascript
// To use pagination for specefic items
const LimitedUser = await user.find().limit(5).skip(1);
console.log ("Accessed users while skipping 1st", LimitedUser);

```
```javascript
//To sort the users from the database
const SortUsers = await user.find().sort({age : -1}) // -1 sorts the user in ascending order
console.log ("Sorted user according to age in Ascending order : ", SortUsers);
```
# How to Get Specific Fields in MongoDB

In MongoDB, you can retrieve specific fields using **projection**. This can be done in both **Mongoose** and **MongoDB queries**.

---

## Using Mongoose

When querying documents, you can specify which fields to include or exclude.

### **Method 1: Using `.select()`**
```javascript
const user = await User.findOne({ name: 'Shashank Goud' }).select('name email');
console.log(user);
```
- This will return only the `name` and `email` fields.

To **exclude a field**, use `-` before the field name:
```javascript
const user = await User.findOne({ name: 'Shashank Goud' }).select('-age');
console.log(user);
```
- This will return all fields **except** `age`.

---

### **Method 2: Using `{ projection }` in `.find()`**
```javascript
const user = await User.findOne({ name: 'Shashank Goud' }, { name: 1, email: 1, _id: 0 });
console.log(user);
```
- `1` means **include** the field.
- `0` means **exclude** the field (`_id: 0` removes the `_id` field from the result).

---

## Using Native MongoDB Queries

If you're using the MongoDB shell or native driver:

```javascript
db.users.find({ name: 'Shashank Goud' }, { name: 1, email: 1, _id: 0 });
```
This returns:
```json
{ "name": "Shashank Goud", "email": "shashank10@gmail.com" }
```

---

## Key Points
- **Include fields:** `{ fieldName: 1 }`
- **Exclude fields:** `{ fieldName: 0 }`
- Cannot mix `1` and `0` (except `_id` which is optional).
- Use `.select()` in **Mongoose** and `{ projection }` in native **MongoDB**.

# NODEMON
**What is Nodemon?**
Nodemon is a tool that automatically restarts a Node.js application whenever it detects file changes. This helps developers avoid manually stopping and restarting the server every time they make changes to the code.

**Why Use Nodemon?**
Speeds up development – No need to restart the server manually after code changes.
Monitors file changes – Watches for updates in your project files and restarts the app automatically.
Works with any Node.js application – Can be used with Express, NestJS, or any other Node-based project.
Lightweight & Easy to Use – No configuration needed in most cases.



---

## Middleware in Simple Terms

Middleware is a function that runs **between** the request and response.

```js
app.use((req, res, next) => {
  console.log('Request received at:', new Date());
  next(); // pass control to the next middleware/route
});
```

---

## Functions of middleware
- Express helps you build APIs and web apps faster.
- Use different HTTP methods for different actions.
- Use middleware (`express.json()`) to parse JSON.
- `req.params` for route values like `/user/:id`
- `req.query` for URLs like `/search?keyword=abc`

---

# Dev Dependencies (Development Dependencies)
Dev dependencies are packages that are only needed during the development phase of a project—not in production.

They help developers write, test, and maintain code, but they are not required when the application is actually running.


# Some commonly used properties while defining a Schema using mongoose

```js
const mongoose = require('mongoose');

const userSchema = new mongoose.Schema({
  name: {
    type: String,           // Data type
    required: true,         // Makes the field mandatory
    trim: true              // Removes whitespace from both ends
  },
  age: {
    type: Number,
    min: 0,                 // Minimum value allowed
    max: 120                // Maximum value allowed
  },
  email: {
    type: String,
    unique: true,           // Ensures value is unique in the collection
    lowercase: true         // Converts string to lowercase before saving
  },
  isActive: {
    type: Boolean,
    default: true           // Default value if none is provided
  },
  tags: {
    type: [String],         // Array of strings
    default: []
  },
  createdAt: {
    type: Date,
    default: Date.now       // Automatically sets current timestamp
  }
});
```
---

# Bcrypt Common Methods (with Examples)

`bcrypt` is a popular Node.js library for securely hashing passwords.

---

## 1. `bcrypt.hash()`
**Purpose:** Hashes a password.

**Syntax:**
```javascript
bcrypt.hash(data, saltRounds)
```
- `data`: Plain text password.
- `saltRounds`: Number of rounds to generate the salt (common: 10–12).

**Example:**
```javascript
const bcrypt = require('bcrypt');

async function hashPassword(password) {
  const saltRounds = 10;
  const hashedPassword = await bcrypt.hash(password, saltRounds);
  console.log(hashedPassword);
}

hashPassword('myPassword123');
```

---

## 2. `bcrypt.compare()`
**Purpose:** Compares a plain text password with a hashed password.

**Syntax:**
```javascript
bcrypt.compare(data, hashedPassword)
```
- Returns `true` if matched, otherwise `false`.

**Example:**
```javascript
const bcrypt = require('bcrypt');

async function checkPassword(password, hashedPassword) {
  const match = await bcrypt.compare(password, hashedPassword);
  if (match) {
    console.log("Password matched!");
  } else {
    console.log("Password incorrect.");
  }
}

// Example usage
const plainPassword = 'myPassword123';
const hashedPassword = '$2b$10$H9m5kH8q4Lj1Zi0W8F23zexfzMAtOcGp69/PKmWxXQw6zw6Hc/7bK'; // Example hash
checkPassword(plainPassword, hashedPassword);
```

---

## 3. `bcrypt.genSalt()`
**Purpose:** Generates a salt manually.

**Syntax:**
```javascript
bcrypt.genSalt(saltRounds)
```
- Generates salt for manual password hashing.

**Example:**
```javascript
const bcrypt = require('bcrypt');

async function manualHash(password) {
  const salt = await bcrypt.genSalt(10);
  const hashedPassword = await bcrypt.hash(password, salt);
  console.log(hashedPassword);
}

manualHash('myPassword123');
```

---

## ⚡ Bonus: Synchronous Versions

If you prefer not using `async/await`, `bcrypt` provides synchronous methods:

| Async Method         | Sync Version          |
| -------------------- | ---------------------- |
| `bcrypt.hash()`       | `bcrypt.hashSync()`     |
| `bcrypt.compare()`    | `bcrypt.compareSync()`  |
| `bcrypt.genSalt()`    | `bcrypt.genSaltSync()`  |

**Sync Example:**
```javascript
const bcrypt = require('bcrypt');

const salt = bcrypt.genSaltSync(10);
const hashedPassword = bcrypt.hashSync('myPassword123', salt);

const isMatch = bcrypt.compareSync('myPassword123', hashedPassword);
console.log(isMatch); // true
```

---

## 🔥 Quick Overview

| Method              | Purpose                                      |
| ------------------- | -------------------------------------------- |
| `hash()`            | Hashes a plain text password                 |
| `compare()`         | Compares plain text password with a hash     |
| `genSalt()`         | Creates a salt for hashing                   |
| `hashSync()`        | Synchronous password hashing                 |
| `compareSync()`     | Synchronous password comparing               |
| `genSaltSync()`     | Synchronous salt generation                  |

---

# Tips
- Recommended `saltRounds`: 10–12.
- Always `await` or use `Promise` methods when dealing with bcrypt asynchronously.
- Never store plain passwords! Always store **only the hashed** version.
- Once the password is hashed it cant be undone
  
---
#  JWT Backend Methods

A reference for commonly used JWT (JSON Web Token) methods in backend applications. This includes token creation, verification, refreshing, and storage strategies.

##  What is JWT?

JWT (JSON Web Token) is an open standard (RFC 7519) for securely transmitting information between parties as a JSON object. It's widely used for authentication and authorization in web applications.

---

## Common JWT Methods

### 1. **Token Creation (Signing)**

Used when a user logs in successfully.

```js
// Example using Node.js with jsonwebtoken
const jwt = require('jsonwebtoken');

const payload = { userId: 123 };
const secret = 'your-secret-key';
const options = { expiresIn: '1h' };

const token = jwt.sign(payload, secret, options);
```

### 2. **Token Verification**

Used to protect routes and ensure the request comes from an authenticated user.

```js
try {
  const decoded = jwt.verify(token, secret);
  console.log(decoded); // { userId: 123, iat: ..., exp: ... }
} catch (err) {
  // Handle invalid or expired token
}
```

### 3. **Token Refresh**

Used to issue a new token when the access token expires, without forcing the user to log in again.

```js
// Typically involves using a separate refresh token
const refreshToken = jwt.sign({ userId: 123 }, refreshSecret, { expiresIn: '7d' });
```

Then when the access token expires:

```js
// Validate refresh token and issue new access token
const newAccessToken = jwt.sign({ userId: 123 }, secret, { expiresIn: '1h' });
```

### 4. **Token Decoding Without Verification**

Useful when you just need to read the payload and don’t care if it’s valid.

```js
const decoded = jwt.decode(token); // No signature verification
```

### 5. **Storing Tokens**

- **Access Token**: Typically stored in memory or HTTP-only cookies.
- **Refresh Token**: Stored securely in HTTP-only cookies or secure storage.
- **Best Practice**: Never store tokens in localStorage on the frontend due to XSS risks.

---

## Best Practices

- Use short-lived access tokens (`15m - 1h`) and long-lived refresh tokens.
- Store secrets in environment variables.
- Use HTTPS to protect tokens in transit.
- Revoke refresh tokens on logout or suspicious activity.



# Common `res.status()` Codes in Express.js

When building APIs in Node.js with Express, you use `res.status()` to tell the client what happened. Below is a quick cheat sheet for the most commonly used status codes.

---

## Success Responses

| Status Code | Name    | Meaning                                      |
|-------------|---------|----------------------------------------------|
| `200`       | OK      | The request was successful                   |
| `201`       | Created | Something new was successfully created       |

---

## Client Errors

| Status Code | Name            | Meaning                                              |
|-------------|-----------------|------------------------------------------------------|
| `400`       | Bad Request     | The request was invalid (e.g. missing or bad data)   |
| `401`       | Unauthorized    | No token or login provided                          |
| `403`       | Forbidden       | You are not allowed to access this resource         |
| `404`       | Not Found       | The requested resource doesn’t exist                |
| `409`       | Conflict        | A conflict occurred (e.g. user already exists)      |

---

## Server Errors

| Status Code | Name                    | Meaning                                |
|-------------|-------------------------|----------------------------------------|
| `500`       | Internal Server Error   | Something went wrong on the server     |

---

## Code Examples

```js
res.status(200).json({ message: "Success" });
res.status(201).json({ message: "Created" });
res.status(400).json({ message: "Bad Request" });
res.status(401).json({ message: "Unauthorized" });
res.status(403).json({ message: "Forbidden" });
res.status(404).json({ message: "Not Found" });
res.status(409).json({ message: "Conflict" });
res.status(500).json({ message: "Server Error" });
```

# What Are Handlers in Express.js?

In **Express.js**, a **handler** is a function that gets called when a specific HTTP request hits the server. It handles the incoming request and sends an appropriate response.

---

## 1. Route Handlers

These are functions that handle HTTP routes.

```js
app.get('/hello', (req, res) => {
  res.send('Hello, world!');
});
```
- Here (req,res) are handlers


# Bearer Header
A Bearer header is an Authorization header that is used to securely send a token (usually a JWT) from the client to the server to prove the user's identity.

# What is req.headers["authorization"]?
When a user (client) sends a request to your server (like opening a page, logging in, etc.), it often includes some headers with extra information.

One of these headers is called `Authorization`
It usually contains login info, like a token or username & password.

**What the code does:**
- req.headers gives you all the headers sent in the request.

- req.headers["authorization"] gets the Authorization header specifically.

- authheader stores that info.

- console.log(authheader) prints it to the console (so developers can see it while debugging).


# How does file uploading works using Cloudinary and Multer :

- Client sends the file through a form using multipart/form-data.

- Multer (middleware) catches the file and temporarily stores it (either in memory or on disk).

- You then send that file to Cloudinary using their SDK.

- Cloudinary uploads the file and returns a URL (and other metadata).

- You store that URL (usually in your database) to use later (like showing the image on a page).


  # Multer package :
  
  Multer is a middleware for Express.js that helps you handle file uploads (like images, PDFs, videos, etc.) from forms (like an HTML form or a Postman request).
  
  Think of Multer as the tool that reads a file from a form and makes it usable in your backend code.

  # 🔧 Why Do We Need Multer?
  By default, Express can’t understand files — it only understands text data like JSON or URL-encoded data.

  If someone uploads a file (e.g., a photo), Express needs help to extract and save it. That’s where Multer comes in.

  # Application of multer :

  - Parses multipart/form-data (the encoding type used for file uploads)

  - Stores the file temporarily (either on disk or in memory)

  - Attaches the file info to req.file so you can access it easily in your route













