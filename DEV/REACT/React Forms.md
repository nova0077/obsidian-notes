- **React hook form** will give us all of the functionalities related to display errors, submitting the form and handling all of that.
- **Yup** is only used for validation 
- Register are used as id's for form elements
- Resolver help us integrating React Hook form and Yup

```jsx
// Form.js
import { useForm } from "react-hook-form";
import { yupResolver } from '@hookform/resolvers/yup'
import * as yup from 'yup'

export const Form = () => {

	const schema = yup.object().shape({
	fullName: yup.string().required("Your full name is required"),
	email: yup.string().email().required(),
	age: yup.number().positive().integer().min(18).required(),
	password: yup.string().min(4).max(20).required(),
	confirmPassword: yup
		.string()
		.oneOf([yup.ref("password"), null],
			"Passwords Dont Match")
		.required(),
	});
	
	const { register, handleSubmit, formState:{errors} } = useForm({
		resolver: yupResolver(schema),
	});
	
	const onSubmit = (data) => {
		console.log(data);
	}
	
	return (
		<form onSubmit={handleSubmit(onSubmit)}>
			<input 
				type="text" 
				placeholder="Full Name... " 
				{...register("fullName")} 
			/>
			<p>{errors.fullName?.message}</p>
			<input 
				type="text" 
				placeholder="Email..." 
				{...register("email")} 
			/>
			<input 
				type="number" 
				placeholder="Age..." 
				{...register("age")} 
			/>
			<input 
				type="password" 
				placeholder="Password... " 
				{...register("password")} 
			/>
			<input
				type="password"
				placeholder="Confirm Password..."
				{...register("confirmPassword")}
			/>
			<input type="submit" />
		</form>
	)
}
```