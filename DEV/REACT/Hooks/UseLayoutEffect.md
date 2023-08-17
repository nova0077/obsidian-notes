- identical to useEffect, but it is called before useEffect.

```jsx
import {useLayoutEffect, useEffect, useRef} from "react";

function App(){
	const inputRef = useRef(null);

	useLayoutEffect(()=>{
		console.log(inputRef.current.value);
	},[]);

	useEffect(()=>{
		inputRef.current.value = "Hello";
	},[]);

	return (
		<div className="App">
			<input ref={inputRef} value="PEDRO" style={{width:400, height:100}} />
		</div>
	)
}

export default App;
```

- In the above code, we always get "PEDRO" in the console despite we are changing its value using Effect.