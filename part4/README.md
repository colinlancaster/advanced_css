# Intro to Sass and NPM

## Variables

Sass is a preprocessor, an extension of CSS that adds power and elegance to the basic language.

Critical Sass features:

- Variables for reusable values like colors, font-sizes, spacing, etc.
- Nesting to nest selectors inside of one another, allowing us to write less code.
- Operators for mathematical operations right inside of CSS
- Partials and imports to write CSS in different files and to import them into a single file
- Mix-ins to write reusable pieces of CSS code
- Functions are similar to mix-ins, with the difference that they produce a value that can be used
- Extends are used to make different selectors inherit declarations that are common to all of them
- Control directives are for writing complex code using conditionals and loops (we are not covering these in the course)

## First Steps with Sass: Variables and Nesting

CSS declarations can be nested as follows:

```css
li {
  some-prop: some-value;

  &:first-child {
    some-prop: some-value;
  }
}
```

Don't go any deeper than three levels.

To pick a darker color without going through the trouble of getting the HEX code, use the `darken()` function in SCSS.

```css
background-color: darken($color-variable-name, 15%);

// or

background-color: lighten($color-variable-name, 15%);
```

## Mix-ins, Extends, and Functions with Sass

Chunks of code that are reusable are called mix-ins.

**LOOK!** - You can give mix-ins params/overloads

```css
@mixin style-link-text($color) {
  text-decoration: none;
  text-transform: uppercase;
  color: $color;
}
```

Functions are declared in the following way:

```scss
@function divide($a, $b) {
  @return $a / $b;
}
```

Declare an extend in the following manner:

```scss
%btn-placeholder {
  padding: 10px;
  display: inline-block;
  text-align: center;
  border-radius: 100px;
  width: $width-btn;
  @include style-link-text($color-text-light);
}
```

Use an extend in the following manner:

```scss
@extend %btn-placeholder;
```

Using extenders means that the selectors are copied to the extender.

Using mix-ins means that the CSS is applied to each selector.

> Only ever use an extend if the rules you are extending are inherently or thematically linked.
> Mix-ins are preferred most of the time.


Install Sass via NodeJS with:

```bash
node i node-sass --save-dev
```

### Usage of Sass

In your `package.json` file make sure to add the following:

```json
"scripts": {
    "compile:sass": "node-sass sass/main.scss css/style.css"
},
```

You can now compile a Sass file by using

```bash
npm run compile:sass -w
```

Use the `-w` flag to watch for changes.

### Reloading Pages Automatically

Install `live-server` with the following command:

```bash
npm i live-server --g
```

`-g` installs the module globally

Run `live-server` with the following command:

```bash
live-server
```

A new browser will open.

There should be two terminal windows open: one watching for Sass changes to compile into CSS, the other to refresh the browser automatically.
