#### PropTypes
- In react to define the type of properties we have to install a package called prop-types.
- If you does not follow the data type provided in the propType, it just gives you a warning.
  Ex: name is number,
- It helps you to debug fast.

```jsx
// Person.js
import PropTypes from "prop-types";

export const Person = (props) =>{
	return (
		<div>
			<h1>Name: {props.name}</h1>
			<h1>Email: {props.email}</h1>
			<h1>Age: {props.age}</h1>
		</div>
	);
};

Person.propTypes = {
	name: PropTypes.string,
	email: PropTypes.string,
	age: PropTypes.number,
}
```

#### TypeScript
- `npx create-react-app . --template typescript` command to install typescript in our current directory.
- **enum** is used to define the set of named constants.
- function in typescript
```tsx
function App(){
	const getAge = (name: string): number => {
		return 99;
	}
}
```

```tsx
// Person.tsx
interface Props {
	name: string;
	email: string;
	age: number;
	country?: Country; // "?" is used for optional 
}

export enum Country {
	Brazil = "Brazil",
	Cannada = "Cannada",
	France = "France",
}

export const Person = (props: Props) => 
	const [name, setName] = useState<string>(""); // defining a state using typescript
	return (
		<div>
			<h1>Name: {props.name}</h1>
			<h1>Email: {props.email}</h1>
			<h1>Age: {props.age}</h1>
		</div>
	);
}
```

