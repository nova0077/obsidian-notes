#### Prop Drilling 
1. Passing a property over multiple components, which pass this property to another component.
2. To avoid prop drilling we use **CREATE CONTEXT Hook()**.

#### State Management 
1. It is a process for managing the data that React components need in order to render themselves.
2. This data is stored in the components state object.
3. When the state objet changes, the component will re-render itself.

#### CREATE CONTEXT HOOK() [[UseContext]]
It is a way to manage states globally across multiple components.
 
```jsx
// App.js
import {useContext} from "react";
export const AppContext = createContext();

function App(){
	const [username, setUsername] = useState("praveen");
	return(
		<div className='App'>
			<AppContext.Provider value={{username}/*values that need to be passed with components*/}>
				<Router>
					<Routes>
						<Route path="/" element={<Home/>} />
						<Route path="/profile" element={<Profile/>} />
						<Route path="/contact" element={<Contact/>} />
						<Route path="*" element={<h1>Page not Found</h1>} />
					</Routes>
				</Router>
			</AppContext.Provider>
		</div>
	);
}
```

```jsx
// Home.js
import {useContext} from "react";
import {AppContext} from "../App";
export const Home = () => {
	const {username} = useContext(AppContext);
	return <h1>This is the home page and user is: {username}<h1>
};
```
