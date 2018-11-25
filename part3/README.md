# Three Pillars of Writing Good HTML and CSS

1. Responsive Design
2. Writing Maintainable and Scalable Code
3. Web Performance

### Responsive Design

Build one website that works beautifully across all screen sizes and devices.

Topics include:

- Fluid layouts
- Media queries
- Responsive images
- Correct units
- Desktop-first vs mobile-first

### Maintainable and Scalable Code

Topics include:

- Clean
- Easy to understand
- Promotes growth
- Reusable
- How to organized files
- How to name classes
- How to structure HTML

### Web Performance

Topics include:

- Less HTTP requests
- Less code
- Compress code
- Use a CSS preprocessor
- Fewer images (Biggest impact)
- Compress images

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

- Author declarations are what we write.
- User declarations kick in when a user changes the font size via a browser option.
- Browser (user agent). If nothing else is specified, this is the default.

The cascade combines all of this CSS from different CSS.

The cascade uses...

- The importance (weight)
- Specificity
- Source order

...to determine which one goes first.

**Importance**

- User `!important` declaration
- Author `!important` declarations
- Author declarations
- User declarations
- Default browser declarations

**Specificity**

1. Inline styles
2. IDs
3. Classes, pseudo-classes, attribute
4. Elements, pseudo-element

**Source Order**

The last declaration in the code will override all other declarations and will be applied.

**Key Takeaways**

- CSS declarations marked with `!important` have the highest priority. use only has a last resource. There are usually better ways of going about a fix.

- Inline styles will always win.

- A selector that contains 1 ID is more specific than one with 1000 classes.

- A selector that contains 1 class is more specific than one with 1000 classes.

- The universal selector `*` has no specificity value (0,0,0,0).

- Rely more on specificity than on order of selectors.

- But rely on order when using 3rd party style sheets. Always put your author stylesheet last.

- More on specificity: [https://slicejack.com/quick-guide-to-css-specificity/](https://slicejack.com/quick-guide-to-css-specificity/)

# Specificity In Practice

[The Specificity Calculator](https://specificity.keegan.st/)

Essentially, count the number of elements/ids/classes/pseudo classes. The higher count determines the specificity.

Using `!important` will ignore cascade specificity.

[My Example](https://codepen.io/strflyr/pen/eQKWZO)

# How CSS is Parsed - Part 2: Value Processing

`rem` and `vh` will ultimately be rendered as `px`.

1. Declared Value (author declarations)
2. Cascaded Value (after the cascade)
3. Specified Value (defaulting, if there is no cascaded value)
4. Computed Value (converting relative values to absolute)
5. Used Value (final calculations, based on layout)
6. Actual Value (browser and device restrictions)

### How Units Are Converted From Relative To Absolute

%s with fonts are different from %s with distances.

**Fonts**

`font-size: 150%;` - a font with have a size 150% larger than its parent element

**Length**
`padding: 10%;` - an element that has 10% of the padding of the parent element

`em` - use the parent/current element as a reference

`rem` - use the root element as the reference

**Summary**

- Each property has an intial value, which is used if nothing is declared
- Browsers specify a root `font-size` for each page (usually `16px`)
- Percentages and relative values are always converted to pixels
- Percentages are measured relateive to their parent's `font-size`, if used to specify `font-size`.
- Percentages are measured relative to their parent's `width` fi they are usued to specify lengths
- `em` are measured relative to their parent `font-size`, if used to specify `font-size`.
- `em` are measured relative to the current `font-size`, if used to specify lengths.
- `rem` are always measured relative to the document's root `font-size`.
- `vh` and `vw` are simply percentage measurements of the viewport's `height` and `width`.

# How CSS Is Parsed - Part 3: Inheritance

Inheritance is a way of propogating values from the parents to the children.

Every CSS property must have a value.

```
CSS asks "Is there a cascaded value?"

  If yes, specified value = cascaded value.

  If no, "Is the property inherited?". This is specific to each prop. Some props are inherited, others are not.
    If yes, specified value = computed value of parent element
    If no, specified value = initial value (specific to each prop)
```

**Summary**

- Inheritance passes the values for some specific properties from parents to children - more maintainable code.
- Properties related to text are inherited: `font-family`, `font-size`, `color`, etc.
- `margin` and `padding` are not inherited.
- The computed value of a prop is what gets inherited, not the declared value.
- Inheritence of a prop only works if no one declares a value for that prop.
- You can use the `inherit` keyword to force inheritance on a certain prop.
- The `initial` keyword resets a prop to its initial value.

# Convertin PX to REM: An Effective Workflow

The `html` element determines the default `font-size` of the document. When no styling is applied, the default `font-size` in browsers is `16px`.

If you want to change this, simply apply a new `font-size` to the `html` element, like so...

```
html {
  font-size: 10px;
}
```

To convert `px` to `rem` use the following formula:

```
px / html `font-size`
```

If you are trying to convert a font size of `25px` to `rem` when you have a `html` `font-size` of `16px`, then the calculation would be...

```
25px / 16px
```

> !IMPORTANT - convert almost all `px` values to `rem` based on the `font-size` of the `html` element.

`rem`'s are not supported below IE9.

# How CSS Renders a Website: The Visual Formatting Model

The Visual Formatting Model - Algorithm that calculates boxes and determines the layout of these boxes, for each element in the render tree, in order to determine the final layout of the page.

- Dimensions of boxes: the box-model
- Box type: inline, block, inline-block
- Positioning Scheme: floats and positioning
- Stacking contexts
- Other elements in the render tree
-Viewport size, dimensions of images, etc.

This is how the browser figures out what to show the user.

![An image of the box model](boxmodel.png)

- Content - text, images, etc.
- Padding - transparent area around the content inside the box.
- Border - goes around the padding and the content.
- Margin - space between boxes
- Fill area - area that gets filled with the background color or background image.

total width = right border + right padding + specified width + left padding + left border

total height = top border + top padding + specified height + bottom padding + bottom border

If we set `box-sizing: border-box`, the height and width will be defined for the entire box, including the padding and border.

![An example of border-box in action](borderbox.png)

### Box Types: Inline, Block-Level, and Inline-Block

**Block-Level**

- Elements formatted visually as blocks
- 100% of parent's width
- Vertically, one after another
- Box-model applies as showed

_How to Implement_

```
display: block;
(display: flex)
(display: list-item)
(display: table)
```
**Inline**

- Content is distributed in lines
- Occupies only the space that the content needs
- No line-breaks
- No heights and widths
- Paddings and margins only horizontal (left and right)

_How to Implement_

```
display: inline;
```

**Inline-Block**

- A mix of block and inline
- Occupies only the space that the content needs
- No line-breaks
- Box-model applies as shown

_How to Implement_

```
display: inline-block;
```

### Positioning Schemes: Normal Flow, Absolute Positioning, and Floats

**Normal Flow**

- Default positioning scheme
- Not floated
- No absolutely positioned
- Elements laid out according to their source order

_How to Implement_

```
position: relative /* This is browser default */
```

**Absolute Positioning**

- Element is removed from the normal flow
- No impact on surrounding content or elements
- We use `top`, `bottom`, `left`, and `right`.

_How to Implement_

```
position: absolute;
position: fixed;
```

**Floats**

* Element is removed from the normal flow
* Text and inline elements will wrap around the floated element
* The container will not adjust its height to the element

_How to Implement_

```
float: left;
float: right;
```


### Stacking Contexts

Stacking contexts determine the order that elements are rendered on the page.

Next contexts can be created with CSS props. `z-index` is most commonly known.

# CSS Architecture, Components, and BEM (Block Element Modifier)

We want code that is:

- Clean
- Modular
- Reusable
- Ready for Growth

**Think** about the layout of your page or app before writing code.

- Use component driven design.
- Modular building blocks that make up interfaces.
- Held together by the layout of the page.
- Reusable across a project, and in between different projects.
- Independent, allowing us to use them anywhere on the page. No dependence on parents.

**Build** your layout in HTML and CSS with a consistent structure or naming classes.

- **B**lock **E**lement **M**odifier
- A Block is a stand alone component that is meaningful on its own.
- An Element is a part of blcok that has no standalone meaning of its own.


```
.block {}
.block__element {}
.block__element--modifier {}
```

![An example of BEM](bem.png)

**Architect** create a logical architecture for your CSS with files and folders.

The `7-1` pattern.

* 7 different folders for partial Sass files, and 1 main Sass file to import all other files into a compiled CSS stylesheet.

```
base/
components/
layout/
pages/
themes/
abstracts/
vendors/
```

# Implementing BEM in the Natour Project

