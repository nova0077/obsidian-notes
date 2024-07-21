![[Pasted image 20230926105855.png]]

- When we submit a form a HHTP request will be sent, and we control where the HTTP request goes to using **action**, and we control which type of **method** using method attribute.

## Input element
![[Pasted image 20230926110758.png]]
- In HTML5, it included many new input types, which include (color picker, range selector, time selector etc.,)
- **placeholder** attribute displays the text which shows up before we typed anything, it does not apply for all inputs (ex: color input) 

## Label element
![[Pasted image 20230926111700.png]]
Note: We can also write input inside a label tag to avoid writing id and for attributes
```html
<label>
	Enter a Number: 
	<input type="number" placeholder="enter a number">
</label>
```

## Button Elements
- If you have a button inside a form, the default behaviour is to submit the form, even though there are multiple buttons, all will lead to submit the form.
- If we do not mention the type of the button, it will be of **`type="submit"`** by default.
- To avoid this we use **`type="button"`**
- You can also use **input** to submit the form, both are same
```html
<button>Click me !</button>  
<input type="submit" value="Click me!">
```


## Name Attribute
- This attribute gives the names to input and make it unique which will be sent using HTTP.
![[Pasted image 20230926122801.png]]

Example: Search Form
```html
<h2>Hijacking Searches</h2>
<h3> Search Reddit </h3>
<form action="https://www.reddit.com/search">
	<input type="text" name="q">
	<button>Search reddit</button>
</form>

<h3>Search Youtube </h3>
<form action="https://www.youtube.com/results">
	<input type="text" name="search_results">
	<!-- without button, if you click enter, it works !! -->
</form
```

## Form Validations
- To add constraints to the user's input
```html
<form>
	<p>
		<label for="username">Username</label>
		<input type="text" id="username" name="username"
			minlength="5"
			maxlength="20"
			required
		>
	</p>
</form>
```