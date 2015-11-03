# You don't need JavaScript for that!

## Ben Ilegbodu

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](http://www.benmvp.com/) | [#fossetcon](https://twitter.com/hashtag/fossetcon)

NOTES:


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

<!-- .slide: data-background="url(img/eventbrite-logo.png) no-repeat center" data-background-size="contain"-->

NOTES:
- How many of you have heard of Eventbrite?
  - I sure hope so! We're sponsoring the event
  - Any of you who registered for Nodevember used Eventbrite to buy your ticket
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
- Without using any JavaScript!

=====

# Interactivity

with CSS `:hover`

NOTES:
_[3 minutes]_

- Let's start simple looking at iteractivity with `:hover`
- This doesn't require any HTML5 or CSS3 fanciness
- Just some fun CSS pseudo-class code

/////

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
.header-nav-item--cart:before {
  content: "\f07a"; /* shopping-cart icon */
}
.header-nav-item--me:before {
  content: "\f007"; /* user icon */
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

## `@font-face` Browser support

![@font-face web fonts support](img/font-face-support.png)

IE8+, Edge, Chrome, Firefox, Opera, Safari 8+, Android 4.1+, iOS


NOTES:
_[9 minutes]_

/////

![HTML for Font Icon Usage by CSS Tricks](img/css-tricks-html-for-font-icon-usage.png)

https://css-tricks.com/html-for-icon-font-usage/


NOTES:

=====

# Functionality

with HTML5 `<input>`

NOTES:
_[10 minutes]_


=====

# Layout

with CSS3 `display:flex`

=====

# Animation

with CSS3 `transition` & `animation`

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
_[30 minutes]_

/////

# Questions?

## Ben Ilegbodu

[benmvp.com](http://www.benmvp.com/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)
[github.com/benmvp](https://github.com/benmvp/)