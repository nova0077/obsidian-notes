- It is a function that is called whenever the page is renders.
- 
```jsx
import React, {useEffect, useState} from "react";
import axios from "axios";

function App(){
	const [data, setData] = useState("");
	const [count, setCount] = useState(0);

	useEffect(()=>{
		axios
			.get("https://jsonplaceholder.typicode.com/comments")
			.then((response) => {
				setData(response.data[0].email);
			})
	}, [count]);

	return (
		<div>
			Hello World
			<h1>{data}</h1>
			<h1>{count}</h1>
			<button onClick={()=>setCount(count+1)}> CLick </button>
		</div>
	)
}
```

- In the above code, we passed count state in the dependencies list, this means whenever our count state changes the useEffect function will be called.
