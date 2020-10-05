---
layout: post
title: On the power of HTML and CSS.
category: [originals]
tags: [technology]
---

One can use only html and css to make a grid of pictures, where, on hovering over a picture one would be presented with text in its place.
It can be achieved simply through tables and a few lines of css.

create a table of contents, where rows alternate between pictures and the text content that is to be shown.
The text can be of any length since the cell can expand to show all of the hidden text.

By, first, targeting the rows with the ::nth-child(n + 2) sudo-element, and using display: none to both hide it and ensure it doesn't take up space on the canvas.

```javascript
.th:nth-child(n + 2) {
	display: none;
	z-index: 10;		/* Any sufficiently high z-index will work here. */
}
```

Second, targeting the other rows, and applying the following CSS:

```css
.th>:nth-child(n + 1) {
	min-height: 350px; 	/* Really, this can be any value, this is the minimum height of your content, wich for me is images. */
}
```

Lastly, by using the :hover sudo-element and targeting neighboring elements with +.

```css
.th:nth-child(n + 1):hover + .th {
	display: block;
	margin-top: -350px; 	/* This is the same values as min-height! */
	background: white;	/* Some backgroud color for your content, to hide the image. */
}
```

This could be further taken to show the new content as an animation, and exercise left to the reader.