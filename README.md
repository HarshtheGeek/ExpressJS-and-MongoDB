# Express_JS
The following repo will contain the notes and the code of Express js, a popular and lightweight web application framework for Node.js

# Example of Express JS routes

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














