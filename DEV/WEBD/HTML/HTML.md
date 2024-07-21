**HTML is a markup language**

# HTML Elements
- To write HTML, we pick some set of standard elements that all browsers recognise.
- Common Elements include:
	- `<p>`=> represents paragraph of text
	- `<h1` => represents header of a page
	- <img> `<img>` => embeds an image
	- `<form>` => represents a form
	- `<b>` => Bolds the content

# HTML Tags
- We create elements by writing tags
- Most (but not all) elements consist of an opening and closing tag.
- `(opening tag) <p> I am a paragraph </p> (closing tag)`

# HTML Skeleton
- We write our HTML in a standard "skeleton"
```html
<!DOCTYPE html>  
<html lang="en">  
	<head>
		<meta charset="UTF-8">  
		<title>Page Title</title>  
		<meta name="viewport" content="width=device-width,initial-scale=1">  
	</head>
	<body>  
		
	</body>  
</html>
```

1. `<!DOCTYPE html>` should be present. It informs the browser that this is an HTML document.
2. `<html lang="en"> </html>` An HTML start and end tag define the start and end of an HTML document.
>[!note]
>The HTML page is missing head tags. Head tags are not needed in HTML.
>In HTML, everything before the body tag is considered a part of the head.

3. A meta viewport tag makes the page look good on all screen sizes (Laptop, Mobile)