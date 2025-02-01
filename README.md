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





