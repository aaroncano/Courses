# jQuery
The most popular JavaScript tool.

Your browser will run any js inside a script element, including jQuery.

---
## Functions

`.addClass()` function allows you to add classes to elements.

`.removeClass()` function allows you to remove classes from elements.

`.css()` function allows you to change the css of an element.

`.prop()` function allows you to change the properties of an element.

`.html()` function allows you to change the html of an element.

`.text()` function allows you to change the text of an element. This will not render html.

`.remove()` function allows you to remove an element.

`.appendTo()` function allows you to move an element.

`.clone()` function allows you to clone an element. This will not clone event handlers.

`.parent()` function allows you to target the parent of an element.

`.children()` function allows you to target the children of an element.

`.target:nth-child(2)` function allows you to target the nth child of an element.

`.target:even` function allows you to target even elements.

`.target:odd` function allows you to target odd elements.

---

## Examples

```js
$(document).ready(function() {
  $("button").addClass("animated bounce"); //targets elements
  $(".well").addClass("animated shake"); //targets classes
  $("#target3").addClass("animated fadeOut"); //targets id

  $("button").removeClass("btn-default"); //removes class

  $("#target1").css("color", "red"); //changes css

  $("#target1").prop("disabled", true); //changes property

  $("#target4").html("<em>#target4</em>"); //changes html
  $("#target4").text("<em>#target4</em>"); //changes text

  $("#target1").remove(); //removes element

  $("#target2").appendTo("#right-well"); //moves element

  $("#target5").clone().appendTo("#left-well"); //clones element
  
  $("#target1").parent().css("background-color", "red"); //targets parent
  $("#right-well").children().css("color", "orange"); //targets children
  $(".target:nth-child(2)").addClass("animated bounce"); //targets nth child
  
  $(".target:even").addClass("animated shake"); //targets even elements
  $(".target:odd").addClass("animated shake"); //targets odd elements

  $("body").addClass("animated hinge"); //targets body

});
```