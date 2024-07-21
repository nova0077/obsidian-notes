What Exactly is HTML5 ?
HTML5 is the latest evolution of the standard that defines HTML. It includes new elements & features for browsers to implement.

## Inline Elements Vs Block Elements
- Inline elements fit in alongside other elements
- Block level elements take up a whole "block" of space.

## Divs and Spans
- div is a generic container to hold things and group things together
- div is a block line element, it does not share its horizontal space with other elements
- Span is a inline container. It is used to group elements for styling purposes.

### Important elements
- `<hr>`=> adds a horizontal line, represents a thematic break.
- `<br>` => Line break elements, breaks the current line and keeps the rest of the content in the new line, used for poems or an address.
- `<sup>` => Super script, is used to elevate text from the base line. 
	Ex: a^2 + b^2
- `<sub>` => Sub script, is used to write text below the base line
	Ex: a/2 , C4H6
```index.html
<!-- represents 1/2 in more suitable way -->
<p>
	<sup>1</sup>
	/
	<sub>2</sub> 
</p>
```

## HTML Entities
-  _Entities_ are used to display reserved characters, that normally would be invalid.
- Start with an ampersand and end with a semicolon
- The browser interprets them and renders the correct character instead.
- every entity has its entity name and entity number.
- some important entities
	1. < => &lt;
	2. > => &gt;
	3. & => &amp;

## HTML Semantic
- Semantic elements = elements with a meaning. 
- Examples of **non-semantic** elements: `<div>` and `<span>` - Tells nothing about its content.
- Examples of **semantic** elements: `<form>`, `<table>`, and `<article>` - Clearly defines its content.
- It helps in reading and accessing the content for screen readers.
- Instead of Divs, Use more specific elements like
	- *`<section>`* => represents a standalone section. sections have a heading
	- *`<article>`* => represents a self-contained composition in a document which is independently distributable or reusable.
	- *`<nav>`* => Its purpose is to provide navigation links.
	- *`<main>`* => represents the dominant content of the `<body>` of a document
	- *`<header>`* => header element represents introductory content
	- *`<footer>`* => contains information about the author, copyright data or links related to documents.
	- *`<aside>`* => represents a portion of document whose content is indirectly related to main content. asides are frequently presented as sidebars or call-out boxes.
	- **`<time>`** => represents a specific period of time in time. it contains date time attribute
	- **`<figure>`** => represents self contained content, with optional caption (`<figcaption>`)
