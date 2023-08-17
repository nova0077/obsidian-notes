- similar to [[useMemo]] hook
- It memoizes callback functions by avoiding unnecessary re-creation of callback functions on every render, especially when passing callbacks as props to child components.
- 
```jsx
import React, { useState, useCallback } from 'react';

function ParentComponent() {
    const [count, setCount] = useState(0);

    // Without useCallback: A new increment function is created on each render.
    const increment = () => {
        setCount(count + 1);
    };

    // With useCallback: The increment function is memoized to prevent unnecessary re-creation.
    const memoizedIncrement = useCallback(() => {
        setCount(count + 1);
    }, [count]);

    return (
        <div>
            <p>Count: {count}</p>
            <ChildComponent increment={memoizedIncrement} />
        </div>
    );
}

function ChildComponent({ increment }) {
    return <button onClick={increment}>Increment</button>;
}

```
Note: With useMemo we are memoizing the value returned by the function, but in the useCallback we are memoizing the entire funciton