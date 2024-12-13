To build a **simple page with server-side rendering (SSR)**, we can use **Node.js** and **Express** (a popular web framework for Node.js). Here, I'll walk you through the process step-by-step to create a basic SSR page, where the server will render the HTML and send it to the client.

### Steps to Build a Simple SSR Page

#### 1. Set Up Node.js and Express
First, we need to set up **Node.js** and **Express** in your project.

1. **Initialize a New Project**:
   Open your terminal and run the following commands to set up a new Node.js project:

   ```bash
   mkdir ssr-example
   cd ssr-example
   npm init -y
   ```

2. **Install Express**:
   Now, install **Express**, a minimal web framework for Node.js:

   ```bash
   npm install express
   ```

---

#### 2. Create the Server (Server-Side Logic)

Next, we will create the main server file, where Express will handle the server-side logic and render an HTML page on request.

1. **Create `server.js`**:
   In the project folder, create a new file called `server.js`.

   Inside `server.js`, we will create a simple Express server that renders an HTML page with some dynamic content.

   ```js
   const express = require('express');
   const app = express();
   const port = 3000;

   // Sample data
   const products = [
     { id: 1, name: 'Product 1', price: 10 },
     { id: 2, name: 'Product 2', price: 20 },
     { id: 3, name: 'Product 3', price: 30 }
   ];

   // Route to render the page
   app.get('/', (req, res) => {
     const productHTML = products
       .map(product => `<li>${product.name} - $${product.price}</li>`)
       .join('');
     
     const html = `
       <html>
         <head><title>Server-Side Rendering Example</title></head>
         <body>
           <h1>Welcome to SSR Page</h1>
           <h2>Product List:</h2>
           <ul>
             ${productHTML}
           </ul>
         </body>
       </html>
     `;
     res.send(html);  // Send the HTML to the client
   });

   // Start the server
   app.listen(port, () => {
     console.log(`Server running at http://localhost:${port}`);
   });
   ```

   Here’s what’s happening in the code above:
   - We create a basic **Express server**.
   - The route `GET /` sends back an HTML page with a list of products.
   - The `productHTML` is dynamically generated using the `products` array (containing product name and price).
   - Finally, the **HTML** is sent as a response to the client.

---

#### 3. Run the Server

Once you’ve created `server.js`, run the server by typing the following command in your terminal:

```bash
node server.js
```

This will start the server on `http://localhost:3000`.

---

#### 4. Open the SSR Page in the Browser

Now, open your browser and visit `http://localhost:3000`.

You should see a simple page with a list of products. This is a server-side rendered page where the HTML was generated on the server and sent to the browser:

```
Welcome to SSR Page
Product List:
- Product 1 - $10
- Product 2 - $20
- Product 3 - $30
```

---

#### 5. Explanation of SSR Flow

1. **Request**: The client (browser) sends a request to the server for the root path `/` (i.e., `http://localhost:3000`).
2. **Server Processing**: The server receives the request, fetches the product data from the `products` array, and dynamically generates the HTML content.
3. **Rendering HTML**: The HTML content is rendered on the server and sent as a response to the client.
4. **Client Display**: The browser receives the complete HTML and renders it immediately, displaying the product list.

---

### Optional: Adding a CSS File

You can add styles to the SSR page by linking a CSS file. Here's how:

1. **Create a CSS file**: Create a file named `styles.css` in the same folder with the following content:

   ```css
   body {
     font-family: Arial, sans-serif;
     margin: 0;
     padding: 0;
     background-color: #f4f4f4;
     color: #333;
   }

   h1 {
     color: #333;
     text-align: center;
   }

   h2 {
     color: #555;
   }

   ul {
     list-style-type: none;
     padding: 0;
   }

   li {
     background-color: #fff;
     margin: 5px 0;
     padding: 10px;
     border-radius: 5px;
     box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
   }
   ```

2. **Link the CSS File**: In your `server.js`, update the HTML response to include the CSS file:

   ```js
   const html = `
     <html>
       <head>
         <title>Server-Side Rendering Example</title>
         <link rel="stylesheet" href="/styles.css">
       </head>
       <body>
         <h1>Welcome to SSR Page</h1>
         <h2>Product List:</h2>
         <ul>
           ${productHTML}
         </ul>
       </body>
     </html>
   `;
   ```

3. **Serve the CSS File**: Add a static file server to Express by using `express.static` to serve the CSS file:

   ```js
   app.use(express.static(__dirname)); // Serve static files in the current directory
   ```

Now, when you refresh the page at `http://localhost:3000`, the CSS will be applied, and the page will look much better.

---

### Conclusion

You've successfully created a simple **Server-Side Rendered (SSR)** page using **Node.js** and **Express**. The server dynamically generates HTML and sends it to the client in response to a request, ensuring faster loading times and better SEO.

This is just the basics, but SSR can be used with more complex logic and even templates or rendering engines like **EJS**, **Pug**, or **Handlebars**. As your app grows, you can handle dynamic data fetching and rendering more complex pages as well.

If you wanted to expand this further, you could implement additional features like:
- Routing (e.g., for different pages or resources)
- Fetching data from an API or database
- Implementing a templating engine to manage complex HTML templates more efficiently.