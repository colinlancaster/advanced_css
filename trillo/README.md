# Trillo Notes

## Flexbox

### Background

Flexbox makes it easy to align elements to one another, in different directions and in different orders.

The idea is to give the container the ability to expand and shrink elements to best use all the available space.

Flexbox replaces float layouts, which means fewer lines of code and better semantics.

Flexbox completely changes the way that we build one-dimensional layouts.

### Practical Usage

The item whose contents you want to flex should have their `display: flex` property set. This creates a flex container that behaves line an inline element.

All direct children of the flex container are called the flex items.

* X-direction is called the `main axis`.
* Y-direction is called the `cross axis`.

### Properties

![Cheatsheet](cheatsheet.png)

### Example

HTML

```html
<div class="container">
  <div class="item">1</div>
  <div class="item">2</div>
  <div class="item">3</div>
  <div class="item">4</div>
  <div class="item">5</div>
</div>
```

CSS

```css
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  background-color: #ccc;
  padding: 10px;

  /* This makes a huge difference */
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: flex-end;


/* Look at the following options for each flex property */
/*   flex-direction: row-reverse; */
/*   flex-direction: column; */
/*   flex-direction: column-reverse; */
/*   justify-content: space-between; */
/*   justify-content: space-around; */
/*   justify-content: flex-end; */
/*   justify-content: flex-start; */
/*   align-items: stretch; */
/*   align-items: baseline; */
}

.item {
  background-color: #f1425d;
  padding: 40px;
  margin: 30px;
  color: #fff;
  font-size: 40px;
}
```

The numbers used by the `order` and `flex-grow` properties only matter in relation to each other.

A simple trick to expand a flex item to occupy all available space is to set the `flex` property to `1`.

`flex-basis` is used to expand the width of an element.