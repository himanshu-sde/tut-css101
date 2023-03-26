# tut-css101
Notes on CSS by The Odin Project

CSS 101

1. Selector {Property : value} 💣️
    • <div> is a container used often to wrap content.
    • Selectors simply refer to the HTML elements to which CSS rules apply; they’re what is actually being “selected” for each rule.
    • 4 types – universal,type,class and id
    • Universal selector applies to all
    • * {
  color: purple;
}
    • A type selector (or element selector) will select all elements of the given element type, and the syntax is just the name of the element:
    • <!-- index.html -->

<div>Hello, World!</div>
<div>Hello again!</div>
<p>Hi...</p>
<div>Okay, bye.</div>
    • /* styles.css */

div {
  color: white;
}
    • ABOVE all three <div> elements would be selected, while the <p> element wouldn’t be.
    • Class selectors will select all elements with the given class, which is just an attribute you place on an HTML element.
    • <!-- index.html -->

<div class="alert-text">
  Please agree to our terms of service.
</div>
    • /* styles.css */

.alert-text {
  color: red;
}
    • Another thing you can do with the class attribute is to add multiple classes to a single element as a space-separated list, such as class="alert-text severe-alert". 
    • ID selectors are similar to class selectors. They select an element with the given ID, which is another attribute you place on an HTML element:
    • <!-- index.html -->

<div id="title">My Awesome 90's Page</div>
/* styles.css */

#title {
  background-color: red;
}
    • Classes aren’t required to be unique, so you can use the same class on as many elements as you want while Ids are unique.
    • Cant add multiple Ids but can add multiple classes.
    • Class us . While ids use #.
    • GROPING SELECTORS: LIKE OR OPERATOR
    •  if we have 2 or more selectors who share some common styles :
    • 
.read,.unread {
  color: white;
  background-color: black;
}

.read {
  /* several unique declarations */
}

.unread {
  /* several unique declarations */
}
    • Chaining SELECTORS : 
    •  we could chain both the class selectors together in our CSS like so:
.subsection.header {
  color: red;
}
    • What.subsection.headerdoes is it selects any element that has both the subsection and header classes.
    • We can also chain a class and an id:
    • 
.subsection.header { 
 color: red;
}

.subsection#preview {
  color: blue;
}
                • Descendant Combinator :  LIKE AND OPERATOR
Combinators allow us to combine multiple selectors differently than either grouping or chaining them, as they show a relationship between the selectors. There are 4 types of combinators, descendent is one of them.
So something like .ancestor .child would select an element with the class child if it has an ancestor with the class ancestor. 
Another way to think of it is child will only be selected if it is nested inside of ancestor, no matter how deep.
:
<!-- index.html -->

<div class="ancestor"> <!-- A -->
  <div class="contents"> <!-- B -->
    <div class="contents"> <!-- C -->
    </div>
  </div>
</div>

<div class="contents"></div> <!-- D -->
/* styles.css */

.ancestor .contents {
  /* some declarations */
}
IN THIS => class (B and C) would be selected, but that last element (D) won’t be.



2. Some Properties: 💣️
    • color property sets an element’s text color.
    • background-color sets the background color of an element.
    • font-family  can be a single value or a comma-separated list of values that determine what font an element uses. Each font will fall into one of two categories, either a “font family name” like "DejaVu Sans" (we use quotes due to the whitespace between words) or a “generic family name” like sans-serif (generic family names never use quotes).
    • font-size  will, as the property name suggests, set the size of the font. When giving a value to this property, the value should not contain any whitespace, e.g. font-size: 22px
    • font-weight  affects the boldness of text, assuming the font supports the specified weight. This value can be a keyword, e.g. font-weight: bold, or a number between 1 and 1000, e.g. font-weight: 700 (the equivalent of bold)
    • text-align  will align text horizontally within an element, and you can use the common keywords you may have come across in word processors as the value for this property, e.g. text-align: center
    • By default, an <img> element’s  height  and  width  values will be the same as the actual image file’s height and width. If you wanted to adjust the size of the image without causing it to lose its proportions, you would use a value of “auto” for the  height  property and adjust the  width  value:
    • EXAMPLE:
img {  
height: auto;
  width: 500px;
}


3. SOME RULES: 💣️
    • 

<div class="main">
  <div class="list subsection"></div>
</div>
/* rule 1 */
.subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
In the example above, both rules are using only class selectors, but rule 2 is more specific because it is using more class selectors, so the  color: red; declaration would take precedence.
    • 

<div class="main">
  <div class="list" id="subsection"></div>
</div>
/* rule 1 */
#subsection {
  color: blue;
}

/* rule 2 */
.main .list {
  color: red;
}
In the example above, despite rule 2 having more class selectors than ID selectors, rule 1 is more specific because ID beats class. In this case, the  color: blue; declaration would take precedence.
    • <!-- index.html -->

<div class="main">
  <div class="list">
    <div id="subsection"></div>
  </div>
</div>
/* rule 1 */
.list #subsection {
  background-color: yellow;
  color: blue;
}

/* rule 2 */
.main .list #subsection {
  color: red;
}
In this example, both rules are using ID and class selectors, so neither rule is using a more specific selector than the other. The cascade then checks the amounts of each selector type. Both rules only have one ID selector, but rule 2 has more class selectors, so rule 2 has a higher specificity!
While the  color: red  declaration would take precedence, the  background-color: yellow  declaration would still be applied since there’s no conflicting declaration for it.

=> Difference bw .cls1 (space) .cls2 and .cls1.cls2 is that former should be in parent-child relationship and later classes should be siblings



BOX MODEL:💣️


