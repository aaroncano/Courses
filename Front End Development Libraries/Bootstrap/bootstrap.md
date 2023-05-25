# Bootstrap

Bootstrap is a responsive CSS framework. It will figure out how wide your screen is and respond by resizing your HTML elements.

---

## Adding Bootstrap to your project
Add the following code to the top of your HTML:
```html
<link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous"/>
```

## Responsive images
Add "img-responsive" as a class in your img  and the image should perfectly fit the width of your page.
```html
<img class="img-responsive" src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/running-cats.jpg">
```

## Center text
You can add several classes to the same element.
```html
<h2 class="red-text text-center">your text</h2>
```

## Buttons
Bootstrap has its own styles for button elements.
You can use the "btn" class to add them. 
You can add multiple classes to one button.
```html
<button class="btn btn-default">Submit</button>

<button class="btn btn-default btn-block">Submit</button> <!-- with btn-block it would take up 100% of the available width -->

<button class="btn btn-block btn-primary">Like</button><!-- btn-primary is for the main collor of your app. It is useful for highlighting actions you want your user to take -->

<button class="btn btn-block btn-info">Info</button> <!--btn-info is used to call attention to optional actions that the user can take.-->

<button class="btn btn-block btn-danger">Delete</button> <!-- btn-danger is used to notify users that the button performs a destructive action. -->
```

---

## Bootstrap Grid
Bootstrap uses a responsive 12-column grid system, which makes it easy to put elements into rows and specify each element's relative width.
Most of Bootstrap's classes can be applied to a div element.

Bootstrap has different column width attributes that it uses depending on how wide the user's screen is. For example, phones have narrow screens, and laptops have wider screens.
 
"col-md-*". Here, md means medium, and * is a number specifying how many columns wide the element should be. In this case, the column width of an element on a medium-sized screen, such as a laptop, is being specified.

```HTML
  <div class="row">
    <div class="col-xs-4">
      <button class="btn btn-block btn-primary">Like</button>
    </div>
      <div class="col-xs-4">
        <button class="btn btn-block btn-info">Info</button>
    </div>
      <div class="col-xs-4">
        <button class="btn btn-block btn-danger">Delete</button>
    </div>
  </div>
```

---

## Create a custom heading
```html
  <div class="row">
    <div class="col-xs-8">
      <h2 class="text-primary text-center">CatPhotoApp</h2>
    </div>
    <div class="col-xs-4">
      <a href="#"><img class="img-responsive thick-green-border" src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back."></a>
    </div>
  </div>
```

## Font Awesome
Font Awesome is a convenient library of icons. There icons are treated just like fonts.

Include Font Awesome in any app:
```html
<link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.8.1/css/all.css" integrity="sha384-50oBUHEmvpQ+1lW4y57PTFmhCaXp0ML5d60M1M7uH2+nqUivzIebhndOJK28anvf" crossorigin="anonymous">
```
The i element was originally used to make other elements italic, but is now commonly used for icons. Span is also acceptable.
```html
<i class="fas fa-info-circle"></i>

<button class="btn btn-block btn-primary"><i class="fas fa-thumbs-up"></i> Like</button>
```


## Forms
All textual input, textarea, and select elements with the class .form-control have a width of 100%.
```html
<form action="https://freecatphotoapp.com/submit-cat-photo">
    <div class="row">
      <div class="col-xs-6">
        <label><input type="radio" name="indoor-outdoor"> Indoor</label>
      </div>
      <div class="col-xs-6">
        <label><input type="radio" name="indoor-outdoor"> Outdoor</label>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Loving</label>
      </div>
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Lazy</label>
      </div>
      <div class="col-xs-4">
        <label><input type="checkbox" name="personality"> Crazy</label>
      </div>
    </div>
    <div class="row">
      <div class="col-xs-7">
         <input type="text" class="form-control" placeholder="cat photo URL" required>
      </div>
      <div class="col-xs-5">
        <button type="submit" class="btn btn-primary"><i class="fa fa-paper-plane"></i> Submit</button>
      </div>
    </div>
  </form>
```

```
```
```
