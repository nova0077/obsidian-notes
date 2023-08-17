
1. **What is CORS, and why is it necessary?**
    Answer: CORS stands for Cross-Origin Resource Sharing. It's a *security feature that controls access to resources* on one domain from another domain. It's essential to prevent unauthorized access and maintain data security.
    
2. **How do you enable CORS in a Node.js application using Express?**
    Answer: You can enable CORS in an Express application using the *cors middleware*. By adding `app.use(cors())` to your code, you allow specified domains to access your server's resources.

3. **Setting Up CORS Middleware in Express**
```jsx
const express = require('express');
const cors = require('cors');

const app = express();

app.use(cors()); // Enable CORS for all routes

// Your routes and server setup
```

4. **Example: Specifying Allowed Origins with CORS Middleware**
```jsx
const express = require('express');
const cors = require('cors');

const app = express();

const allowedOrigins = ['http://localhost:3000', 'https://example.com'];
app.use(cors({ origin: allowedOrigins }));

// Your routes and server setup
```

