- It is a special object that allows you to access and interact with the DOM
- 
```jsx
import React, {useRef} from "react"

function App(){
	const inputRef = useRef(null);

	const onClick = ()=> {
		console.log(inputRef.current.value); 
		// no need to do event.value you can directly access it using ref
		inputRef.current.focus();
		// inputRef.current.value="";
	};
	return(
		<div>
			<h1>Pedro</h1>
			<input type="text" placeholder="Ex.." ref={inputRef} />
			<button onclick={onClick}> Change Name </button>
		</div>
	)
} 

export default App;
```
