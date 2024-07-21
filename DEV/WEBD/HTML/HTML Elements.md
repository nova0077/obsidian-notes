## HTML Lists
- Unordered Lists (`<ul>`)
- Ordered Lists (`<ol>`)
- List items (`<li>`)

### HTML Description Lists
- `<dl>` tag defines description list
- `<dt>` tag defines term (name)
- `<dd>` tag describes each term
```html
<dl>
	<dt>Coffee</dt>
	<dd>- black hot drink </dd>
	<dt>Milk</dt>
	<dd>- white cold drink </dd>
</dl>
```
![[Pasted image 20230909120505.png]]


## The anchor element
The `<a>` tag defines a hyperlink, which is used to link from one page to another.
#### Attributes
- href => Specifies the URL of the page the link goes to
- rel => Specifies the relationship between the current document and the linked document
- target => Specifies where to open the linked document

Important Attributes with its values
- `target = _blank` opens the link in a new page.
- `<a href = "tel:+9390639860"> phone number </a>` Links a phone number
- `<a href = "mailto:someone@example.com"> Send email </a>` Links an email address
- `<a href="#section2"> Go to section 2 </a>` links to another section on the same page
- `<a href="javascript:alert('Hello World!');">Execute JavaScript</a>` Links a JavaScript code

## The image element
- used to embed an image in a web page.
- The `img` tag creates a holding space for the referenced image
- It has 2 required attributes:
	1. **src** - Specifies the path or address of the image
	2. **alt** - Specifies an alternate text for the image. It will be read by the screenreader.
```img.html
<img 
	src="img_girl.jpg" alt="Girl in a jacket" 
	width="500" height="600"
>
```
-  Use the CSS **`float`** property to let the image float to the left or to the right
```img.html
<p>
	<img 
		src="smiley.gif" alt="Smiley face" 
		style="float:right; width:42px; height:42px;"
	>  
	The image will float to the right of the text.
</p>
```

>[!note]
>A screen reader is a software program that reads the HTML code, and allows the user to "listen" to the content. Screen readers are useful for people who are visually impaired or learning disabled.


## HTML Comments
```index.html
<!-- This is a comment -->
```
