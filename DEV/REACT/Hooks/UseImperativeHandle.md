- Its a way to allow a parent component to interact directly with a child component's instance, methods or properties.
- By using this ref, we will expose our child component methods to a parent component.

```jsx
// Button.js
import React, {forwardRef, useImperativeHandle, useState} from "react"

const Button = forwardRef((props, ref)=> {
	const [toggle, setToggle] = useState(false);

	useImperativeHandle(ref, ()=>({
		alterToggle(){
			setToggle(!toggle);	
		},
	}))

	return (
		<>
			<button>Button From Child </button>
			{toggle && <span>Toggle</span>}
		</>
	);
});

export default Button
```

```jsx
// App.js
import React, {useRef} from "react";
import Button from "./Button";

function ImperativeHandle(){
	const bttonRef = useRef(null);
	return (
		<div>
			<button 
				onClick={()=>{
					buttonRef.current.alterToggle();
				}}
			>
				Button From Parent
			</button>
			<Button ref={buttonRef} />					
		</div>
	)
}

export default App
```
