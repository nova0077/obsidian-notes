- It provides a way to access the context of a parent component without the need for prop drilling.
- You can access the context value directly within your functional component.

### without useContext
```jsx
// App.js
import React, {useState} from "react";
import Login from "./Login"
import User from "./User"

function App(){
	const [username, setUsername] = useState("");
	return(
		<div>
			<Login setUsername={setUsername}/>
			<User username={username}/>
		</div>
	)
}

export default App;
```

```jsx
// Login.js
import React from "react";

fucntion Login({setUsername}){
	return(
		<div>
			<input
				onChange={(event)=>{
					setUsername(event.target.value);
				}}
			/>
		</div>
	)
}

export default Login;
```

```jsx
// User.js
import React from "react";

function User({username}){
	return(
		<div>
			<h1>User: {username} </h1>
		</div>
	);
};

export default User;
```
In this above code, we have 3 components, the data is being shared among the child components (user & Login) and their functionalities are being implemented in their child component.

The above code can be modified like this

### with useContext
```jsx
import React, {useState, createContext} from "react";
import Login from "./Login"
import User from "./User"

export const AppContext = createContext(null);
function App(){
	const [username, setUsername] = useState("");
	return(
		<AppContext.Provider value = {{username, setUsername}}>
			<Login/>
			<User/>
		</AppContext.Provider>
	)
}

export default App;
```

```jsx
import React, {useContext} from "react";
import {AppContext} from "./App"

fucntion Login(){
	const {setUsername} = useContext(AppContext);
	return(
		<div>
			<input
				onChange={(event)=>{
					setUsername(event.target.value);
				}}
			/>
		</div>
	)
}

export default Login;
```

```jsx
// User.js
import React, {useContext} from "react";

function User(){
	const {username} = useContext(AppContext);
	return(
		<div>
			<h1>User: {username} </h1>
		</div>
	);
};

export default User;
```