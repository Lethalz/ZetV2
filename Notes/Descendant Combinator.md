2207301815
	Status: #idea  
		Tags: [[Webdev]] [[CSS]] 

# Descendant Combinator

```html
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
```

```css
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
```
In the above example, the first two elements with the `contents` class (B and C) would be selected, but that last element (D) won’t be.



# Reference
[Css foundations](https://www.theodinproject.com/lessons/foundations-css-foundations#descendant-combinator-description)
[[The Cascade of CSS]]
