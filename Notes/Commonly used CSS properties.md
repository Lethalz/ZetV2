2207301644
	Status: #idea 
		Tags: [[Webdev]] [[CSS]]
		

# Commonly used CSS properties

### color and background-color 

```css

p {
  /* hex example: */
  color: #1100ff;
  /* rgb example: */
  background-color: rgb(100, 0, 127);
  /* hsl example: */
  color: hsl(15, 82%, 56%);
}
```
---
### Typography Basics and `text-align`

`font-family` can be a single value or a comma-separated list of values.

Have a fallback incase the browser does not support the first font that you've chosen.
e.g  `font-family: "Times New Roman", sans-serif;`

`font-size` selects the size of the font. the value of this property should not contain any whitespace.

`font-weight` affects the boldness of text
e.g. `font-weight: bold`  or a number between 1 and 1000, e.g. `font-weight: 700`.

`text-align` will align text horizontally within an element
 `text-align: center` left , right etc..

By default  an images height and width will be the same as the actual image file. To adjust the size without losing proportions use "auto" for the height property and adjust the `width` value

```css
img {
  height: auto;
  width: 500px;
}
```
 


---
# Reference
[Css Foundations](https://www.theodinproject.com/lessons/foundations-css-foundations)
[[Anatomy of CSS syntax]]
