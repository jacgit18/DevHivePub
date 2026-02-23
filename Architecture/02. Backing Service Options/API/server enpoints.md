---
tags: 
author:
  - gitUserNamePlaceHolder
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 2024-06-09
EditDate: 
Relates: "[[Non-API Endpoints]]"
Peer Reviewed: 0
dg-publish:
---
Non-API endpoints are typically used for serving web pages, static files, or other non-JSON data in a web application. Here are a few examples of non-API endpoints:

### Example Non-API Endpoints

#### 1. Serving Static Files

Serving static files like HTML, CSS, JavaScript, images, etc.

```javascript
app.use(express.static('public'));

// Now files in the 'public' directory can be accessed directly, e.g.,
// http://yourdomain.com/index.html
// http://yourdomain.com/style.css
// http://yourdomain.com/script.js
```

#### 2. Rendering Views with a Template Engine

Rendering dynamic HTML pages using a template engine like EJS, Pug, or Handlebars.

```javascript
app.set('view engine', 'ejs');

app.get('/', (req, res) => {
  res.render('index', { title: 'Home Page', message: 'Welcome to the Home Page!' });
});

// http://yourdomain.com/
// This would render the 'index.ejs' file located in the views directory
```

#### 3. Handling Form Submissions

Handling form submissions and redirecting or rendering a success page.

```javascript
app.post('/submit-form', (req, res) => {
  // Handle form data
  const formData = req.body;
  console.log(formData);

  // Redirect to a success page
  res.redirect('/thank-you');
});

// http://yourdomain.com/submit-form
// Form data is processed and user is redirected to /thank-you
```

#### 4. Simple Redirects

Redirecting one route to another.

```javascript
app.get('/old-route', (req, res) => {
  res.redirect('/new-route');
});

// http://yourdomain.com/old-route
// This will redirect the user to http://yourdomain.com/new-route
```

#### 5. Serving HTML Content Directly

Serving HTML content directly within the route handler.

```javascript
app.get('/about', (req, res) => {
  res.send('<h1>About Us</h1><p>This is the about page.</p>');
});

// http://yourdomain.com/about
// This serves the provided HTML content
```

### Example Usage

Here's how you might combine these examples in a small Express application:

```javascript
const express = require('express');
const app = express();
const port = 3000;

// Middleware to parse JSON and URL-encoded data
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Serving static files from the 'public' directory
app.use(express.static('public'));

// Set the view engine to EJS
app.set('view engine', 'ejs');

// Home route that renders an EJS template
app.get('/', (req, res) => {
  res.render('index', { title: 'Home Page', message: 'Welcome to the Home Page!' });
});

// About route that serves HTML content directly
app.get('/about', (req, res) => {
  res.send('<h1>About Us</h1><p>This is the about page.</p>');
});

// Route for handling form submissions
app.post('/submit-form', (req, res) => {
  const formData = req.body;
  console.log(formData);
  res.redirect('/thank-you');
});

// Thank you page route
app.get('/thank-you', (req, res) => {
  res.send('<h1>Thank You</h1><p>Your form has been submitted successfully.</p>');
});

// Redirect from old route to new route
app.get('/old-route', (req, res) => {
  res.redirect('/new-route');
});

// New route
app.get('/new-route', (req, res) => {
  res.send('<h1>New Route</h1><p>This is the new route.</p>');
});

// Start the server
app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

These examples illustrate different ways to handle non-API endpoints in an Express application, providing a mix of static file serving, dynamic content rendering, form handling, and route redirection.



Correct, the `/v1` prefix is typically used to denote versioning in APIs, and it is less common to use such a prefix for non-API endpoints. For non-API routes, you generally use more descriptive, user-friendly paths that are relevant to the content or functionality being provided. Here are some guidelines and best practices for non-API endpoint routing:

### Best Practices for Non-API Endpoint Routing

1. **Descriptive Paths**: Use descriptive and meaningful paths that indicate the content or purpose of the route.
2. **Consistency**: Maintain consistency in naming conventions and structure across your routes.
3. **Avoid Versioning**: Avoid using versioning in non-API routes. Versioning is typically used for APIs to manage different versions of the API.

### Examples of Non-API Endpoint Paths

#### Descriptive Paths
```javascript
app.get('/home', (req, res) => {
  res.render('home', { title: 'Home Page' });
});

app.get('/about', (req, res) => {
  res.render('about', { title: 'About Us' });
});

app.get('/contact', (req, res) => {
  res.render('contact', { title: 'Contact Us' });
});

app.post('/contact/submit', (req, res) => {
  // Handle contact form submission
  res.redirect('/thank-you');
});

app.get('/thank-you', (req, res) => {
  res.send('<h1>Thank You</h1><p>We have received your message.</p>');
});
```

### Full Example

Here's a complete example combining these routes in an Express application:

```javascript
const express = require('express');
const app = express();
const port = 3000;

// Middleware to parse JSON and URL-encoded data
app.use(express.json());
app.use(express.urlencoded({ extended: true }));

// Set the view engine to EJS
app.set('view engine', 'ejs');

// Home route
app.get('/home', (req, res) => {
  res.render('home', { title: 'Home Page' });
});

// About route
app.get('/about', (req, res) => {
  res.render('about', { title: 'About Us' });
});

// Contact route
app.get('/contact', (req, res) => {
  res.render('contact', { title: 'Contact Us' });
});

// Handle contact form submission
app.post('/contact/submit', (req, res) => {
  const formData = req.body;
  console.log(formData);
  res.redirect('/thank-you');
});

// Thank you page
app.get('/thank-you', (req, res) => {
  res.send('<h1>Thank You</h1><p>We have received your message.</p>');
});

// Start the server
app.listen(port, () => {
  console.log(`Server is running at http://localhost:${port}`);
});
```

### Summary
- **Avoid versioning** in non-API routes.
- **Use descriptive paths** that reflect the purpose or content of the page.
- **Ensure consistency** in the naming and structure of your routes.

By following these best practices, your non-API endpoints will be more intuitive and user-friendly.





Yes, in Node.js, you can achieve similar functionality by using global variables or by extending prototypes. However, it's generally not recommended to modify global objects directly in Node.js because it can lead to unexpected behavior and make your code less modular and maintainable.

Instead, you can use dependency injection or module-level variables to share functionality across your application. For example, you can create a module that exports an instance of Axios with predefined configurations and import it wherever needed in your application.

Here's an example of how you could achieve similar functionality in Node.js without directly modifying global properties:

```javascript
// axiosInstance.js
const axios = require('axios');

const axiosInstance = axios.create({
  // Your axios configurations here
});

module.exports = axiosInstance;
```

Then, in your main file:

```javascript
// main.js
const axiosInstance = require('./axiosInstance');
const { createApp } = require('vue');
const App = require('./App.vue');
const BaseButton = require('./shared/BaseButton.vue');
const BaseCard = require('./shared/BaseCard.vue');

const app = createApp(App);

app.config.globalProperties.$axios = axiosInstance;

app.component('base-card', BaseCard);
app.component('base-button', BaseButton);

app.mount('#app');
```

This way, you create a separate module for configuring and exporting your Axios instance, and then you import and use it in your main file. This approach keeps your code modular and makes it easier to maintain and test.