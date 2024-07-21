- **What is CSS** ?
CSS is a language for describing how documents are presented visually, how they are arranged and styled.

![[Pasted image 20230926132928.png]]

Example
```css
img {
	width: 100px;
	height: 200px;
}

/* selecting every 2nd input and adding border red */
input[type="text"]:nth-of-type(2n){
	border: 2px solid red;
}
```

## *Including Styles*
![[Pasted image 20230926133826.png]]

index.html
```html
<head>
	<link rel="stylesheet" href="style.css">
	<style>
		h2{
			color: red;
		}
	</style>
</head>
<body>
	<h1 style="color: purple"> Hello World </h1>
</body>
```

style.css
```css
h1{
	color: purple;
}

h2{
	color: red;
}
```