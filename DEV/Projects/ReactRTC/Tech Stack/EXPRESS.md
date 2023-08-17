## Express:

1. **What is Express, and how does it simplify building server-side applications?**
    Answer: Express is a web application framework for Node.js that *simplifies the process of creating web servers* and handling HTTP requests. It provides tools to define routes, handle requests, and manage middleware.
    
2. **Explain the concept of routing in Express.**
    Answer: Routing in Express involves defining URL paths and associating them with specific functions (route handlers). When a request matches a defined route, the associated function is executed.

3. **Example: Creating an Express Server**
```jsx
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Hello, Express server!');
});

const PORT = process.env.PORT || 5005;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});

```

4. **Example: Express Routing**
```jsx
const express = require('express');
const app = express();

app.get('/', (req, res) => {
  res.send('Home page');
});

app.get('/about', (req, res) => {
  res.send('About page');
});

const PORT = process.env.PORT || 5005;
app.listen(PORT, () => {
  console.log(`Server is running on port ${PORT}`);
});
```