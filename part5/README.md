# More Natours!

## Basic Responsive Design Principles

1. Fluid Grids and Layouts - To allow content to easily adapt to the current viewport width used to browse the website. Uses `%` rather than `px` for all layout-related lengths.

2. Flexible and Responsive Images - Images behave differently than text content, and so we need to ensure that they also adapt nicely to the current viewport.

3. Media Queries - To change styles on certain viewport widths (breakpoints), allowing us to create a different version of our website for different widths.

## Layout Types

1. Float-Based Layouts (no!)
2. Flexbox
3. CSS Grid

> In this course we will focus on Float Layouts for the Natours project. Each project will touch on the different layout types.

## Grid System

This is the very basic basics of a grid system. It is already fully responsive!

Here is the **HTML**!

```html

<section class="grid-test">
      <div class="row">
        <div class="col-1-of-2">Col 1 of 2</div>
        <div class="col-1-of-2">Col 1 of 2</div>
      </div>

      <div class="row">
        <div class="col-1-of-3">Col 1 of 3</div>
        <div class="col-1-of-3">Col 1 of 3</div>
        <div class="col-1-of-3">Col 1 of 3</div>
      </div>

      <div class="row">
        <div class="col-1-of-3">Col 1 of 3</div>
        <div class="col-2-of-3">Col 2 of 3</div>
      </div>

      <div class="row">
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-1-of-4">Col 1 of 4</div>
      </div>

      <div class="row">
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-2-of-4">Col 2 of 4</div>
      </div>

      <div class="row">
        <div class="col-1-of-4">Col 1 of 4</div>
        <div class="col-3-of-4">Col 3 of 4</div>
      </div>
    </section>
```

Here is the **CSS**!

```css
.row {
  max-width: $grid-width;
  background-color: #eee;
  margin: 0 auto;

  // Applies a margin-bottom to everything _but_ the last child.
  &:not(:last-child) {
    margin-bottom: $gutter-vertical;
  }

  @include clearfix;

  // Select where all attribs start with "col-".
  // Start with "col-", end with "col-", contains "col-" are all available
  [class^="col-"] {
    background-color: orangered;
    float: left;

    // No margin right on the last child
    &:not(:last-child) {
      margin-right: $gutter-horizontal;
    }
  }

  // Select a col-1-of-2 that is _always_ inside a row
  .col-1-of-2 {
    // You can do mathematical calculates where you can mix units.
    // Escape variables with the below syntax
    width: calc( (100% - #{$gutter-horizontal}) / 2 );
  }

  .col-2-of-3 {
    width: calc( 2 * ((100% - 2 * #{$gutter-horizontal}) / 3) + #{$gutter-horizontal});
  }

  .col-1-of-3 {
    width: calc( (100% - 2 * #{$gutter-horizontal}) / 3);
  }

  .col-1-of-4 {
    width: calc( (100% - 3 * #{$gutter-horizontal}) / 4);
  }

  .col-2-of-4 {
    width: calc( 2* ((100% - 3 * #{$gutter-horizontal}) / 4) + #{$gutter-horizontal});
  }

  .col-3-of-4 {
    width: calc( 3 * ((100% - 3 * #{$gutter-horizontal}) / 4) + (2 * #{$gutter-horizontal}) );
  }
}

```