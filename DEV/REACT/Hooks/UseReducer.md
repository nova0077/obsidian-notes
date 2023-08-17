- It is similar to useState hook, that provides a way to manage complex state logic in functional components.
- It is more suitable for complex state transitions that involve multiple values or logic.
- 
```jsx
import React, {useReducer} from "react"

const reducer = (state, action) => {
	switch(action.type){
		case "INCREMENT":
			return {count: state.count+1, showText:state.showText};
		case "toggleShowText":
			return {count:state.count, showText:!state.showText};
		default:
			return state;
	}
}
const App = () => {
	const [state, dispatch] = useReducer(reducer, {count: 0, showText: true});

	return (
		<div>
			<h1> {state.count} </h1>
			<button
				onClick={()=>{
					dispatch({type: "INCREMENT"});
					dispatch({type: "toggleShowText"});
				}}
			> Click Here</button>
			{showText && <p>This is a text </p>}
		</div>
	);
};

export default App
```

- Reducer => function that specifies how the should update based on different actions
- Dispatch => function used to send an action to the reducer

### Why UseReducer ? 
- The reducer function can encapsulate the logic
- For managing GLOBAL state across multiple components
- Avoids unnecessary re-renders
- Code Readability