# You dont know Js

The _You Don't Know JS_ (YDKJS) series aims to teach JavaScript thoroughly, challenging readers to understand the language deeply, not just superficially. The first book, _Up & Going_, introduces basic programming concepts, especially for beginners, and provides a quick overview of JavaScript. It encourages readers to explore beyond the basics and dive into the deeper parts of the language. The series focuses on mastering JavaScript's complexities, moving beyond simple "copy-paste" learning, to develop a strong, practical understanding of the language.

### Summary 2

This section introduces programming concepts using JavaScript:

1. **Code and Statements**:
   - A **program** (source code) is a set of instructions for a computer.
   - **Statements** are instructions that perform specific tasks. Example:
     ```javascript
     a = b * 2;
     ```
     - `a` and `b` are variables, `*` is an operator, and `2` is a literal value.
2. **Expressions**:

   - **Expressions** are combinations of variables, values, and operators.
   - In `a = b * 2;`, the expression parts are:
     - `2` (literal value)
     - `b` (variable)
     - `b * 2` (arithmetic expression)
     - `a = b * 2` (assignment expression)

3. **Executing a Program**:

   - Code is executed by **interpreting** or **compiling** (JavaScript is typically interpreted).
   - The JavaScript engine compiles the code on the fly and then runs it.

4. **Practical Code Examples**:
   - **Running Code in Console**: Type JavaScript in the browser's developer console.
   ```javascript
   a = 21;
   b = a * 2;
   console.log(b); // Output: 42
   ```
   - **Output**: `console.log(..)` prints values in the console.
   - **Input**: `prompt(..)` takes input from the user.
   ```javascript
   age = prompt("Please tell me your age:");
   console.log(age);
   ```

### Key Points:

- Statements, expressions, and operators form the core of a program.
- JavaScript executes in the browser console using `console.log(..)` for output.
- **Input** can be captured with `prompt(..)` for simple tasks.

### Example Code:

```javascript
// Example 1: Statement and Expression
let a = 21;
let b = a * 2;
console.log(b); // Output: 42

// Example 2: Taking Input and Output
let age = prompt("Please tell me your age:");
console.log(age); // Output: User input
```

### Summary 3

This section focuses on **operators**, **values & types**, and **comments** in JavaScript:

1. **Operators**:

   - Operators perform actions on values and variables.
   - **Assignment operator** `=`: Assigns the value on the right to the variable on the left.
     ```javascript
     a = 2; // a is assigned 2
     ```
   - **Math operators**: `+` (addition), `-` (subtraction), `*` (multiplication), `/` (division).
   - **Compound assignment operators**: `+=`, `-=`, `*=`, `/=` (e.g., `a += 2` is the same as `a = a + 2`).
   - **Increment/Decrement**: `++` (increment), `--` (decrement), e.g., `a++`.
   - **Equality operators**: `==`, `===`, `!=`, `!==`.
   - **Comparison operators**: `<`, `>`, `<=`, `>=`.
   - **Logical operators**: `&&` (AND), `||` (OR).

2. **Values & Types**:

   - Types represent how data is used:
     - **Number** for math (e.g., `42`).
     - **String** for text (e.g., `"Hello"`).
     - **Boolean** for true/false values.
   - **Literals**: Direct values like `42`, `"Hello"`, `true`.
   - **Type conversion (coercion)**: JavaScript can automatically or explicitly convert between types.
     ```javascript
     var a = "42";
     var b = Number(a); // Coerce string "42" to number 42
     console.log(b); // Output: 42
     ```

3. **Code Comments**:
   - Comments help explain the code to humans. They are ignored by the compiler/interpreter.
   - **Single-line comment**: `// This is a comment`.
   - **Multi-line comment**: `/* This is a multi-line comment */`.
   - Good comments explain _why_ the code is written a certain way, not just _what_ it does.
   - Example:
     ```javascript
     var a = 42; // This stores the meaning of life
     ```

### Example Code:

```javascript
// Assignment and math operations
let a = 5;
let b = a * 2; // b is now 10

// Compound assignment
a += 3; // a becomes 8

// Increment and Decrement
a++; // a becomes 9
b--; // b becomes 9

// Equality and comparison
console.log(a == b); // true, because a and b are both 9

// Type conversion
let str = "123";
let num = Number(str); // Converts string to number
console.log(num); // 123

// Comments
/* This is a multi-line comment
   explaining the following code */
let answer = 42; // Answer to the ultimate question
```

### Key Points:

- **Operators** perform actions like assigning, comparing, or performing arithmetic.
- **Types** categorize data, such as numbers and strings.
- **Comments** are for explaining the code to other developers, improving readability.

The passage you provided covers various fundamental programming concepts in JavaScript, focusing on **variables**, **blocks**, **conditionals**, and **loops**. Let’s summarize and break down these key ideas:

### Variables

- **Variables** are containers for storing data values that can change throughout the program. In JavaScript, variables are dynamically typed, meaning the type of value a variable holds can change.
  - Example: `var amount = 99.99;` assigns a number to `amount`. Later, this value can change, such as `amount = "$" + String(amount);`, converting the number to a string and adding a "$" sign.
  - **Constants**: Variables that should not change after being set are often declared using a convention (uppercase with underscores, e.g., `TAX_RATE = 0.08`). In ES6, `const` is used to prevent reassignment of a variable.

### Blocks

- A **block** groups multiple statements together and is defined by curly braces `{ }`.
  - Blocks are most commonly used in control statements like **if** and **loops**.
  - Example of a block used in an `if` statement:
    ```javascript
    if (amount > 10) {
      amount = amount * 2;
      console.log(amount); // Output: 199.98
    }
    ```

### Conditionals

- **Conditionals** allow programs to make decisions based on whether a condition is true or false. The most common conditional statement is `if`, which runs a block of code if the condition is true.
  - Example:
    ```javascript
    if (amount < bank_balance) {
      console.log("I want to buy this phone!");
    }
    ```
- **Else**: An optional `else` block can run if the `if` condition is false.

  - Example:
    ```javascript
    if (amount < bank_balance) {
      console.log("I'll take the accessory!");
    } else {
      console.log("No, thanks.");
    }
    ```

- **Truthy and Falsy values**: JavaScript automatically coerces values into `true` or `false`. Some values like `0` and `""` are "falsy" (coerce to `false`), while others like `99.99` and `"free"` are "truthy" (coerce to `true`).

### Loops

- **Loops** are used to repeat a block of code multiple times based on a condition.

  - A **while loop** executes a block as long as the condition is true:
    ```javascript
    while (numOfCustomers > 0) {
      console.log("How may I help you?");
      numOfCustomers = numOfCustomers - 1;
    }
    ```
  - A **do..while loop** is similar but guarantees at least one execution of the loop block before checking the condition:
    ```javascript
    do {
      console.log("How may I help you?");
      numOfCustomers = numOfCustomers - 1;
    } while (numOfCustomers > 0);
    ```

- **For loop** is typically used for counting iterations:

  ```javascript
  for (var i = 0; i <= 9; i = i + 1) {
    console.log(i); // Outputs numbers 0 to 9
  }
  ```

  - The `for` loop has three parts:
    1. **Initialization**: `var i = 0`
    2. **Condition**: `i <= 9`
    3. **Update**: `i = i + 1`

- **Breaking out of loops**: You can use `break` to stop the loop at any point when a certain condition is met.

---

These concepts, particularly **variables**, **conditionals**, and **loops**, form the foundation of most programming tasks. They allow programs to store and manipulate data, make decisions based on conditions, and repeat tasks efficiently.

This section focuses on key programming concepts that help organize code and make it more efficient, particularly in JavaScript. Here's a summary and breakdown of the main ideas covered:

### 1. **Functions**

Functions are reusable blocks of code designed to perform specific tasks. By using functions, we can avoid repetition and make our code more organized and modular. Here's how they work:

- A function can take **parameters** (inputs) and **return values** (outputs).
- You can call a function by its name, and it will execute the code within it.

**Example:**

```javascript
function printAmount(amt) {
  console.log(amt.toFixed(2));
}
var amount = 99.99;
printAmount(amount); // Output: 99.99
amount = amount * 2;
printAmount(amount); // Output: 199.98
```

### 2. **Scope**

Scope in programming refers to the context in which variables are accessible. JavaScript uses **lexical scope**, meaning that a function can access variables defined in its outer scopes, but not vice versa.

**Example:**

```javascript
function outer() {
  var a = 1;
  function inner() {
    var b = 2;
    console.log(a + b); // 3 (inner has access to both `a` and `b`)
  }
  inner();
  console.log(a); // 1 (outer can access `a`, but not `b`)
}
outer();
```

### 3. **Organizing Code with Functions**

Functions can help organize related blocks of code into reusable, named units. This not only makes the code cleaner but also aids in better readability and maintenance.

**Example:**

```javascript
const TAX_RATE = 0.08;
function calculateFinalPurchaseAmount(amt) {
  amt = amt + amt * TAX_RATE; // Adds tax to the amount
  return amt;
}
var amount = 99.99;
amount = calculateFinalPurchaseAmount(amount);
console.log(amount.toFixed(2)); // Output: 107.99
```

### 4. **Practice Problem**

The practice problem encourages applying the concepts learned by writing a program to calculate the total cost of purchasing phones, accessories, and taxes. The program should:

- Keep purchasing phones until you run out of money.
- Add accessories to each phone if the total is below a given threshold.
- Calculate the final purchase amount with tax.
- Check if the total amount is affordable given the bank balance.

Here's an example solution in JavaScript:

```javascript
const SPENDING_THRESHOLD = 200;
const TAX_RATE = 0.08;
const PHONE_PRICE = 99.99;
const ACCESSORY_PRICE = 9.99;
var bank_balance = 303.91;
var amount = 0;

function calculateTax(amount) {
  return amount * TAX_RATE;
}

function formatAmount(amount) {
  return "$" + amount.toFixed(2);
}

while (amount < bank_balance) {
  amount = amount + PHONE_PRICE; // Buy a new phone
  if (amount < SPENDING_THRESHOLD) {
    amount = amount + ACCESSORY_PRICE; // Add an accessory if below threshold
  }
}

amount = amount + calculateTax(amount); // Add tax
console.log("Your purchase: " + formatAmount(amount)); // Display total purchase

if (amount > bank_balance) {
  console.log("You can't afford this purchase. :("); // Check affordability
}
```

### 5. **Key Programming Concepts**

- **Operators:** Perform operations on values (e.g., `+`, `-`, `*`, `/`).
- **Variables:** Store data (e.g., strings, numbers, etc.).
- **Conditionals (if statements):** Make decisions based on conditions.
- **Loops:** Repeat tasks until a condition is met.
- **Functions:** Organize your code into reusable blocks.
- **Comments:** Help make code readable and maintainable.

### 6. **Importance of Practice**

The key takeaway is that learning programming is best done through **practice**. Try out examples, experiment with different values, and continue working on problems to improve your skills.

### Conclusion

This chapter has covered essential programming concepts such as functions, scope, loops, conditionals, and the importance of organization. The example problem shows how to apply these concepts to build a more complex program in a structured manner, enhancing your ability to solve real-world problems.

# Chapter 2

This chapter introduces fundamental JavaScript concepts and gives a foundational overview of key topics you'll need to understand as a JavaScript developer. Here's a summary of the key ideas from this section:

### Values & Types

- **JavaScript has typed values, not typed variables.** Variables store values, and each value has a specific type.
- The main data types in JavaScript are:

  - `string`
  - `number`
  - `boolean`
  - `null` and `undefined`
  - `object`
  - `symbol` (introduced in ES6)

- The `typeof` operator helps identify the type of a value.
  ```javascript
  var a;
  console.log(typeof a); // "undefined"
  a = "hello world";
  console.log(typeof a); // "string"
  a = 42;
  console.log(typeof a); // "number"
  a = true;
  console.log(typeof a); // "boolean"
  a = null;
  console.log(typeof a); // "object" (a known JavaScript bug)
  ```

### Objects

- An **object** is a collection of properties with names (keys) and corresponding values.
  ```javascript
  var obj = {
    a: "hello world",
    b: 42,
    c: true,
  };
  console.log(obj.a); // "hello world"
  console.log(obj["b"]); // 42
  ```

### Arrays

- An **array** is a special type of object where values are indexed numerically.
  ```javascript
  var arr = ["hello world", 42, true];
  console.log(arr[0]); // "hello world"
  console.log(arr.length); // 3
  ```

### Functions

- **Functions** are also objects in JavaScript, and can have properties.
  ```javascript
  function foo() {
    return 42;
  }
  foo.bar = "hello world";
  console.log(typeof foo); // "function"
  console.log(foo.bar); // "hello world"
  ```

### Built-In Type Methods

- Each data type (string, number, etc.) has built-in methods to interact with them. For example, strings have methods like `.toUpperCase()`, and numbers have `.toFixed()`.
  ```javascript
  var a = "hello world";
  console.log(a.toUpperCase()); // "HELLO WORLD"
  var b = 3.14159;
  console.log(b.toFixed(4)); // "3.1416"
  ```

### Coercion

- **Coercion** refers to converting values between types, either explicitly (by you) or implicitly (by JavaScript during operations).
  - **Explicit coercion** happens when you manually convert a value to another type, like using `Number()`.
    ```javascript
    var a = "42";
    var b = Number(a); // 42
    ```
  - **Implicit coercion** happens when JavaScript converts values during an operation.
    ```javascript
    var a = "42";
    var b = a * 1; // Implicit coercion from string to number
    console.log(b); // 42
    ```

### Truthy & Falsy Values

- **Truthy** values are values that, when coerced to a boolean, are `true`.
- **Falsy** values are values that coerce to `false`. The falsy values include:

  - `""` (empty string)
  - `0`, `-0`, `NaN` (invalid number)
  - `null`, `undefined`
  - `false`

  All other values are **truthy** (e.g., `"hello"`, `42`, `true`, `[ ]`, `{ }`, and functions).

### Equality Operators

- JavaScript has several equality operators:

  - `==` (loose equality): Compares values and allows **type coercion**.
  - `===` (strict equality): Compares values without **type coercion**.
  - `!=` (loose inequality) and `!==` (strict inequality).

- It’s generally better to use `===` to avoid unexpected type coercion.
  ```javascript
  var a = "42";
  var b = 42;
  console.log(a == b); // true (due to coercion)
  console.log(a === b); // false (no coercion)
  ```

### Key Takeaways

- **Always use `===`** for comparisons unless you specifically need type coercion (e.g., for loose comparisons).
- **Use arrays for indexed collections** of data and objects for named properties.
- Understand **coercion** and **truthy/falsy** values to avoid unexpected behavior in your code.

This chapter lays the groundwork for more advanced concepts covered in the **YDKJS (You Don't Know JS)** series, and it encourages experimenting with the code to reinforce learning. Be patient and review these concepts as needed to build a solid understanding of JavaScript.

This section of text provides a deep dive into some important concepts in JavaScript, particularly variables, scoping, functions, and best practices.

### **Variables**

In JavaScript, variables are identifiers that must adhere to specific naming rules. An identifier can start with letters (`a-z`, `A-Z`), dollar sign (`$`), or underscore (`_`), and can include numbers (`0-9`) after the initial character. For example, `let name = "John";` is valid, but `let 2name = "John";` is not.

There are reserved words in JavaScript that cannot be used as variable names (such as `for`, `if`, `null`, `true`, `false`), as these are reserved for the language’s syntax.

### **Function Scopes and Hoisting**

- **Function Scopes**: Variables declared with `var` inside a function are scoped to that function, meaning they are only accessible within the function or any nested functions within it.
- **Hoisting**: JavaScript hoists variable declarations to the top of their scope, meaning that even if you declare a variable later in the code, the variable declaration is conceptually moved to the top. This behavior applies to function declarations as well. However, hoisting can lead to unexpected results if not understood properly, especially when dealing with variables declared using `var`.

### **Nested Scopes**

Variables declared inside a function or block (like `if` or `while` statements) are accessible only within that scope or nested scopes. Variables from an outer scope are available to inner scopes, but not vice versa.

For example:

```javascript
function foo() {
  var a = 1;
  function bar() {
    var b = 2;
    function baz() {
      var c = 3;
      console.log(a, b, c); // 1 2 3
    }
    baz();
    console.log(a, b); // 1 2
  }
  bar();
  console.log(a); // 1
}
foo();
```

Here, variable `a` is available in all nested functions, `b` is available only inside `bar()`, and `c` is available only inside `baz()`.

### **Strict Mode**

Strict mode (`"use strict";`) was introduced in ECMAScript 5 to enforce stricter parsing and error handling in JavaScript. It helps avoid potential problems by catching common coding errors, like using undeclared variables. In strict mode, assignments to undeclared variables result in a `ReferenceError`.

Example:

```javascript
"use strict";
a = 1; // This will throw a ReferenceError because 'a' is not declared.
```

### **Functions as Values**

Functions in JavaScript are first-class objects, meaning they can be assigned to variables, passed as arguments, and returned from other functions. Functions can be declared anonymously (without a name) or named. The following are examples of function expressions:

```javascript
var foo = function () {
  /*...*/
}; // anonymous function
var x = function bar() {
  /*...*/
}; // named function expression
```

### **Immediately Invoked Function Expressions (IIFE)**

An IIFE is a function expression that is executed immediately after it is defined. It’s often used to create a new scope for variables without polluting the global scope.

Example:

```javascript
(function IIFE() {
  console.log("Hello!"); // "Hello!"
})();
```

An IIFE can also return values:

```javascript
var x = (function IIFE() {
  return 42;
})();
console.log(x); // 42
```

### **Block Scoping with `let`**

ES6 introduced `let`, which allows block-level scoping (scope limited to a block enclosed by `{}`), unlike `var`, which is function-scoped. This makes it easier to control the visibility of variables within specific blocks, reducing issues related to variable leakage in the broader scope.

Example:

```javascript
function foo() {
  var a = 1;
  if (a >= 1) {
    let b = 2;
    while (b < 5) {
      let c = b * 2;
      b++;
      console.log(a + c);
    }
  }
}
foo();
// Output: 5, 7, 9
```

Here, `b` is scoped to the `if` block and `c` is scoped to the `while` loop, meaning they are not accessible outside of their respective blocks.

### **Conditionals**

In JavaScript, `if`, `else if`, and `else` are used for conditional checks. Alternatively, a `switch` statement can handle multiple conditions, and the conditional (ternary) operator provides a shorthand for simple if-else statements.

Example:

```javascript
var a = 42;
var b = a > 41 ? "hello" : "world"; // b = "hello"
```

### **Conclusion**

Understanding JavaScript’s scoping rules, strict mode, function expressions, and conditionals is crucial for writing clean, efficient code. Proper use of variable declaration (`var`, `let`, `const`), function scopes, and the correct handling of hoisting and block-level scoping (via `let` and `const`) leads to fewer bugs and more predictable behavior in JavaScript programs. Additionally, utilizing strict mode and IIFEs can help ensure safer and more modular code.

### Summary of Key Concepts from the Excerpt:

1. **Closure**:

   - A closure in JavaScript allows a function to remember and access its lexical scope, even after the outer function has finished executing.
   - Example: `makeAdder(x)` creates a closure, where the inner function `add(y)` remembers the value of `x` even after `makeAdder` finishes. This allows for the creation of functions like `plusOne` and `plusTen` that retain their respective `x` values (1 and 10) even when called later.

2. **Modules and Closures**:

   - Closures are commonly used in JavaScript to create **modules**, which allow for data encapsulation. A module can have private variables and methods that are not accessible from the outside world, while exposing a public API.
   - Example: The `User` function creates a module with private `username` and `password` variables. The `doLogin` function has a closure over these variables, allowing the module to manage login details securely.

3. **The `this` Keyword**:

   - The value of `this` in JavaScript is determined by how a function is called, not by how it is defined. It typically refers to an object, but the specific object depends on the function's call context.
   - Example:
     - In `foo()`, `this` refers to the global object.
     - In `obj1.foo()`, `this` refers to `obj1`.
     - `foo.call(obj2)` explicitly sets `this` to `obj2`.
     - `new foo()` creates a new object, setting `this` to that object.

4. **Prototypes**:

   - JavaScript uses **prototypes** to implement inheritance. If a property or method doesn't exist on an object, JavaScript looks up the object's prototype chain.
   - Example: `bar` is linked to `foo` via `Object.create(foo)`, so if `bar` doesn't have a property `a`, it will look for it on `foo`.

5. **Polyfilling and Transpiling**:

   - **Polyfilling**: Involves writing code that simulates newer JavaScript features in older environments that don't support them.
   - **Transpiling**: Involves using a tool (like Babel) to convert new JavaScript syntax into older syntax that older browsers can understand. This allows developers to use newer features without worrying about browser support.

6. **Non-JavaScript Components**:
   - Not all objects and functions in JavaScript are part of the language itself. Some, like the `document` object in browsers (part of the DOM API) and functions like `alert()`, are provided by the host environment (e.g., the browser) rather than the JavaScript engine.
   - These host objects are often treated as JavaScript objects but are essentially interfaces to native browser functionality.

### Review:

- **Fundamentals**: To understand JavaScript well, it's essential to grasp the language’s core features, such as closures, `this`, prototypes, and modules.
- **Advanced Concepts**: As you grow more familiar with these basics, you will be able to dive deeper into JavaScript’s more advanced capabilities, such as polyfilling, transpiling, and working with non-JavaScript components like the DOM.

Understanding these core concepts will serve as a foundation for more complex topics and allow you to write more effective and efficient JavaScript code.
