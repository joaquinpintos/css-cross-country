css-cross-country
=================

Code School - Learn the fundamentals &amp; foundational elements of CSS with CSS Cross-Country. Review all the web-styling necessities for front-end efficiency. 

### Level 1

#### External Stylesheets
Refactor the `<head>` tag so that all CSS is instead found on an external stylesheet;

#### ID Selector
Select the slogan only by its ID attribute, then center the text and make it italic;

#### Compound Selector
Add a declaration that selects the `<section>` via both class attributes, removing the border when both are present;

#### Style Specificity
Remove the non-external styles found on the HTML page so that !important is no longer needed to set the `<header>` background in style.css.

#### Floats
Float the `<aside>` to the right and add 10px of margin to its left and bottom sides.

#### Columns
Now let's make the `<article>` a column width the same width as the `<aside>` column and float it left.


### Level 2 - Clear Carving

#### Clearfix
Sometimes clearing is necessary. Floated items can be taller than non-floated content or even All children are floating. For all this cases we can apply 3 ways of clearing. They are:
1.Clear with a subsequent element: Requires sequence to stay intact - breaks if things move; Background / border do not extend. 

```html
    <div>
     <img src="ski.jpg" alt="Skiing!" />
     <p>To successfully ski, simply do not fall.</p>
    </div> 
    <div class="intro">
      <p>Whee!</p>
    </div>
```
```css
    img {
      float: left;
    }
    .intro {
      clear: both;
    }
```

2.Manual clearing: Requires an empty element; Might not be necessary later. 

```html
    <div>
     <img src="ski.jpg" alt="Skiing!" />
     <p>To successfully ski, simply do not fall.</p>
     <div class="clear"></div>
    </div>
```

```css
    .clear {
     clear: both;
    }
```

3.The clearfix. 

```html    
    <div class="group">
     <img src="ski.jpg" alt="Skiing!" />
     <p>To successfully ski, simply do not fall.</p>
    </div>
```
```css
    .group:before, .group:after { content: "";
      display: table; }
    .group :after {
      clear: both; }
    .group {
      zoom: 1; /* IE6&7 */ }
```

##### Challenge
Rather than using `<div class="clear"></div>` to clear floats, refactor this page to use the clearfix method via .group.

#### Nested Selectors
By default nested elements automatically inherit parent styles, but sometimes we expect a different behavior from nested elements. On those cases is very important to know the **specificity rule**(the priority of selectors). Think os specificity as four digits number, where the lowest values are in the amount of elements selectors (a, p, img, div, etc); and the highest values are in the inline selectors. ex.:

######0,0,0,1
```css
    p { color: #fff; }
```

######0,0,1,0
```css
    .intro { color: #98c7d4; }
```

######0,1,0,0
```css
    #header { color: #444245; }
```

######1,0,0,0
```html
    <h1 style="color: #000;">Mogul</h1>
```

##### Challenge
Use a nested selector to make paragraphs only within asides `italic`.

#### Inherited Styles
##### Challenge
For `anchor` tags within `aside paragraphs`, override the inherited `italics` with a `normal` font-style.

#### Specificity
##### Challenge
Refactor the CSS declarations for `.active a` and `.copyright` so that the `!important` rule can be removed.

#### Removing Id Selectors
##### Challenge
Refactor `#home` scoped anchor tags to be scoped to the `.home` class instead, so that the `.button` declaration no longer needs reference to the home class or ID.

### Level 3 - Box Bindings

#### Box Model
When adapting a layout is important to have in mind the box model. Each DOM element has a imaginary diagram with 4 areas (content area, padding area, border area and margin area). 

Total calculated box width = content width + padding width + border width;

ex.: 100px content width + 15px padding width + 10px border width = 125px box width
```css
    .downhill {
        border: 5px solid #fff;
        padding-left: 10px;
        padding-right: 5px;
        width: 100px;
    }
```
##### Challenge
The `<figure>` in our page footer should have a total box `width` of `120px`. Add an appropriate content `width` given its base `padding` and `border`.

#### Box Model Overflow
When adapting a design to its content is important to have in mind that a content could request to be overflow. The css has the `overflow` property that could be set as `visible` / `auto` / `hidden` / `scroll`. the overflow is by default applied for both axis, but is possible to restrict it to each axi using `overflow-x` or `overflow-y`.

##### Challenge
Add an appropriate content height to give the `<figure>` a height of `120px`, hide any `overflow` on the `x-axis`, and add a `scroll bar` on the `y-axis` if necessary. Hint: Use `overflow-x` and `overflow-y` to target the different axes.

#### Positioning
To setup layout positioning, the css, brings the `position` property. It could be set as one of the follow values: `static`, `relative`, `absolute` and `fixed`. Using a value other than `static` causes an object to become a **positioned** element. After became a **positioned element**, the element could use the `top`, `left`, `bottom`, and `right` properties for placement.

#### Relative Positioning
After set as relative, the renders occours in the normal flow, then shifted via positioning properties.

##### Challenge
Anchors with a `.button` class are floated to the right of our `<h3>`, but we'd like them to be centered vertically. Use `relative positioning` to move the button down `3px`.

#### Scoping Position
##### Challenge
We've attempted to position the newsletter paragraph to stick to the bottom of the footer, but it's sticking to the window instead. Add the necessary `positioning` to `<footer>` to scope it.

#### Absolute Positioning
##### Challenge
Use `absolute positioning` to place the `<figure>` in the upper right corner of the footer. Set a `z-index` on `.newsletter` to keep it above `<figure>` after it's positioned.

### Level 4 - Grooming Your Code
#### DRY
In IT world DRY is an acronym for Don't Repeat Yourself. when we're talking about css, there are some places to keep it in mind. 
1. Suppose you want to include a font property in a number of text-related elements, in a not DRY way, you could finished with something like a font-family for each element h1, p also .sale. 

```html
<body>
    <div class="container">
    <h1>Sven's Snowshoe Superstore</h1>
    <p>Our snowshoes are so stylish!</p>
    <a class="sale" href="/sale">View our sales</a>
  </div>
</body>
```
##### NOT-DRY WAY
```css
    h1 {
      font-family: Arial, sans-serif; 
    }
    p {
      font-family: Arial, sans-serif;
    }
    .sale {
      font-family: Arial, sans-serif;
    }
```
##### DRY
###### Selector combination:
```css
    h1, p, .sale {
      font-family: Arial, sans-serif; 
    }
```
###### Target parent element:
```css
    .container {
      font-family: Arial, sans-serif; 
    }
```

##### Challenge
Refactor any repeated declarations and apply them to a single parent container

#### Selector Combination
##### Challenge
Combine selectors that share the same properties into a comma-delimited list.

#### Selector Combination II
##### Challenge
Combine selectors that share the same properties into a comma-delimited list, then override the comma-delimited definition with individual definitions.

#### Shorthand
##### Challenge
Refactor the paragraph properties to use shorthand syntax.

#### Inline
##### Challenge
Use `display: inline` to make the `nav` list items display horizontal with `right` and `left` margins of `5px`. Be sure to use the shorthand syntax for `margin`.

#### Horizontal Centering
##### Challenge
Give the unordered list in `<nav>` a `width` of `250px` and `center` it `horizontally` within its parent container. Use shorthand syntax where appropriate.

### Level 5 - CSS Safety

#### Collapsing Margins
Margin properties specify the width of the margin area of a box. In a page with 3 main areas (header, article and aside), where your layout requests a margin of 20px between them, you could end up with something like:
```html
  <header>
  </header>
  <article>
  </article>
  <aside>
  </aside>
```

```css
  article {
    margin: 20px 0; 
  }
```
Now think about a layout change, we want to remove the article, leaving header and aside with a 20px margin between them... it shouldn't work now? Is it? A proper way to do that will be think about them as complementary blocks with a first margin added to the second with a total of 20px... **BUT THIS IS WRONG - in most cases*.

According to w3c spec, two adjoining margins will be collapse and the highest value of them will be the final margin between those blocks. For example, with the following style definition the margin between header and article should be 20px and between article and aside will be 30px.

```css
  header {
    margin: 20px 0; 
  }
  article {
    margin: 10px 0;
  }
  aside {
    margin: 30px 0;
  }
```
##### Challenge
Refactor the spacing between `<header>`, `<article>`, and `<aside>` so that elements will have a `20px` margin above and below, regardless of their order on the page. Account for collapsing margins and use shorthand syntax.

#### Non-Collapsing
Collapsing margins will not occur when one or more block element has:
1.Padding or border;
2.Relative or absolute positioning, float left or right;

##### Challenge
Add a `20px` bottom margin to `<header>`, `<article>`, and `<aside>` using the shorthand syntax. Remove any top margins and keep in mind that with `top` and `bottom` padding, the margins will no longer collapse.

#### Despecify
##### Challenge
Refactor these declarations so that they aren't tied only to `section articles` and can apply to `paragraphs` and `h1s` site-wide.

#### Reasonable Defaults
##### Challenge 
Oops, the `background`, `min-height`, `width`, and `padding` properties shouldn't apply to paragraphs other than `p.history`. Separately define styles that are specific to `p.history`, and leave styles that can be reused site-wide in the p declaration.

### Level 5 - Image Issues
#### Content Images
In every layout you start is important to differ between layout or content image. Each of them has best practices to be used, for content images, you should consider to use `inline` image instead of `background` some element. This will give you freedom to repeat it properly, or change origem and values properly. ex.:

##### WORST FOR CONTENT
```html
  <h4>Rental Products</h4>
  <ul>
    <li class="snowmobile"></li>
  </ul>
```
```css
  .snowmobile li {
    background: url(snowmobile.jpg); height: 300px;
    width: 400px;
  }
```

##### BEST FOR CONTENT
```html
  <h4>Rental Products</h4>
  <ul>
    <li><img src="snowmobile.jpg" alt="Snowmobile" /></li>
  </ul>
```

##### Challenge
Replace the product image incorrectly set as a background image in `<figure>` with an inline image. Use the same path and add an `alt` attribute to match the product name.

#### Background Images
For layout images, you should consider to use `background` some element instead of an `inline img`. This will give you security to manage it as needed. ex.:

##### WORST FOR LAYOUT
```html
  <h1>Feel the rhythm, feel the rhyme, get on up, it’s bobsled time!</h1>
  <img src="divider.jpg" alt="Divider" />
```

##### BEST FOR LAYOUT
```html
  <h1>Feel the rhythm, feel the rhyme, get on up, it’s bobsled time!</h1>
```
```css
  h1 {
    background: url(divider.jpg); margin-bottom: 10px; padding-bottom: 10px;
  }
```

##### Challenge
Refactor the inline image in `.more` to be a background image, placed in the `top right` of the `.more` button.

#### Image Crop
Sometimes we'll need to present imagens among our content. Probably they will be idealized by our designs as in different sizes that they were shot. On those cases the recommended is to *never* apply resizing directly to the `inline img` once it could deform the images during the resize. Check below the wright and wrong way to do.

##### WRONG WAY
```html
  <h4>Rental Products</h4> 
  <ul class="rental">
    <li><img src="snowboard.jpg" alt="Snowboard" /></li>
  </ul>
```
```css 
  .rental img {
    height: 300px;
    width: 400px; 
  }
```
##### WRIGHT WAY
```html
  <h4>Rental Products</h4> 
  <ul class="rental">
    <li class="crop">
      <img src="snowboard.jpg" alt="Snowboard" />
    </li>
  </ul>
```
```css 
  .crop {
    height: 300px;
    width: 400px; 
    overflow: hidden;
  }
```


##### Challenge
Images are currently being non-proportionally resized via CSS. Apply the `height` and `width` to their parent list items instead, and hide any `overflow`.

#### Proportional Image Crop
To proportionaly crop image, you should choose one of the containers size to be equal (`width` or `height`) and use the other as auto.

```html
  <h4>Rental Products</h4> 
  <ul class="rental">
    <li class="crop">
      <img src="snowboard.jpg" alt="Snowboard" />
    </li>
  </ul>
```
```css 
  .crop {
    height: 300px;
    width: 400px; 
    overflow: hidden;
  }
  .crop img {
    height: 300px;
    width: auto;
  }
```

##### Challenge
Now our images aren't squished, but they don't use the container effectively. Set a `height` on the images to match the container and make sure the `width` scales proportionally automatically.

#### Portrait Image Crop
##### Challenge
The new store images are portrait rather than landscape orientation. Swap the `<img>` `width` and `height` to better handle this type of proportion.

### Level 7 - Sprightly Slaloms

#### Image Replacement
Sometimes we need to replace by images some elements like logos, that normally come in replace to `a` elements. On those cases we have to proceed with some steps. 
1. Add descriptive text to image-replaced elements;
2. Add text-indent to hides the placeholder text;

```html
  <a href="#" class="logo">Sven's Snowshoe Emporium</a>
```
```css
  .logo {
    background: url(logo.png);
    display: block;
    height: 100px;
    width: 200px;
    text-ident: -9999px;
  }
```

##### Challenge
The anchor in `<h1>` is now replaced with a background image, but there's no fallback text. Add the logo's text to the HTML and remove it from view.