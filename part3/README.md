# Three Pillars of Writing Good HTML and CSS

1. Responsive Design
2. Writing Maintainable and Scalable Code
3. Web Performance

### Responsive Design

Build one website that works beautifully across all screen sizes and devices.

Topics include:

* Fluid layouts
* Media queries
* Responsive images
* Correct units
* Desktop-first vs mobile-first

### Maintainable and Scalable Code

Topics include:

* Clean
* Easy to understand
* Promotes growth
* Reusable
* How to organized files
* How to name classes
* How to structure HTML

### Web Performance

Topics include:

* Less HTTP requests
* Less code
* Compress code
* Use a CSS preprocessor
* Fewer images (Biggest impact)
* Compress images

# How CSS Works Behind the Scenes: An Overview

What happens when we load up a webpage?

Load HTML ->
Parse HTML / Load CSS ->
Parse CSS ->
  -> Resolve conflicting CSS declarations (cascade)
  -> Process final CSS values

-> Document Object Model (DOM)
-> CSS Object Model (CSSOM)

This process forms the render tree.

The website is rendered with the visual formatting model. This algorithm calculates the box model, floats, and positioning.

Final website is rendered.

# How CSS Is Parsed

The Cascade and Specificity

A CSS rule consists of a selector and a declaration block.

**A Selector**

```
.my-class {
  ...
}
```

**Declaration Block**

```
{
  width: 100%;
  height: 100%;
}
```

> Cascade: The process of combining different stylesheets and resolving conflicts between different CSS rules and declarations, when more than one rule applies to a certain element.

**The Three Types of Styles**

* Author declarations are what we write.
* User declarations kick in when a user changes the font size via a browser option.
* Browser (user agent). If nothing else is specified, this is the default.

The cascade combines all of this CSS from different CSS.

The cascade uses...

* The importance (weight)
* Specificity
* Source order

...to determine which one goes first.

**Importance**

* User `!important` declaration
* Author `!important` declarations
* Author declarations
* User declarations
* Default browser declarations

**Specificity**

1. Inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-element

**Source Order**

The last declaration in the code will override all other declarations and will be applied.

**Key Takeaways*

* CSS declarations marked with `!important` have the highest priority. use only has a last resource. There are usually better ways of going about a fix.

* Inline styles will always win.

* A selector that contains 1 ID is more specific than one with 1000 classes.

* A selector that contains 1 class is more specific than one with 1000 classes.

* The universal selector `*` has no specificity value (0,0,0,0).

* Rely more on specificity than on order of selectors.

* But rely on order when using 3rd party style sheets. Always put your author stylesheet last.

* More on specificity: [https://slicejack.com/quick-guide-to-css-specificity/](https://slicejack.com/quick-guide-to-css-specificity/)

