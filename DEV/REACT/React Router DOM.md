It is used to build Single Page Application, i.e, Applications have many pages or components but page is never REFRESHED.
instead the content is dynamically fetched based on URL.

This process is called Routing and it is done with REACT ROUTER DOM.

React Router Dom supports components based Routing.

- React Router DOM is a library that helps you manage navigation and routing in your React applications.

```jsx
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function Home() {
    return <h2>Welcome to the Home Page</h2>;
}

function About() {
    return <h2>About Us</h2>;
}

function Contact() {
    return <h2>Contact Information</h2>;
}

function App() {
    return (
        <Router>
            <div>
                <nav>
                    <Link to="/">Home</Link>
                    <Link to="/about">About</Link>
                    <Link to="/contact">Contact</Link>
                </nav>
                
                <Route path="/" exact component={Home} />
                <Route path="/about" component={About} />
                <Route path="/contact" component={Contact} />
            </div>
        </Router>
    );
}

export default App;
```


