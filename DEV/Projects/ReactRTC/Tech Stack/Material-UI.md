## React and Material-UI:

1. **What is Material-UI, and why would you use it in a React project?**
    Answer: Material-UI is a popular library that *provides predesigned components and styles* for building user interfaces in React. It helps create consistent and visually appealing UIs without starting from scratch.
    
2. **How can you customize a Material-UI component's style?**
    Answer: *Material-UI components often come with props* that allow you to customize their style, such as **`style`**, **`classes`**, or **`className`**.
    
3. **Example: Using Material-UI Button Component**
```jsx
import React from 'react';
import { Button } from '@material-ui/core';

function App() {
  return (
    <div>
      <Button variant="contained" color="primary">
        Click me!
      </Button>
    </div>
  );
}

export default App;
```

4. **Example: Styling with Material-UI Theme**
```jsx
import React from 'react';
import { Button, ThemeProvider, createTheme } from '@material-ui/core';

const theme = createTheme({
  palette: {
    primary: {
      main: '#FF5722',
    },
  },
});

function App() {
  return (
    <ThemeProvider theme={theme}>
      <div>
        <Button variant="contained" color="primary">
          Styled Button
        </Button>
      </div>
    </ThemeProvider>
  );
}

export default App;
``` 
Here, we customize the button color using a Material-UI theme.