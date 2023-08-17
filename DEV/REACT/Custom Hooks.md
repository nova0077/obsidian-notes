- A hook is a function that allows us to abstract lot of logic in react and it is reusable.
- In function we cannot access the state and life cycle of an application, but with hook we can do all that stuff.

Example of custom hook to fetch API
```jsx
// App.js
import "./App.css";
import {Cat} from "./components/Cat";
import {QueryClient, QueryClientProvider} from '@tanstack/react-query';

function App() {
	const client = new QueryClient({
		defaultOptions: {
			queries: {
				refetchOnwindowsFocus: true,
			},
		},
	});
		  
	return (
		<div className="App">
			<QueryClientProvider client={client}>
				<Cat/>
			</QueryClientProvider>
		</div>
	)
}

export default App;
```

```jsx
// Cat.js
import { useQuery } from "@tanstack/react-query";
import { useGetCat } from "../useGetCat";

export const Cat = () => {
	const {data, isCatLoading, refetchData} = useGetCat()
	
	if(isCatLoading) return <h1>Loading...</h1>;
	return (
	<div>
		<button onClick={refetchData}>refetch</button>
		<h1>{data?.fact}</h1>;
	</div>
	)
}
```

```jsx
import { useQuery } from "@tanstack/react-query";
import Axios from "axios";

export const useGetCat = () => {
	const {
		data,
		refetch,
		isLoading: isCatLoading,
		error,
	} = useQuery(["cat"], async () => {
		return Axios.get("https://catfact.ninja/fact")
			.then((res) => res.data);
	}); 
	
	const refetchData = () => {
		alert("Data Refetched");
		refetch();
	}
	
	return { data, refetchData, isCatLoading };
};
```
