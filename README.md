# Express_JS
The following repo will contain the notes and the code of Express js, a popular and lightweight web application framework for Node.js

# Examoke of Express JS routes

```javascript
// Import the Express.js library
const express = require("express");

// Create an instance of an Express application
const app = express();

/**
 * Define a route for the root URL ("/")
 * This responds with a plain text message when the root URL is accessed.
 */
app.get("/", (req, res) => {
    res.send("Hello, if you are seeing this that means appka code sahi se work kar raha hai");
});

/**
 * Define a route for "/products"
 * This responds with a JSON array of products when the "/products" URL is accessed.
 */
app.get("/products", (req, res) => {
    // Array of sample products
    const Products = [
        {
            id: 1,
            label: 'Product 1',
        },
        {
            id: 2,
            label: 'Product 2',
        },
        {
            id: 3,
            label: 'Product 3',
        }
    ];
    // Send the products array as a JSON response
    res.json(Products);
});

// Define the port the server will listen on
const port = 3000;

// Start the server and log a message when it's running
app.listen(port, () => {
    console.log(`The server is now running at port ${port}`);
});
```

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

# MongogoDB and Mongoose

**MongoDB** is a NoSQL database that stores data in a flexible, JSON-like document format instead of the traditional table-based relational databases. It is schema-less, meaning documents in the same collection can have different structures. MongoDB is designed for scalability, high performance, and ease of development.

Key Features of MongoDB:

- Document-oriented storage (JSON-like BSON format)
- Schema-less (flexible data models)
- High availability with replication
- Horizontal scalability with sharding
- Rich query language for filtering, sorting, and aggregations

**Mongoose** is an ODM (Object Data Modeling) library for MongoDB in Node.js. It provides a schema-based solution to model application data, making MongoDB easier to work with.

Key Features of Mongoose:

Defines schemas for MongoDB collections
Provides built-in validation for data
Supports middleware (pre/post hooks for operations)
Enables relationships and virtuals between documents
Simplifies queries with powerful built-in methods

Here’s your content formatted properly for GitHub (Markdown format):  

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

#### Example (Defining a Schema in Mongoose):
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
```

This format is **GitHub-friendly** and can be used in **README.md** files or any Markdown-supported documentation. 🚀 Let me know if you need any modifications!








