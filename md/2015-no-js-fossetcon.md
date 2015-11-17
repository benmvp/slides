# You don't need JavaScript for that!

## Ben Ilegbodu

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](http://www.benmvp.com/) | [#fossetcon](https://twitter.com/hashtag/fossetcon)

NOTES:
- How many folks here would call themselves web developers?
- How many of you use toolkits/libraries like jQuery?
- The goal of this talk is to highlight ways that you can use HTML & CSS to replace functionality we previously could only accomplish w/ JavaScript

=====

ben-ilegbodu.json

<div style="display:flex">
	<div style="flex:0 0 50%;">
		<pre><code class="lang-json">
{
  "name": "Ben Ilegbodu",
  "priorities": [
    "Jesus", "family", "work"
  ],
  "location": "SF Bay Area",
  "work": "@Eventbrite",
  "role": "Sr. UI Engineer",
  "hobbies": [
    "basketball", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="img/family-nyc.jpg" style="width:100%;height:auto" alt="Family in NYC" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](img/eventbrite-logo.png)

NOTES:
- Currently a Senior UI Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- I work on the team that’s actual rebuilding that page you used to buy your tickets into something beautiful & responsive

=====

# Agenda

1. Interactivity
1. Functionality
1. Layout
1. Animation

NOTES:
_[2 minutes]_

- Here's what we'll be talking about today in our session
- We'll look at how we can implement interactivity, functionality, layout & animation
- Without using any JavaScript! (or at least very little)
- The rationale being that if we use HTML/CSS, the browser executes the interaction which will typically be more performant

=====

# Interactivity

with CSS `:hover`

NOTES:
_[3 minutes]_

- Let's start simple looking at iteractivity with `:hover`
- This doesn't require any HTML5 or CSS3 fanciness
- Just some fun CSS pseudo-class code

/////

###### Interactivity

## Header navigation example

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

NOTES:
- Header navigation menu that enables interactivity using the `:hover` CSS pseudo selector.- On hover of a menu item:
  - the text goes from dark to light
  - the item background image goes from light to dark
  - the icon goes from a "dormant" to "active" state.
- Use an icon font from Font Awesome instead of traditional image
- Normally you would use `<img>` for images or `background-image` for image sprite

/////

###### Interactivity

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

Uses an icon font!

NOTES:
_[4 minutes]_

- Use an icon font from Font Awesome instead of traditional image
- Normally you would use `<img>` for images or `background-image` for image sprite
- Icon fonts are fonts just like Arial or Comic Sans, but instead of comprising text characters, they contain custom monochrome image glyphs.
- Icon fonts are awesome because:
  - Super lightweight compared to traditional images
  - Can easily change their size, color and any other text property.

/////

###### Interactivity

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

```html
<header class="global-header">
  <ul class="header-nav">
    <li class="header-nav-item header-nav-item--home">
      <a class="header-nav-item__link" href="#home">Home</a>
    </li>
    <li class="header-nav-item header-nav-item--search">
      <a class="header-nav-item__link" href="#search">Search</a>
    </li>
    <li class="header-nav-item header-nav-item--cart">
      <a class="header-nav-item__link" href="#cart">Cart</a>
    </li>
    <li class="header-nav-item header-nav-item--me">
      <a class="header-nav-item__link" href="#account">Me</a>
    </li>
  </ul>
</header>
```

[SMACSS](https://smacss.com/) + [BEM](https://css-tricks.com/bem-101/) CSS class naming


NOTES:
_[5 minutes]_

- Using semantic HTML5 `<header>` tag & `<ul>` + `<li>`
- Also using SMACSS + BEM CSS class naming
- Generic class for all of the items + unique class for each item

/////

###### Interactivity

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

```css
.header-nav-item {
  background: #ddd;
  float: left;
  font-size: 28px;
  list-style: none;
  width: 25%;
}
.header-nav-item__link { color: #222; }
```

```css
.header-nav-item:before {
  color: #222;
  font-family: FontAwesome;
  font-size: 25px;
}
.header-nav-item--home:before {
  content: "\f015";   /* home icon */
}
.header-nav-item--search:before {
  content: "\f002"; /* search icon */
}
```

NOTES:
_[6 minutes]_

- We set the background of each item to gray & float them to keep them on same line
- We set the link color to black
- The interesting part is the second section defining the CSS for the icons
- Use `:before` pseudo-class to add content to each item
- Set the `font-family` for all of them
- `FontAwesome` web font is defined via `@font-face`
- Set unique content for each item

/////

###### Interactivity

## Hover support

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

The JavaScript way:

```js
$('.header-nav-item').hover(
  function(e) {
    if (e.type == 'mouseover') {
      // change background to dark, text to light & image to "active"
    }
    else {
      // revert background to light, text to dark & image to "dormant"
    }
  }
);
```

NOTES:
_[7 minutes]_

- Not sure why you would use JS/jquery but if you're unaware of how to use `:hover` pseudo-class, this might be the only other way
- There's nothing functionally wrong with this approach, but you have to write code to do what the browser can do for you
- Plus there's now styling in the JS, which really should be separate
- There's a better way!

/////

###### Interactivity

## Hover support

<iframe src="no-js/interactivity.html" style="width:100%;height:60px;"></iframe>

The CSS way:

```css
.header-nav-item:hover { background: #222; }
.header-nav-item:hover .header-nav-item__link { color: #00a8f2; }
```

```css
.header-nav-item:hover:before { color: #ff8000; }
.header-nav-item--home:hover:before {
  content: "\f1ad"; /* building icon */
}
.header-nav-item--search:hover:before {
  content: "\f00e"; /* search-plus icon */
}
.header-nav-item--cart:hover:before {
  content: "\f217"; /* cart-plus icon */
}
.header-nav-item--me:hover:before {
  content: "\f234"; /* user-plus icon */
}
```

NOTES:
_[8 minutes]_

- The key is the `:hover` pseudo-class
- We set the background of the item to black on hover
- When we hover over the item we set the color of the link to black
- We change the color of the icons to orange on hover
  - Notice the double pseuo-classes: `:hover` & `:before`
  - Also change the icons to + versions

/////

###### Interactivity

## `@font-face` Browser support

[![@font-face web fonts support](img/no-js/font-face-support.png)](http://caniuse.com/#feat=fontface)

IE8+, Edge, Chrome, Firefox, Opera, Safari 8+, Android 4.1+, iOS

http://caniuse.com/#feat=fontface

NOTES:
_[9 minutes]_

/////

###### Interactivity

[![HTML for Font Icon Usage by CSS Tricks](img/no-js/css-tricks-html-for-font-icon-usage.png)](https://css-tricks.com/html-for-icon-font-usage/)

https://css-tricks.com/html-for-icon-font-usage/


NOTES:

=====

# Functionality

with new HTML5 `<input>` types

NOTES:
_[10 minutes]_

/////

###### Functionality

<iframe src="no-js/functionality.html" style="width:100%;height:640px;"></iframe>

NOTES:
- We'll be working off of this beautiful form example
- Clicking labels focuses field
- Placeholder text where appropriate
- Fancy new fields like date picker, slider, color picker & auto-suggest
- Ability to style required vs. optional fields
- Ability to style valid vs invalid fields

/////

###### Functionality

<div style="display:flex;justify-content:space-between;align-items:center;">
  <div style="flex:0 0 45%;">

    <iframe src="no-js/functionality.html" style="width:100%;height:640px;"></iframe>

  </div>
  <div style="flex:0 0 52%;">

    <code>&lt;label&gt;</code> &amp; <code>for</code> attribute

    <pre><code class="lang-html">
<label for="name">Full Name\*:</label>
<input id="name" type="text" />

<label for="email">Email\*:</label>
<input id="email" type="email" />
      </code></pre>

<br />
Equivalent JavaScript
    <pre><code class="lang-js">
$('label').click(function() {
  var inputId = $(this).attr('for');

  $('#' + inputId).focus();
});
      </code></pre>

  </div>
</div>

<p class="fragment">Doesn't even require HTML5 support!</p>

NOTES:
_[11 minutes]_

- Using the `<label>` tag with the `for` attribute automatically focus field when clicked
- The equivalent JavaScript is simple enough, but unnecessary!
- This doesn't require any HTML5 support, you can use this in any browser!

/////

###### Functionality

HTML5 `placeholder` attribute

<input type="url" class="input-example" placeholder="Enter URL" />

```html
<input type="url" placeholder="Enter URL" />
```
<!-- .element: class="large" -->
<br />
<br />
Equivalent JavaScript

- `onload`: `placeholder` &#8594; `value` if `value` is empty
- `onfocus`: Clear `value` if it equals `placeholder`
- `onblur`: `placeholder` &#8594; `value` if `value` is empty

NOTES:
- Trying to build a robust JS implementation is tricky
- There have been times I've used sites that have built it themselves and I'll click in and the placeholder text doesn't go away

/////

###### Functionality

`<input>` type `email`

<input class="input-example" type="email" placeholder="Enter email" required />

```html
<input type="email" placeholder="Enter email" required />
```
<!-- .element: class="large" -->
<br />
<img src="img/no-js/ios-email-keyboard.png" style="width:600px;" alt="iOS email software keyboard" /><br />
special email-focused software keyboard!

NOTES:
_[12 minutes]_

- Instead of `type="text"`, it's `type="email"`
- Provides email-focused software keyboard where applicable
- Default email validation (more on that later)

/////

###### Functionality

`<input>` type `url`

<input class="input-example" type="url" placeholder="Enter URL" />

```html
<input type="url" placeholder="Enter url" />
```
<!-- .element: class="large" -->
<br />
<img src="img/no-js/ios-url-keyboard.png" style="width:600px;" alt="iOS url software keyboard" /><br />
special URL-focused software keyboard!

NOTES:
_[13 minutes]_

- Instead of `type="text"`, it's `type="url"`
- Provides url-focused software keyboard where applicable
- Default url validation (more on that later)

/////

###### Functionality

`<input>` type `number`

<input class="input-example" type="number" min="10" max="48" step="2" />

```html
<input type="number" step="2" min="10" max="48" />
```
<!-- .element: class="large" -->
<br />
<img src="img/no-js/ios-number-keyboard.png" style="width:600px;" alt="iOS number software keyboard" /><br />
special number-focused software keyboard!

NOTES:
_[14 minutes]_

- Instead of `type="text"`, it's `type="number"`
- Provides number-focused software keyboard where applicable
- `min` & `max` dictate bounds
- `step` dictates up/down arrows as well as validation (no decimals)
- Can't type in non numbers
- Default number validation (more on that later)

/////

###### Functionality

`<input>` type `tel`

<input class="input-example" type="tel" placeholder="###-###-####" />

```html
<input type="tel" placeholder="###-###-####" />
```
<!-- .element: class="large" -->
<br />
<img src="img/no-js/ios-telephone-keyboard.png" style="width:600px;" alt="iOS telephone software keyboard" /><br />
special telephone-focused software keyboard!

NOTES:
_[15 minutes]_

- Instead of `type="text"`, it's `type="telephone"`
- Provides telephone-focused software keyboard where applicable
- No validation or character prevention

/////

###### Functionality

`<input>` type `range`
<br />
<br />
<input type="range" placeholder="0 - 10" min="0" max="10" step="1" style="width:650px" />
<br />
<br />
```html
<input type="range" placeholder="0 - 10" min="0" max="10" step="1" />
```
<!-- .element: class="large" -->
<br />
native slider UI!

NOTES:
- Instead of `type="text"`, it's `type="range"`
- Provides native slider UI where applicable

/////

###### Functionality

`<input>` type `date`

<input class="input-example" type="date" placeholder="MM/DD/YYYY" pattern="^\d{2}/\d{2}/\d{4}$" />

```html
<input type="date" placeholder="MM/DD/YYYY" pattern="^\d{2}/\d{2}/\d{4}$" />
```
<!-- .element: class="large" -->
<br />
<img src="img/no-js/ios-date-keyboard.png" style="width:600px;" alt="iOS date software keyboard" /><br />
native date picker UI!

NOTES:
_[16 minutes]_

- Instead of `type="text"`, it's `type="date"`
- Provides native date picker UI where applicable
- Use `pattern` & `placeholder` as fallback since not all browsers support

/////

###### Functionality

`<input>` type `color`

<input type="color" class="input-example" placeholder="#XXXXXX" value="#00008b" style="width:250px;height:100px" pattern="#[0-9a-fA-F]{6}" />

```html
<input type="color" placeholder="#XXXXXX" value="#00008b" pattern="#[0-9a-fA-F]{6}" />
```
<!-- .element: class="large" -->
<br />
native color picker UI!

NOTES:
_[17 minutes]_

- Instead of `type="text"`, it's `type="color"`
- Provides native color picker UI where applicable
- Use `pattern` w/ `placeholder` as a fallback since not all browsers support

/////

###### Functionality

`<input>` & `<datalist>`

<input type="text" class="input-example" list="suggested-names" />
<datalist id="suggested-names">
  <option>Simone</option>
  <option>Suzie</option>
  <option>Susane</option>
  <option>Scott</option>
  <option>Simon<option>
  <option>Sully</option>
  <option>Stephanie</option>
  <option>Shelly</option>
</datalist>

```html
<input type="number" list="suggested-names" />
<datalist id="suggested-names">
  <option>Simone</option>
  <option>Suzie</option>
  <option>Susane</option>
  <option>Scott</option>
  <option>Simon<option>
  <option>Sully</option>
  <option>Stephanie</option>
  <option>Shelly</option>
</datalist>
```
<br />
native auto-suggest UI!

NOTES:
_[18 minutes]_

- Create a `<datalist>` with 0 or more `<option>`s and `id` attribute
- Reference in `<input>` with `list` attribute
- Drop down for all suggestions
- Start typing for matches

/////

###### Functionality

### Validation

<div style="display:flex;justify-content:space-between;">
  <div style="flex:0 0 48%;">

<h4>HTML attributes</h4>

<ul>
  <li><code>type</code></li>
  <li><code>required</code></li>
  <li><code>minlength</code></li>
  <li><code>min</code></li>
  <li><code>max</code></li>
  <li><code>step</code></li>
  <li><code>pattern</code> (regex)</li>
</ul>  

  </div>
  <div style="flex:0 0 48%;">

<h4>CSS psuedo selectors</h4>

<ul>
  <li><code>:required</code></li>
  <li><code>:optional</code></li>
  <li><code>:valid</code></li>
  <li><code>:invalid</code></li>
  <li><code>:in-range</code></li>
  <li><code>:out-of-range</code></li>
</ul>

  </div>
</div>

NOTES:
_[19 minutes]_

/////

###### Functionality


<div style="display:flex;justify-content:space-between;align-items:center;">
  <div style="flex:0 0 48%;">
    <iframe src="no-js/functionality.html" style="width:100%;height:640px;"></iframe>
  </div>
  <div class="fragment" style="flex:0 0 48%;">
    <h4>JavaScript</h4>
    <pre><code>$('.form').submit(function(e) {
  $(this).addClass('form-submitted');
  if (!this.checkValidity()) {
    e.preventDefault();
  }
});</code></pre>

    <h4>CSS</h4>
    <pre><code>.form-submitted input:valid {
  background: #ccff90;
}
.form-submitted input:invalid {
  background: #ff8a80;
}</code></pre>
  </div>
</div>

NOTES:
_[20 minutes]_

- Put everything together and we get our original form
- Confession: I'm using a little bit of JS
  - `:valid` and `:invalid` selectors apply even before first form submit
  - Using JS to add a class to the form after first submit so form doesn't load w/ errors
  - Essentially applying CSS state via JavaScript
  - Going to cover this concept in detail in our next section

/////

###### Functionality


<div style="display:flex;justify-content:space-between;align-items:center;">
  <div style="flex:0 0 48%;">
    <iframe src="no-js/functionality.html" style="width:100%;height:640px;"></iframe>
  </div>
  <div style="flex:0 0 48%;">
    <h4>Pros</h4>

    <ul>
      <li>Native UI elements</li>
      <li>Type-focused software keyboards</li>
      <li>Form element validation for _free_</li>
    </ul>

    <br /><br />
    <h4>Cons</h4>

    <ul>
      <li>Minimal style control of UI elements</li>
      <li>Not supported in old browsers</li>
      <li>Cross-element validation</li>
    </ul>
  </div>
</div>

NOTES:
_[21 minutes]_

/////

###### Functionality

[![Wufoo - The Current State of HTML5 Forms](img/no-js/wufoo-html5-forms.png)](http://www.wufoo.com/html5/)

http://www.wufoo.com/html5/

NOTES:
- Wufoo has a extremely detailed posts about all of the HTML5 input types and attributes
  - Browser support too

=====

# Layout

with CSS3 `display:flex`

NOTES:
_[22 minutes]_

/////

###### Layout

## Linear layout

<div class="collection-example" style="justify-content:space-between;align-items:flex-end;margin-bottom:80px">
	<div class="item-example item-example-1" style="order:3">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2" style="order:1">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3" style="order:4;align-self:stretch">333333333333333333</div>
	<div class="item-example item-example-4" style="order:2">4444444444444<br>4444444444444</div>
</div>

```html
<div class="collection">
	<div class="item item-1">11111111111<br>11111111111<br>11111111111</div>
	<div class="item item-2">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item item-3">333333333333333333</div>
	<div class="item item-4">4444444444444<br>4444444444444</div>
</div>
```

`display:flex` to the rescue!

<!-- .element class="fragment" -->

NOTES:
- In this section we want to build the following horizontal layout given this HTML markup
  - Items are evenly spaced
  - Bottom-aligned, except for last which is top-aligned
  - Reordered
- HTML was originally designed for displaying text-based documents like papers or articles
- Wasn't made for advanced layout
- We've had CSS positioning, but that assumes that you have fixed dimensions or locations
- Prior to CSS3 all we've had to use is `display:float` or `display:inline-block`
- So we'd have to result to some amount of JavaScript to get this sort of layout
- Now we have `display:flex`

/////

> The main idea behind the **flex layout** is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space, or shrinks them to prevent overflow.

~Chris Coyer ([Css-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/))

/////

###### Layout

### `display` (container)

<div class="collection-example" style="margin-bottom:80px">
	<div class="item-example item-example-1">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3">333333333333333333</div>
	<div class="item-example item-example-4">4444444444444<br>4444444444444</div>
</div>

```css
.collection {
	display: flex;
}
```
<!-- .element class="larger" -->

<a href="javascript:$('section.stack.present section.present .collection-example').css('display', 'block')">
	<code>block</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('display', 'flex')">
	<code>flex</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('display', 'inline-flex')">
	<code>inline-flex</code></a>

NOTES:
_[24 minutes]_

- It all starts with `display:flex` (or `display:inline-flex`) on the container
- It enables a flex context for all its direct children.

/////

###### Layout

### `justify-content` (container)

<div class="collection-example" style="margin-bottom:80px;justify-content:space-between">
	<div class="item-example item-example-1">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3">333333333333333333</div>
	<div class="item-example item-example-4">4444444444444<br>4444444444444</div>
</div>

```css
.collection {
	justify-content: space-between;
}
```
<!-- .element class="larger" -->

<a href="javascript:$('section.stack.present section.present .collection-example').css('justify-content', 'center')">
	<code>center</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('justify-content', 'flex-end')">
	<code>flex-end</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('justify-content', 'flex-start')">
	<code>flex-start</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('justify-content', 'space-around')">
	<code>space-around</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('justify-content', 'space-between')">
	<code>space-between</code></a>

NOTES:
_[25 minutes]_

- We can then set `justify-content: space-between` to evenly space
- `justify-content` helps distribute extra free space left over when either all the flex items on a line are inflexible, or are flexible but have reached their maximum size.
- Options:
  - `center`: items are centered along the line
  - `flex-end`: items are packed toward to end line
  - `flex-start`: (default) items are packed toward the start line
  - `space-around`: items are evenly distributed in the line with equal space around them.
  - `space-between`: items are evenly distributed in the line; first item is on the start line, last item on the end line

/////

###### Layout

### `align-items` (container)

<div class="collection-example" style="margin-bottom:80px;justify-content:space-between;align-items:flex-end">
	<div class="item-example item-example-1">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3">333333333333333333</div>
	<div class="item-example item-example-4">4444444444444<br>4444444444444</div>
</div>

```css
.collection {
	align-items: flex-end;
}
```
<!-- .element class="larger" -->

<a href="javascript:$('section.stack.present section.present .collection-example').css('align-items', 'baseline')">
	<code>baseline</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('align-items', 'center')">
	<code>center</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('align-items', 'flex-end')">
	<code>flex-end</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('align-items', 'flex-start')">
	<code>flex-start</code></a> |
<a href="javascript:$('section.stack.present section.present .collection-example').css('align-items', 'stretch')">
	<code>stretch</code></a>

NOTES:
_[26 minutes]_

- We can then set `align-items: flex-end` to align at the bottom
- `align-items` defines the default behavior for how flex items are laid out along the cross axis on the current line. Think of it as the `justify-content` version for the cross-axis (perpendicular to the main-axis).
- Options:
  - `baseline`: items are aligned such as their baselines align
  - `center`: items are centered in the cross-axis
  - `flex-end`: cross-end margin edge of the items is placed on the cross-end line
  - `flex-start`: cross-start margin edge of the items is placed on the cross-start line
  - `stretch`: (default) stretch to fill the container (still respect min-width/max-width)

/////

###### Layout

### `align-self` (items)

<div class="collection-example" style="margin-bottom:80px;justify-content:space-between;align-items:flex-end">
	<div class="item-example item-example-1">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3" style="align-self:stretch">333333333333333333</div>
	<div class="item-example item-example-4">4444444444444<br>4444444444444</div>
</div>

```css
.item-3 {
	align-self: stretch;
}
```
<!-- .element class="larger" -->

<a href="javascript:$('section.stack.present section.present .item-example-3).css('align-self', 'baseline')">
	<code>baseline</code></a> |
<a href="javascript:$('section.stack.present section.present .item-example-3').css('align-self', 'center')">
	<code>center</code></a> |
<a href="javascript:$('section.stack.present section.present .item-example-3').css('align-self', 'flex-end')">
	<code>flex-end</code></a> |
<a href="javascript:$('section.stack.present section.present .item-example-3').css('align-self', 'flex-start')">
	<code>flex-start</code></a> |
<a href="javascript:$('section.stack.present section.present .item-example-3').css('align-self', 'stretch')">
	<code>stretch</code></a>

NOTES:
_[27 minutes]_

- We can then set `align-self: stretch` to align the individual item at the top
- `align-self` allows the default alignment (or the one specified by `align-items`) to be overridden for individual flex items.
- Options:
  - `baseline`: item is aligned such as their baselines align
  - `center`: item is centered in the cross-axis
  - `flex-end`: cross-end margin edge of the item is placed on the cross-end line
  - `flex-start`: cross-start margin edge of the item is placed on the cross-start line
  - `stretch`: (default) stretch to fill the container (still respect min-width/max-width)

/////

###### Layout

### `order` (items)

<div class="collection-example" style="margin-bottom:80px;justify-content:space-between;align-items:flex-end">
	<div class="item-example item-example-1" style="order:3">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2" style="order:1">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3" style="order:4;align-self:stretch">333333333333333333</div>
	<div class="item-example item-example-4" style="order:2">4444444444444<br>4444444444444</div>
</div>

```css
.item-1 { order: 3; }
.item-2 { order: 1; }
.item-3 { order: 4; }
.item-4 { order: 2; }
```

NOTES:
_[28 minutes]_

- By default, flex items are laid out in the source order.
- `order` controls the order in which they appear in the flex container.
- The value can be any integer (including negative numbers)

/////

###### Layout

## Flexbox layout module

<div style="display:flex">
	<div style="flex:0 0 50%;">
		<h3>Container</h3>

		<ul>
			<li>__<code>display</code>__</li>
			<li>__<code>justify-content</code>__</li>
			<li>__<code>align-items</code>__</li>
			<li><code>flex-direction</code></li>
			<li><code>flex-wrap</code></li>
			<li><code>align-content</code></li>
		</ul>
	</div>
	<div style="flex:0 0 50%;">
		<h3>Items</h3>

		<ul>
			<li>__<code>align-self</code>__</li>
			<li>__<code>order</code>__</li>
			<li><code>flex-grow</code></li>
			<li><code>flex-shrink</code></li>
			<li><code>flex-basis</code></li>
		</ul>
	</div>
</div>

NOTES:
_[28 minutes]_

- Here's the full list of flexbox-related styles
- We covered about half of them
- They all can be useful in different cases

/////

###### Layout

## Linear layout

<div class="collection-example" style="justify-content:space-between;align-items:flex-end">
	<div class="item-example item-example-1" style="order:3">11111111111<br>11111111111<br>11111111111</div>
	<div class="item-example item-example-2" style="order:1">2222222<br>2222222<br>2222222<br>2222222</div>
	<div class="item-example item-example-3" style="order:4;align-self:stretch">333333333333333333</div>
	<div class="item-example item-example-4" style="order:2">4444444444444<br>4444444444444</div>
</div>

NOTES:

- Once again here's the result of all of our work to make a linear layout!

/////

###### Layout

## Flexbox Browser support

[![@font-face web fonts support](img/no-js/flexbox-browser-support.png)](http://caniuse.com/#feat=flexbox)

IE10+, Edge, Chrome, Firefox, Opera, Safari 8+, Android 4.1+, iOS

http://caniuse.com/#feat=flexbox

/////

###### Layout

[![CSS Tricks - A Complete Guide to Flexbox](img/no-js/css-tricks-flexbox-guide.png)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

=====

# Animation

with CSS3 `transition` & `animation`

NOTES:
_[29 minutes]_

=====

# Recap

1. Interactivity
1. Functionality
1. Layout
1. Animation

NOTES:
- Interactivity with :hover
- Functionality with HTML5 input
- Layout with CSS3 flexbox
- Animation with CSS3 transition & animation

=====

# Shoutouts

/////

![Fossetcon logo](img/fossetcon-logo-dark.jpg)

/////

![Eventbrite logo](img/eventbrite-logo.png)

## We're hiring!   <!-- .element: class="fragment" -->

/////

# YOU!

=====

# THANKS!

NOTES:
_[38 minutes]_

/////

# Questions?

## Ben Ilegbodu

[benmvp.com](http://www.benmvp.com/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github.com/benmvp](https://github.com/benmvp/)

Code examples: [benmvp.github.io/you-dont-need-js-for-that/](http://benmvp.github.io/you-dont-need-js-for-that/)
