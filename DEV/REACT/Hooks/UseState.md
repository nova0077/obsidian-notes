- It allows functional components to manage state in a more intuitive way and enables them to respond to changes.

```jsx
import React from "react";

const App = () => {
	const [counter, setCounter] = useState(0);

	const increment = () =>{
		setCounter(counter+1);
	}
	return(
		<div>
			{counter}
			<button onClick={increment}> Increment </button>
		</div>
	)
}

export default App;
```

```jsx
import React from "react"

const App = () => {
	const [inputValue, setInputValue] = useState("");

	let onChange = (event) => {
		setInputValue(event.target.value);
	};
	
	return (
		<div>
			<input 
				placeholder="enter something..." 
				onChange={onChange}
			/>
			{inputValue}
		</div>
	)
}

export default App;
```

