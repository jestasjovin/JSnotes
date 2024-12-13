To render **divs** conditionally in JavaScript, you can use **if-else** statements, or **ternary operators** to decide which elements should be displayed based on certain conditions (like authentication status, data availability, or user interaction).

Here are several approaches to render divs conditionally:

---

### **1. Using If-Else Condition**

You can use an **if-else** statement to determine whether to display a specific **div** based on a condition.

#### **Example 1: Show/Hide div based on a condition (Authentication)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conditional Rendering</title>
</head>
<body>
    <h1>Conditional Rendering Example</h1>

    <div id="welcome-message"></div>
    <div id="login-message"></div>

    <script>
        // Simulate whether the user is logged in or not
        let isLoggedIn = false;

        // Conditionally render the divs
        if (isLoggedIn) {
            document.getElementById('welcome-message').innerHTML = "<h2>Welcome back, User!</h2>";
            document.getElementById('login-message').style.display = 'none';  // Hide login message
        } else {
            document.getElementById('login-message').innerHTML = "<h2>Please log in.</h2>";
            document.getElementById('welcome-message').style.display = 'none';  // Hide welcome message
        }
    </script>
</body>
</html>
```

In this example:
- The `isLoggedIn` variable controls whether the **welcome message** or the **login message** is shown.
- If `isLoggedIn` is `true`, the welcome message will be displayed, and the login message will be hidden.
- If `isLoggedIn` is `false`, the login message will be shown, and the welcome message will be hidden.

---

### **2. Using Ternary Operator**

You can use the **ternary operator** to conditionally render divs directly in JavaScript.

#### **Example 2: Render div based on a condition (Is logged in or not)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conditional Rendering with Ternary</title>
</head>
<body>
    <h1>Conditional Rendering Example with Ternary Operator</h1>

    <div id="message"></div>

    <script>
        let isLoggedIn = true; // Change to false to test

        // Use ternary operator for conditional rendering
        document.getElementById('message').innerHTML = isLoggedIn
            ? "<h2>Welcome back, User!</h2>"
            : "<h2>Please log in.</h2>";
    </script>
</body>
</html>
```

In this example:
- The ternary operator checks the `isLoggedIn` condition.
- If `isLoggedIn` is `true`, it renders the welcome message.
- If `isLoggedIn` is `false`, it renders the "Please log in" message.

---

### **3. Conditional Rendering Based on Multiple Conditions**

You can combine **multiple conditions** using logical operators to conditionally render **divs** based on more complex criteria.

#### **Example 3: Conditionally Render Multiple Divs Based on Different Criteria**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Multiple Conditional Rendering</title>
</head>
<body>
    <h1>Conditional Rendering Example</h1>

    <div id="user-status"></div>
    <div id="content"></div>

    <script>
        let userRole = "admin"; // Can be "admin", "user", or "guest"
        let isLoggedIn = true;  // Change to false to test

        // Conditionally render divs based on user role and login status
        if (isLoggedIn) {
            if (userRole === "admin") {
                document.getElementById('user-status').innerHTML = "<h2>Welcome, Admin!</h2>";
                document.getElementById('content').innerHTML = "<p>You have full access to the dashboard.</p>";
            } else if (userRole === "user") {
                document.getElementById('user-status').innerHTML = "<h2>Welcome, User!</h2>";
                document.getElementById('content').innerHTML = "<p>You can view your profile.</p>";
            }
        } else {
            document.getElementById('user-status').innerHTML = "<h2>Please log in.</h2>";
            document.getElementById('content').innerHTML = "<p>You must log in to view content.</p>";
        }
    </script>
</body>
</html>
```

In this example:
- There are two conditions: whether the user is logged in (`isLoggedIn`) and the user's role (`userRole`).
- Based on the combination of these two conditions, different messages and content are rendered in the `#user-status` and `#content` divs.
- You can adjust the `userRole` and `isLoggedIn` values to see different render outcomes.

---

### **4. Conditional Rendering with Loops**

If you have an array of data and you want to conditionally render multiple divs based on certain values, you can loop through the data and use conditionals inside the loop.

#### **Example 4: Conditionally Render List Items Based on Array Values**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conditional Rendering in Loops</title>
</head>
<body>
    <h1>Conditional Rendering Example with Array</h1>

    <div id="product-list"></div>

    <script>
        // Sample product data
        const products = [
            { name: 'Laptop', inStock: true },
            { name: 'Smartphone', inStock: false },
            { name: 'Tablet', inStock: true },
        ];

        // Loop through the products array and conditionally render items based on stock availability
        let productListHtml = '';
        products.forEach(product => {
            if (product.inStock) {
                productListHtml += `<div class="product"><h3>${product.name}</h3><p>In stock</p></div>`;
            } else {
                productListHtml += `<div class="product"><h3>${product.name}</h3><p>Out of stock</p></div>`;
            }
        });

        document.getElementById('product-list').innerHTML = productListHtml;
    </script>
</body>
</html>
```

In this example:
- We have an array of **products**.
- Each product has a `name` and an `inStock` property.
- We loop through the array and check if each product is in stock or not. If it's in stock, we render a div with the text "In stock"; if it's not in stock, we render "Out of stock."

---

### **5. Using `display` or `visibility` to Hide/Show Divs**

You can conditionally **show or hide divs** by setting their `style.display` or `style.visibility` properties.

#### **Example 5: Conditionally Hide or Show a Div**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Conditional Show/Hide Div</title>
</head>
<body>
    <h1>Conditional Show/Hide Example</h1>

    <div id="special-offer" style="display:none;">
        <h2>Special Offer for You!</h2>
        <p>50% off on your next purchase.</p>
    </div>

    <button id="showOffer">Show Special Offer</button>

    <script>
        document.getElementById('showOffer').addEventListener('click', function() {
            const isSpecialOfferAvailable = true; // Change this value to control visibility

            if (isSpecialOfferAvailable) {
                document.getElementById('special-offer').style.display = 'block'; // Show the div
            } else {
                document.getElementById('special-offer').style.display = 'none'; // Hide the div
            }
        });
    </script>
</body>
</html>
```

In this example:
- Initially, the **special offer** div is hidden (`style.display = 'none'`).
- When the user clicks the button, the div will be shown or hidden based on the value of `isSpecialOfferAvailable`.

---

### **Summary**

- Use **if-else statements** for more complex conditions when deciding whether to render a div.
- Use the **ternary operator** for simpler, concise conditional rendering.
- **Loops** can be used to conditionally render multiple divs based on an array of data.
- Use **CSS properties** like `style.display` or `style.visibility` to hide or show divs dynamically.

These techniques will allow you to easily manage conditional rendering of divs in your JavaScript code.