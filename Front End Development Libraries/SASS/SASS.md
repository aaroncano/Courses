# SASS

## Variables
SASS uses variables. They are declared and set to store data, similar to JavaScript. Variables are declared with a dollar sign ($) and set with a colon (:).

```scss
$main-fonts: Arial, sans-serif;
$headings-color: green;
```

And to use the variables:
```scss
h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```

---
## Nesting
SASS allows nesting of CSS rules, which is a useful way of organizing a style sheet.


For a large project, the CSS file will have many lines and rules. This is where nesting can help organize your code by placing child style rules within the respective parent elements:

```scss
nav {
  background-color: red;

  ul {
    list-style: none;

    li {
      display: inline-block;
    }
  }
}
```

---
## Mixins

In SASS, a mixin is a group of CSS declarations that can be reused throughout the style sheet.

Newer CSS features take time before they are fully adopted and ready to use in all browsers. The `@mixin` directive is a convenient way to create CSS rules that are compatible with all browsers.

Consider box-shadow:
```css
div {
  -webkit-box-shadow: 0px 0px 4px #fff;
  -moz-box-shadow: 0px 0px 4px #fff;
  -ms-box-shadow: 0px 0px 4px #fff;
  box-shadow: 0px 0px 4px #fff;
}
```

It's a lot of typing to re-write this for multiple selectors. Instead, we can create a mixin:
```scss
@mixin box-shadow($x, $y, $blur, $c){ 
  -webkit-box-shadow: $x $y $blur $c;
  -moz-box-shadow: $x $y $blur $c;
  -ms-box-shadow: $x $y $blur $c;
  box-shadow: $x $y $blur $c;
}
```

The definition starts with @mixin followed by a custom name. The parameters (the $x, $y, $blur, and $c in the example above) are optional. Now any time a box-shadow rule is needed, only a single line calling the mixin replaces having to type all the vendor prefixes. A mixin is called with the @include directive:|  
```scss
div {
  @include box-shadow(0px, 0px, 4px, #fff);
}
```

## Logic in SASS

### If, else
You can use @if or @else if and @else for conditions in SASS.
```scss
@mixin border-stroke($val){
    @if $val == light {
      border: 1px solid black;
    }
    @else if $val == medium {
      border: 3px solid black;
    }
    @else if $val == heavy {
      border: 6px solid black;
    }
    @else{
      border: none;
    }
  }
```

### For loops
You can use @for to iterate through a loop.
@for is used in two ways: "start through end" or "start to end". The main difference is that the "start to end" excludes the end number as part of the count, and "start through end" includes the end number as part of the count.

```scss
@for $j from 1 through 6{
  .text-#{$j} {font-size: 15px * $j}
}
```
The `.text-#{$j}` is a string interpolation. It allows you to put a variable directly into a string.

### Each loops
You can use @each to iterate through lists.

You can use list or map data structures in SASS. Lists are a single dimensional array structure that can be a space or comma separated. Maps are similar to JS objects, with a key-value pair.

```scss
@each $color in blue, red, green {
  .#{$color}-text {color: $color;}
} //list

$colors: (color1: blue, color2: red, color3: green); //map

@each $key, $color in $colors {
  .#{$color}-text {color: $color;}
}
``` 

### While loops
The @while directive is an option with similar functionality to the JavaScript while loop. It creates CSS rules until a condition is met.
  
```scss
$x: 1;
@while $x < 13 {
  .col-#{$x} { width: 100%/12 * $x;}
  $x: $x + 1;
}
```
First, define a variable $x and set it to 1. Next, use the @while directive to create the grid system while $x is less than 13. After setting the CSS rule for width, $x is incremented by 1 to avoid an infinite loop.


## Partials
Partials in Sass are separate files that hold segments of CSS code. These are imported and used in other Sass files. This is a great way to group similar code into a module to keep it organized.

Names for partials start with the underscore (_) character, which tells Sass it is a small segment of CSS and not to convert it into a CSS file. Also, Sass files end with the .scss file extension. To bring the code in the partial into another Sass file, use the @import directive.

For example, if all your mixins are saved in a partial named "_mixins.scss", and they are needed in the "main.scss" file, this is how to use them in the main file:

```scss
@import 'mixins'
```

Note that the underscore and file extension are not needed in the import statement - Sass understands it is a partial. Once a partial is imported into a file, all variables, mixins, and other code are available to use.

## Extend
Sass has a feature called extend that makes it easy to borrow the CSS rules from one element and build upon them in another.

```scss
  .info{
    width: 200px;
    border: 1px solid black;
    margin: 0 auto;
  }

  .info-important{
    @extend .info;
    background-color: magenta;
  }
```

