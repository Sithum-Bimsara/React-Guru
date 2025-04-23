# Table of Contents
- [01.React_and_the_DOM](#React_and_the_DOM)
- [02.Creating_a_React_Application_with_Create_React_App](#Creating_a_React_Application_with_Create_React_App)
- [03.Hello_World_in_React](#Hello_World_in_React)
- [04.JavaScript_Objects](#JavaScript_Objects)
- [05.Understanding_the_this_Keyword_in_JavaScript](#Understanding_the_this_Keyword_in_JavaScript)
- [06.Understanding_this_and_the_bind_Method](#Understanding_this_and_the_bind_Method)
- [07.JavaScript_Arrow_Functions](#JavaScript_Arrow_Functions)
- [08.Understanding_Arrow_Functions_in_JavaScript](#Understanding_Arrow_Functions_in_JavaScript)
- [09.JavaScript_map_Method_with_Arrow_Functions](#JavaScript_map_Method_with_Arrow_Functions)
- [10.JavaScript_Object_Destructuring](#JavaScript_Object_Destructuring)

# React_and_the_DOM 

## Introduction to React ⚛️
React is a **JavaScript library** for building fast and interactive user interfaces. It was developed by **Facebook in 2011** and has become the most popular JavaScript library for UI development. As seen in **Google Trends**, React dominates over other frameworks like **Angular** and **Vue**.


## Components in React 🏗️
At the core of every React application are **components**. A component is essentially **a reusable piece of the user interface**.

- React applications are **composed of independent, isolated, and reusable components**.
- The **root component** represents the entire application and contains child components.
- Every React application is a **tree of components**.

### Example: Twitter 🐦
Imagine we're building a Twitter-like application. We can break it down into **components**:

```
App
├── Navbar
├── Profile
├── Trends
└── Feed
    ├── Tweet
    │   └── Like Button
    ├── Tweet
    │   └── Like Button
    └── Tweet
        └── Like Button
```

Here:
- `Navbar`, `Profile`, `Trends`, and `Feed` are top-level components.
- `Feed` contains multiple `Tweet` components.
- Each `Tweet` can have a `Like Button` component, **which can be reused anywhere**.

## How Components Work ⚙️
A React component is typically **a JavaScript class** that has:
1. **State** – Data that the component manages.
2. **Render method** – Describes what the UI should look like.

```jsx
class Tweet extends React.Component {
  render() {
    return <p>This is a Tweet! 📢</p>;
  }
}
```

The **render method returns a React element**, which is a **JavaScript object** that maps to a **DOM element**.

## Virtual DOM vs Real DOM 🖥️
### What is the Virtual DOM? 🌐
The **Virtual DOM (VDOM)** is a lightweight representation of the **Real DOM**.
- Unlike the **Real DOM**, the Virtual DOM is **faster and more efficient**.
- React uses the Virtual DOM to minimize updates to the **Real DOM**, which improves performance.

### How Does React Update the DOM? 🔄
1. When a component's **state changes**, React creates a **new Virtual DOM**.
2. It **compares** this new Virtual DOM with the previous one (using a process called **reconciliation**).
3. React **identifies the changes** and updates only the affected parts of the **Real DOM**.

💡 **This makes React much faster than directly manipulating the Real DOM using vanilla JavaScript or jQuery.**

## Why Use React Instead of Angular? ⚔️
- **React** is a **library**, while **Angular** is a **full-fledged framework**.
- React **only manages UI rendering**, whereas Angular provides solutions for **routing, HTTP calls, and more**.
- React's API is **small and easy to learn**.
- React allows developers to **choose their preferred libraries** instead of relying on built-in solutions.

## What is the DOM? 🌍
### Definition:
The **Document Object Model (DOM)** is a programming interface for web documents.
- It represents the structure of an HTML page **as a tree**.
- JavaScript can manipulate the DOM to change the **content, structure, and style** of a webpage.

### How the DOM Works? ⚙️
1. The browser **parses HTML** and converts it into a DOM tree.
2. JavaScript can interact with the DOM using **methods like `document.querySelector()` and `document.createElement()`**.
3. When JavaScript modifies the DOM, the browser **repaints the page**.

### Where is the DOM Used? 📍
- Every webpage loaded in a browser has a **DOM representation**.
- JavaScript frameworks like **React, Angular, and Vue** manipulate the DOM **to create dynamic web pages**.
- Direct DOM manipulation is **expensive** in performance, which is why React uses a **Virtual DOM** to optimize updates.

## Why is React Called "React"? 🤔
The name **React** comes from the fact that:
- When **state changes**, React **reacts** to the update by efficiently updating the UI.

## Conclusion 🎯
React is a **powerful and efficient** library for building UI components. With concepts like the **Virtual DOM**, component-based architecture, and **state management**, React makes modern web development **faster and more maintainable**. 🚀

---

# Creating_a_React_Application_with_Create_React_App

## 📌 Setting Up the React App

To create a new React application, open your terminal and run the following command:

```bash
npx create-react-app react-app
```

This command installs React along with essential third-party libraries, including:
- A lightweight development server 🌍
- Webpack for bundling files 📦
- Babel for compiling JavaScript ⚡
- Other necessary tools 🛠️

With **Create React App**, you don't need to worry about manual configuration. However, if customization is needed for a production environment, you can eject by running:

```bash
npm run eject
```

(⚠️ This action is irreversible, so use it cautiously!)

## 🏃 Running the React Application

Once installed, navigate into the project folder:

```bash
cd react-app
```

Start the development server:

```bash
npm start
```

This will:
- Launch the development server on **port 3000** 🌐
- Open your default browser pointing to `http://localhost:3000`

## 📂 Understanding the Project Structure

Let's explore the files and folders inside our React project:

### 1️⃣ `node_modules/` 📁
- Contains all third-party dependencies (including React itself)
- **You never need to modify this folder** 🚫

### 2️⃣ `public/` 📁
- Stores static assets like `index.html`, `favicon.ico`, and `manifest.json`
- `index.html` is a simple template containing:
  - Meta tags in the `<head>` section 🏷️
  - A `<div id="root">` in the `<body>` – **the main container for our React app**

### 3️⃣ `src/` 📁
- The heart of our React application ❤️
- Contains all the JavaScript and CSS files

## 📜 Exploring Key Files

### 🏗️ `App.js` - The Root Component

Inside `src/`, we have `App.js`, the main component responsible for rendering content.

```jsx
import React, { Component } from 'react';
import './App.css';

class App extends Component {
  render() {
    return <h1>Hello, React! 🚀</h1>;
  }
}

export default App;
```

Key takeaways:
- **Uses ES6 classes** 📚
- **Extends `Component`**, a built-in React class 🏗️
- **Implements a `render()` method**, which returns JSX 🖼️

### 🔹 What is JSX?
JSX (**JavaScript XML**) allows us to write HTML-like syntax inside JavaScript.

```jsx
const element = <h1>Hello, World! 🌍</h1>;
```

JSX is neither a string nor plain HTML. Behind the scenes, Babel compiles it into:

```js
React.createElement("h1", null, "Hello, World! 🌍");
```

So, it is easy to write JSX instead of writing plain react code like above.



### 🎨 `App.css` - Styling the App
- Contains styles specific to `App.js`
- Imported into `App.js` using `import './App.css';`

### 🧪 `App.test.js` - Testing (Not Covered Here)
- Used for unit testing React components ✅
- Skipped in this guide (covered in advanced courses)

### 🔥 `index.js` - Entry Point of the App
- **Bootstraps the entire React application** 🚀
- Uses `ReactDOM.render()` to mount the `App` component inside `#root`

### 🎭 `index.css`
- Defines global styles for the application 🌍

### 🏴‍☠️ `logo.svg`
- Default React logo used in the starter template 🎨

### 🛠️ `registerServiceWorker.js`
- Caches assets for offline use (may be removed in future versions) 📦

## 🎯 Conclusion

---

# Hello_World_in_React

## 🚀 Setting Up a React Project from Scratch

In this guide, we will delete all files inside the `src` folder and start fresh with a new `index.js` file. We will import necessary modules, define a React element, and render it inside the DOM. Let's get started! 🎉

---

## 🛠️ Importing React and ReactDOM

In modern JavaScript (ES6+), we use modules to import functionalities from different files. Here, we need to import `React` and `ReactDOM`:

```javascript
import React from "react";
import ReactDOM from "react-dom/client";
```

- `React` is the core library that allows us to create UI components.
- `ReactDOM` is used to render our components into the actual DOM.

---

## ✨ Creating a React Element

Now, let's create a simple React element:

```javascript
const element = <h1>Hello World</h1>;
```

- This is JSX (JavaScript XML), a syntax that looks like HTML but compiles to JavaScript.
- Babel, a JavaScript compiler, converts this JSX code into a function call to `React.createElement()`.

Why do we need to import React even though we don’t directly use it?
- JSX gets compiled into `React.createElement()`, so React must be in scope.

To confirm this, let's log the element:

```javascript
console.log(element);
```

### 🔍 Understanding JSX Compilation
The above JSX code:

```javascript
const element = <h1>Hello World</h1>;
```

compiles down to:

```javascript
const element = React.createElement("h1", null, "Hello World");
```

This is why we must import `React` at the top.

---

## 🖥️ Rendering the Element to the DOM

We need to render our React element inside the root div in `index.html`. Here’s how:

```javascript
const root = ReactDOM.createRoot(document.getElementById("root"));
root.render(element);
```

### 🔍 Breakdown of the Code
- `document.getElementById("root")` selects the `<div id="root"></div>` element in `index.html`.
- `ReactDOM.createRoot(...)` creates a root for rendering React components.
- `root.render(element)` renders our React element inside the selected DOM element.

After saving the file, check the browser. You should see:

```
Hello World
```

🔥 Congratulations! You've successfully rendered your first React element! 🎉

---

## 🌐 Understanding Virtual DOM

React uses a **Virtual DOM** to optimize UI updates.
- The `element` we logged earlier is not an actual DOM element but a **React Element**.
- This React Element is a lightweight representation of the actual DOM node.
- React compares the new virtual DOM with the previous one and updates only the changed parts.

Example:
1️⃣ Initial render → `h1` added to the DOM.
2️⃣ Update `h1` text → Only text content changes, not the entire element.

---

## 🔥 Hot Module Reloading (HMR)

Projects created with **Create React App** support Hot Module Reloading (HMR):
- Whenever you save changes, the app **automatically reloads**.
- No need to refresh the browser manually.

Try it:
1️⃣ Change `Hello World` to `Hello React!` in `index.js`.
2️⃣ Save the file.
3️⃣ The browser updates automatically! 🚀


---

# JavaScript_Objects

## 🏗️ Defining an Object
In JavaScript, objects are collections of **key-value pairs**. We can define an object using the `const` keyword:

```javascript
const person = {
    name: "John",
    walk: function() {
        console.log("Walking...");
    }
};
```

Here, we have:
- **`name`**: A property (key-value pair where the value is a string)
- **`walk`**: A method (a function inside an object) 🏃‍♂️

### 🎯 What is a Method?
📌 In **Object-Oriented Programming (OOP)**, a function inside an object is called a **method**.

## ✨ ES6 Method Syntax
Starting from **ES6**, there's a cleaner way to define methods in objects. Instead of using `function`, we can write:

```javascript
const person = {
    name: "John",
    walk() {
        console.log("Walking...");
    },
    talk() {
        console.log("Talking...");
    }
};
```

🚀 **What’s different?**
- No need for `:` (colon) or `function` keyword.
- Methods are now more readable and concise!

Now, our `person` object has:
- **1 Property** (`name`) 🏷️
- **2 Methods** (`walk` and `talk`) 🎙️

## 🎯 Accessing Object Members
There are **two ways** to access properties and methods in an object:

### 1️⃣ Dot Notation (Most Common)
```javascript
person.talk(); // Talking...
person.walk(); // Walking...
console.log(person.name); // John
```
✅ Simple & readable

### 2️⃣ Bracket Notation (Dynamic Access)
```javascript
person["walk"](); // Walking...
console.log(person["name"]); // John
```

🛠️ **Why Use Bracket Notation?**
Sometimes, we don’t know in advance what property or method we need to access. In such cases, **bracket notation** is useful.

Example:
```javascript
const targetMember = "name";
console.log(person[targetMember]); // John
```
🎯 This is helpful when working with **dynamic inputs**, like form fields!

### 🔥 Changing Property Values
```javascript
person.name = "Mike";
console.log(person.name); // Mike
```

📌 **When to Use Each Notation?**
- If you **know** the property/method name ahead of time → Use **dot notation** ✅
- If the property/method is **dynamic** → Use **bracket notation** 🔄

---

# Understanding_the_this_Keyword_in_JavaScript

## Introduction 📌
The `this` keyword in JavaScript is one of the most confusing concepts for developers, especially for those coming from languages like C# or Java. Unlike those languages, where `this` always refers to the current object, JavaScript behaves differently depending on how a function is called.

---

## Example: The `walk` Method 👣

Let's consider a `person` object with a `walk` method:

```javascript
const person = {
    walk() {
        console.log(this);
    }
};
```

Now, when we call `person.walk()`:

```javascript
person.walk();
```

### Output 📤
We see our `person` object logged in the console. ✅

**Why?** Because when a function is called as a method of an object, `this` refers to that object.

---

## What Happens When We Assign `walk` to a Constant? 🤔

Let's define a constant and assign it the `walk` method:

```javascript
const walk = person.walk;
console.log(walk);
```

### Output 📤
It logs the function definition to the console. ✅

Now, let's call the `walk` function:

```javascript
walk();
```

### Unexpected Output ❌
Instead of logging the `person` object, we get `undefined`. 😲

---

## Why Does `this` Become `undefined`? 🤯

🔹 The value of `this` is determined by **how** a function is called.

🔹 When a function is called as an **object method**, `this` refers to the object.

🔹 When a function is called **standalone (outside an object(`person`))**, `this` refers to the **global object** (i.e., `window` in browsers).

🔹 However, in this React project, `strict mode` is enabled by default. 

### What is Strict Mode? 🔒
Strict mode enforces better coding practices by preventing the accidental use of the global object. In strict mode:

- Instead of referencing `window`, `this` is set to `undefined` when calling a function standalone.
- This helps avoid unintended errors and makes JavaScript code safer.

---

## Key Takeaways 📝
✅ `this` inside an **object method** → Refers to the object itself.

✅ `this` inside a **standalone function** → Refers to `window` (unless in strict mode, where it is `undefined`).

✅ `strict mode` prevents accidental access to `window`, making JavaScript safer.

---

## Conclusion 🎯
Understanding `this` in JavaScript is crucial for writing effective code. Always remember:

🚀 **How** you call a function determines `this`.

🔍 In **strict mode**, `this` is `undefined` for standalone functions.

🛠️ Use `.bind()`, `call()`, or `apply()` to explicitly set `this` when necessary.

---

# Understanding_this_and_the_bind_Method

## 🔹 Recap from the Last Lecture

In the last lecture, you learned that when we call a function as a standalone function (outside of an object), the value of `this`:
- 🏠 Defaults to the **global object** (`window` in browsers) 🌍.
- ❗ If **strict mode** (`'use strict'`) is enabled, `this` returns `undefined` 🚫.

## 🔹 Fixing the `this` Problem

In this lecture, we will learn how to **fix** this issue so that no matter how we call the `walk` function, `this` will always reference the `person` object 👤.

### ✅ JavaScript Functions Are Objects
One new thing to note is that **functions in JavaScript are objects** 📦. 
- `person.walk` is actually an **object**.
- Don't believe it? Let's check:
  ```js
  console.log(person.walk);
  ```
- When we log this function, we can see that it has **multiple members** (properties and methods) 🔍.
- One of these methods is **`bind`**, which helps us solve our problem ✅.

## 🔹 The `bind` Method 🏷️
### How Does `bind` Work?
The `bind` method **attaches** a function to an object permanently.

```js
const walk = person.walk.bind(person);
walk();
```

### 🧐 Breaking It Down:
- `bind` **creates a new function** where `this` always refers to the `person` object.
- The **first argument** to `bind` determines the value of `this`.
- Since we pass `person` as an argument, the returned function **always references** `person` 🎯.

### ✅ Fixing Our Issue
Now, when we call the `walk` function, it correctly prints the `person` object to the console 🎉.

## 🔹 Quick Recap 📌
- 🏗️ **Functions in JavaScript are objects**.
- 🎭 **They have properties and methods**.
- 🔗 The **`bind` method** permanently binds `this` to a specific object.
- 📌 **Using `bind`, we ensure that `this` inside a function always refers to the expected object**.
- 🚀 `bind` is widely used in **React applications** to manage function references.

Now you understand how `bind` works and how it helps us control `this` in JavaScript! 🚀🔥

---

# Understanding_this_and the_bind_Method

## 🔹 Recap from the Last Lecture

In the last lecture, you learned that when we call a function as a standalone function (outside of an object), the value of `this`:
- 🏠 Defaults to the **global object** (`window` in browsers) 🌍.
- ❗ If **strict mode** (`'use strict'`) is enabled, `this` returns `undefined` 🚫.

## 🔹 Fixing the `this` Problem

In this lecture, we will learn how to **fix** this issue so that no matter how we call the `walk` function, `this` will always reference the `person` object 👤.

### ✅ JavaScript Functions Are Objects
One new thing to note is that **functions in JavaScript are objects** 📦. 
- `person.walk` is actually an **object**.
- Don't believe it? Let's check:
  ```js
  console.log(person.walk);
  ```
- When we log this function, we can see that it has **multiple members** (properties and methods) 🔍.
- One of these methods is **`bind`**, which helps us solve our problem ✅.

## 🔹 The `bind` Method 🏷️
### How Does `bind` Work?
The `bind` method **attaches** a function to an object permanently.

```js
const walk = person.walk.bind(person);
walk();
```

### 🧐 Breaking It Down:
- `bind` **creates a new function** where `this` always refers to the `person` object.
- The **first argument** to `bind` determines the value of `this`.
- Since we pass `person` as an argument, the returned function **always references** `person` 🎯.

### ✅ Fixing Our Issue
Now, when we call the `walk` function, it correctly prints the `person` object to the console 🎉.

## 🔹 Quick Recap 📌
- 🏗️ **Functions in JavaScript are objects**.
- 🎭 **They have properties and methods**.
- 🔗 The **`bind` method** permanently binds `this` to a specific object.
- 📌 **Using `bind`, we ensure that `this` inside a function always refers to the expected object**.
- 🚀 `bind` is widely used in **React applications** to manage function references.

Now you understand how `bind` works and how it helps us control `this` in JavaScript! 🚀🔥

---
# JavaScript_Arrow_Functions 

## 🎯 Introduction
JavaScript **Arrow Functions** provide a more concise way to write functions. They are especially useful in **callbacks, array methods**, and function expressions.

---

## 🔹 Syntax of an Arrow Function

### ✅ Traditional Function
```js
const squareNumber = function(number) {
    return number * number;
};
```

### ⚡ Arrow Function Equivalent
```js
const square = number => number * number;
console.log(square(2)); // 4
```

### 🔥 Key Differences:
- **No need for the `function` keyword**
- **Implicit return** if the function body contains a single expression
- **Shorter syntax** 📝

---

## 🌟 Example Usage
### 🏗️ Filtering Active Jobs

#### ✅ Using Traditional Function
```js
const jobs = [
    { id: 1, isActive: true },
    { id: 2, isActive: false },
    { id: 3, isActive: true }
];

const activeJobs = jobs.filter(function(job) {
    return job.isActive;
});
```

#### ⚡ Using Arrow Function
```js
const activeJobs = jobs.filter(job => job.isActive);
console.log(activeJobs); // [{ id:1, isActive: true }, { id:3, isActive: true }]
```

---

## 🎯 Advantages of Arrow Functions
✔️ **Concise Syntax** - Less boilerplate code 📌
✔️ **Implicit Return** - No need for `return` in single-expression functions 🎯
✔️ **Lexical `this`** - Arrow functions do not bind their own `this` context 🔥

---

## 🛑 Things to Keep in Mind
❌ Cannot be used as **constructors** (No `new` keyword usage)
❌ Do not have their own **`this`**, **`arguments`**, or **`super`**
❌ Not suitable for methods that require their own `this`

---

# Understanding_Arrow_Functions_in_JavaScript

## 📌 Key Concept: Arrow Functions Don't Rebind `this`

One crucial thing to know about arrow functions is that **they don't rebind `this`**. Let's break this down with an example. 👇

### 👤 Defining a `person` Object
We begin by defining a `person` object with a simple `talk` method:

```javascript
const person = {
  talk() {
    console.log(this);
  }
};
```

Now, when we call `person.talk()`, what do we expect to see in the console? 🧐

```javascript
person.talk();
```

✅ **Expected Output:** A reference to the `person` object.

---

### ⏳ Wrapping in `setTimeout`

Now, let's see what happens when we wrap this inside a `setTimeout` function:

```javascript
setTimeout(function() {
  console.log(this);
}, 1000);
```

After one second, what do we get in the console? 😲

❌ **Unexpected Output:** Instead of the `person` object, we get the `window` object!

### 🤔 Why Does This Happen?

This happens because the callback function inside `setTimeout` is **not part of any object**. Unlike the `talk` method, which belongs to `person`, this function is a **standalone function**. In JavaScript:

- When a function is called as a method on an object ➝ `this` refers to that object. ✅
- When a function is called standalone (not on an object) ➝ `this` refers to the global object (`window` in browsers, `global` in Node.js). ❌

📌 **Strict Mode Exception:** In strict mode, instead of returning `window`, `this` would be `undefined`.

---

### 🔄 The Old Solution: Using `self`

Before arrow functions, developers used a workaround to retain `this`:

```javascript
const person = {
  talk() {
    const self = this; // Store `this` in a variable
    setTimeout(function() {
      console.log(self); // Use `self` inside callback
    }, 1000);
  }
};
```

✅ **Expected Output:** The `person` object. 🎉

---

### ⚡ The Modern Solution: Arrow Functions

With **arrow functions**, we no longer need to store `this` in a variable because **arrow functions inherit `this` from their surrounding context**.

```javascript
const person = {
  talk() {
    setTimeout(() => {
      console.log(this);
    }, 1000);
  }
};
```

✅ **Expected Output:** The `person` object. 🎉

---

### 🎯 Key Takeaways

- **Arrow functions do not rebind `this`**; they inherit it from their enclosing scope.
- If you use a regular function inside `setTimeout`, `this` will refer to `window` (or `undefined` in strict mode).
- Arrow functions eliminate the need for workarounds like `const self = this`.

💡 **Best Practice:** When dealing with `this` in callbacks, prefer using **arrow functions** to avoid unexpected behavior.


---
# JavaScript_map_Method_with_Arrow_Functions

## 🎯 Introduction
The **`map()`** method in JavaScript is used to create a **new array** by applying a function to each element of an existing array. It is widely used for **data transformation**. 🚀

---

## 🔹 Syntax of `map()`

### ✅ Traditional Function
```js
const colors = ['red', 'green', 'blue'];
const items = colors.map(function(color) {
    return '<li>' + color + '</li>';
});
console.log(items);
```

### ⚡ Arrow Function Equivalent
```js
const items = colors.map(color => '<li>' + color + '</li>');
console.log(items);
```

### 🔥 Using Template Literals
```js
const items = colors.map(color => `<li>${color}</li>`);
console.log(items);
```

---

## 🌟 Example Usage
### 🎨 Converting Colors to List Items
#### ✅ Using Traditional Function
```js
const colors = ['red', 'green', 'blue'];
const items = colors.map(function(color) {
    return '<li>' + color + '</li>';
});
console.log(items);
```

#### ⚡ Using Arrow Function
```js
const items = colors.map(color => `<li>${color}</li>`);
console.log(items);
```

---

## 🎯 Advantages of Using `map()` with Arrow Functions
✔️ **Shorter Syntax** - Less boilerplate code 📌
✔️ **More Readable** - Clear and concise 🎯
✔️ **Immutable** - Does not modify the original array 🔥
✔️ **Easier Debugging** - Works well with debugging tools 🛠️

---

## 🛑 Things to Keep in Mind
❌ **Does not modify the original array** - Always returns a new array
❌ **Callback function required** - Must be passed a function
❌ **Always returns an array of the same length**

---


# JavaScript_Object_Destructuring

## 🎯 Introduction
Object **destructuring** in JavaScript allows us to **extract values** from objects into separate variables in a clean and concise way. It reduces redundancy and improves readability. 📌

---

## 🔹 Typical Way of Accessing Object Properties
```js
const address = {
    street: "123 Main St",
    city: "Kurunagala",
    country: "Sri Lanka"
};

const street = address.street;
const city = address.city;
const country = address.country;
```

### 🛑 Issues with this Approach:
❌ **Repetitive** usage of `address.property`
❌ **Verbose** code
❌ **Hard to maintain** when adding/removing properties

---

## 🔥 Using Object Destructuring
### ✅ Destructuring Assignment
```js
const { street, city, country } = address; 
console.log(street);  // Output: 123 Main St
console.log(country); // Output: Sri Lanka
```
✔️ **Less repetitive**
✔️ **Cleaner syntax**
✔️ **Improves readability**

---

## 🎯 Extracting a Single Property
You can also extract **only one property**:
```js
const { city } = address; 
console.log(city);  // Output: Kurunagala
```

---

## 🎭 Renaming Variables with Aliases
You can rename variables while destructuring:
```js
const { street: st, country: cn } = address;
console.log(st); // Output: 123 Main St
console.log(cn); // Output: Sri Lanka
```
✔️ **Avoids naming conflicts**
✔️ **Improves clarity in larger projects**

---

## 🎉 Conclusion
Object **destructuring** is a powerful JavaScript feature that enhances **code readability, efficiency, and maintainability**. It reduces redundancy and makes it easier to work with objects. 🚀

---







