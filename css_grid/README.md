# CSS Grid

> I know this is supposed to be about CSS Grid but look at this Emmet command:
> .container>.item.item--$*6
> Automatically incrementing class names!

Generates the following:
```html
<div class="container">
  <div class="item item--1">1: Orange</div>
  <div class="item item--2">2: Green</div>
  <div class="item item--3">3: Violet</div>
  <div class="item item--4">4: Pink</div>
  <div class="item item--5">5: Blue</div>
  <div class="item item--6">6: Brown</div>
</div>
```

Turn an element into a grid container with `display: grid;`.

Firefox dev tools for grid are unbelievable.

in the `grid-template-rows` and `grid-template-columns` properties, you can mix units. You can use `fr` or fractional units. You can use percentages. You can use pixels. You can use the `repeat([n], [pixel count])`

```html
<div class="challenge">
  <div class="header"></div>
  <div class="small-box-1">Small box 1</div>
  <div class="small-box-2">Small box 2</div>
  <div class="small-box-3">Small box 3</div>
  <div class="main-content">Main content</div>
  <div class="sidebar">Sidebar</div>
  <div class="footer">Footer</div>
</div>
```

```css
html {
  background-color: darkgrey;
}

// METHOD 1: Line Numbers
// .challenge {
//   width: 1000px;
//   margin: 30px auto;
  
//   display: grid;
//   grid-template-rows: 100px 200px 400px 100px;
//   grid-template-columns: repeat(3, 1fr) 200px;
//   grid-gap: 30px;
  
//   & > * {
//     background-color: orangered;
//     padding: 20px;
//     color: white;
//     font-size: 30px;
//     font-family: sans-serif;
//   }
  
//   .header {
//     grid-column: 1 / -1; // Stretch entire width.
//   }
  
//   .sidebar {
//     grid-column: 4 / 5;
//     grid-row: 2 / span 2;
//   }
  
//   .main-content {
//     grid-column: 1 / span 3;
//   }
  
//   .footer {
//     grid-column: 1 / -1;
//   }
// }

// METHOD 2: GRID-LINE NAMES
// Use the names for positioning in a pro layout
.challenge {
  width: 1000px;
  margin: 30px auto;
  
  display: grid;
  grid-template-rows: [header-start] 100px [header-end box-start] 200px [box-end main-start] 400px [main-end footer-start] 100px [footer-end];
  
  grid-template-columns: repeat(3, [col-start] 1fr [col-end]) 200px [grid-end];
  grid-gap: 30px;
  
  & > * {
    background-color: orangered;
    padding: 20px;
    color: white;
    font-size: 30px;
    font-family: sans-serif;
  }
  
  .header {
    grid-column: col-start 1 / grid-end;
  }
  
  .sidebar {
    grid-column: col-end 3 / grid-end;
    grid-row: box-start / main-end;
  }
  
  .main-content {
    grid-column: col-start 1 / col-end 3;
  }
  
  .footer {
    grid-column: col-start 1 / grid-end;
  }
}
```


`minmax(200px, 1fr)` - `minmax` contains boundaries not specific sizes. Min boundry for the previous is `200px`. Max is `1fr`.