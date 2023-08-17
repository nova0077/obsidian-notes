#### React Strict Mode:
- It is helper component that **checks your component to see if you are using unsafe lifecycles**, deprecated life cycle methods that should not be used and it will cause alerts to the console while on strict mode.
- It works by encapsulating a portion of your full application as a component. 
- StrictMode does not render any visible elements in the DOM in development mode.
- UseEffect will be called twice in strict mode, this happens only in development mode not in production mode.
- To prevent this behaviour you can use custom hook instead of useEffect.

#### React Query:
React Query is a data-fetching and state management library for React applications that simplifies fetching, caching, synchronisation and updating data.

```jsx
// App.js
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
function App() {
	const client = new QueryClient({
		defaultOptions: {
			queries: {
				refetchOnWindowFocus: false,
			},
		},
	});
	return (
	<div className="App">
		<QueryClientProvider client={client}>
			<Router>
				<div>
					<Link to="/">HOME</Link>
					<Link to="/menu">MENU</Link>
					<Link to="/contact">CONTACT</Link>
				</div>
				<Routes>
					<Route path="/" element={<Home />} />
					<Route path="/menu" element={<Menu />} />
					<Route path="/contact" element={<Contact />} />
					<Route path="*" element={<h1>Page not found!</h1>} />
				</Routes>
			</Router>
		</QueryClientProvider>
	</div>
	)
}
```

```jsx
// Home.js
import { useQuery } from '@tanstack/react-query'
import Axios from "axios";

export const Home = () => {
	const {data, isLoading, isError, refetch} = useQuery(["cat"],() => {
		return Axios.get("https://catfact.ninja/fact")
			.then((res) => res.data);
	});
	if(isError){
		return <h1>Sorry</h1>
	}
	if(isLoading){
		return <h1>Loading...</h1>
	}
	return (
		<div>
			<h1>
				This is a HOME Page <p>{data?.fact}</p>
			</h1>
			<button onClick={refetch}>refetch</button>
		</div>
	);
}
```

#### Note:
- **useQuery is a custom hook** within React Query used to fetch and cache data in a React application.
- These hooks manage lot of things caching data after initial fetch, re-fetching data in the background.
- If we change the page our react webpage will render and updates with the new data, to stop this, we use **defaultOptions** in queryClient method.
  ```jsx
const client = new QueryClient({
		defaultOptions: {
			queries: {
				refetchOnWindowFocus: false,
			},
		},
	});
```
