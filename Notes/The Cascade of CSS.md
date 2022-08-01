2207301741
	Status: #idea 
		Tags: [[Webdev]] [[CSS]]

# The Cascade of CSS



The cascade or the Hierarchy of CSS determines which rules actually get applied to our HTML elements. (Confliction delegations)

1.  ID selectors (most specific selector)
2.  Class selectors
3.  Type selectors

If there are conflicting delegations @ the same level say 2 class selectors then specificity comes into play :
```html
<div class="main">
  <div class="list subsection"></div>
</div>
```
```css
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```
Rule 2 would override rule 1 because of specificity.


In this example ID beats class so rule two being more specific does not matter.

```html
<!-- index.html -->

<div class="main">
  <div class="list" id="subsection"></div>
</div>
```

```css
/* rule 1 */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
```

## Rule of thumb
If its not on the same level then specificity comes into play only for conflicting delegations.



```css
/* rule 1 */
.class.second-class {
  font-size: 12px;
}

/* rule 2 */
.class .second-class {
  font-size: 24px;
}
```

Rule 2 is using  [[Descendant Combinator| Descendant Combinators]] (the empty space) but they have the same specificity

```css
/* rule 1 */
* {
  color: black;
}

/* rule 2 */
h1 {
  color: orange;
}
```
Rule 2 would have higher priority because it is using a type selector while rule 1 is using a universal selector which has no specifiity 

If there are rules targeting the same leveled element then whichever rule was the last defined takes precedent.

```css
/* styles.css */

.h1 {
  color: red;
}

.h1 {
  color: yellow;
}
```

Yellow would be applied

---
# Reference