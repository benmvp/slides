# Flexing your Flexbox muscles 💪🏾

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@confooca](https://twitter.com/confooca)  

<br />

December 6, 2016  

NOTES:
- My name is Ben Ilegbodu
- Excited to share about the Flexbox module introduced in CSS3
- Posted link to slides on twitter if you want to follow along

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 4px" -->

NOTES:
- But first, would like everyone to stand up!
- Let's do some wall sits
- Let's roll our shoulders
- Let's stretch our arms
- Now turn to your neighbors, introduce yourself & say hi
- You don't realize it, but I just tricked you
- Now you can't say that you didn't get anything out of my talk
- You at least got two things:
- Exercise & and met some people you didn't know
- But hopefully you'll get more out of the talk!

=====

# Building linear layouts in CSS has been hard
<!-- .element: class="statement" -->

NOTES:
- HTML was originally designed for displaying text-based documents like papers or articles
- Wasn't made for advanced layout
- We've had CSS positioning, but that assumes that you have fixed dimensions or locations

/////

# Tables

/////

# Floats

/////

# Inline-block

/////

# Solution: Flexbox Layout Module
<!-- .element: class="statement" -->

NOTES:
- Thankfully the CSS flexible box layout module, aka Flexbox, enables us to elegantly solve our layout problems

=====

ben-ilegbodu.json

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<pre class="large"><code class="lang-json">
{
  "name": "Ben Ilegbodu",
  "priorities": [
    "Jesus", "family", "work"
  ],
  "location": "Pittsburg, CA",
  "work": "@Eventbrite",
  "role": "Frontend Eng Mgr",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/family-avery-birth.jpg" style="width:100%;height:auto" alt="Ilegbodu family after baby Avery was born" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Senior UI Engineer and Frontend Platform Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- I work on the Frontend Platform team and right now we're in the midst of a transition from Backbone/Marionette to React
- Python/Django backend, but using a Node daemon to render React components server-side

=====

# Flexible Layout Module

> The main idea behind the **flex layout** is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space, or shrinks them to prevent overflow.

~Chris Coyer ([Css-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/))

NOTES:

The main idea behind flexbox is to give the container the ability to alter its items' dimensions to best fill the available space in responsive design. A flex container expands items to fill available free space, or shrinks them to prevent overflow.

=====

# Containers

=====

# Items

=====

# Flexbox layout module

<div style="display:flex;margin-top:2em">
	<div style="flex:0 0 50%;">
		<h3>Container</h3>

		<ul>
			<li><code>display</code></li>
			<li><code>justify-content</code></li>
			<li><code>align-items</code></li>
			<li><code>flex-direction</code></li>
			<li><code>flex-wrap</code></li>
			<li><code>align-content</code></li>
		</ul>
	</div>
	<div style="flex:0 0 50%;">
		<h3>Items</h3>

		<ul>
			<li><code>align-self</code></li>
			<li><code>order</code></li>
			<li><code>flex-grow</code></li>
			<li><code>flex-shrink</code></li>
			<li><code>flex-basis</code></li>
		</ul>
	</div>
</div>

=====

# Solved by Flexbox

> Flexbox just does what I want it to do...

~Ben Ilegbodu

/////

# Grid systems

https://philipwalton.github.io/solved-by-flexbox/demos/grids/

/////

# Vertical centering

https://philipwalton.github.io/solved-by-flexbox/demos/vertical-centering/

/////

# Sticky footer

https://philipwalton.github.io/solved-by-flexbox/demos/sticky-footer/

/////

# Media object

https://philipwalton.github.io/solved-by-flexbox/demos/media-object/

/////

# Input add-ons

https://philipwalton.github.io/solved-by-flexbox/demos/input-add-ons/

/////

# Holy grail layout

https://philipwalton.github.io/solved-by-flexbox/demos/holy-grail/

=====

## Browser support

[![CSS3 Flexbox browser support](../../img/no-js/css3-flexbox-browser-support.png)](http://caniuse.com/#feat=flexbox)

IE10+, Edge, Chrome, Firefox, Opera, Safari 8+, Android 4.1+, iOS

http://caniuse.com/#feat=flexbox

NOTES:
- Not supported in IE8 or IE9
- But those should be dead or dying soon

=====

# Looking ahead

/////

# Grid

/////

![Rachel Andrew](../../img/confoo2016/rachel-andrew.jpg)  <!-- .element: style="width: 300px" -->  
Rachel Andrew

<br />

[<h2>The New CSS Layout</h2>](/)

Tomorrow @ 10am in Pavilion A

/////

# Shapes

=====

[![Flexbox layout module specification](../../img/flexbox/flexbox-spec.png)](http://www.w3.org/TR/css3-flexbox/)

[Flexbox layout module specification](http://www.w3.org/TR/css3-flexbox/)

/////

[![CSS Tricks - A Complete Guide to Flexbox](../../img/flexbox/css-tricks-flexbox-guide.png)](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

[A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

/////

[![Solved by Flexbox](../../img/no-js/solved-by-flexbox.png)](http://philipwalton.github.io/solved-by-flexbox/)

[Solved by Flexbox](http://philipwalton.github.io/solved-by-flexbox/)

/////

[![Flexbox Patterns](../../img/no-js/flexbox-patterns.png)](http://www.flexboxpatterns.com/home)

[Flexbox Patterns](http://www.flexboxpatterns.com/home)

/////

[![Flexbox froggy](../../img/no-js/flexbox-froggy.png)](http://flexboxfroggy.com/)

[Flexbox froggy](http://flexboxfroggy.com/)

/////

[![Flexbox defense](../../img/no-js/flexbox-defense.png)](http://www.flexboxdefense.com/)

[Flexbox defense](http://www.flexboxdefense.com/)



=====

![Usain Bolt Thumbs Up](../../img/giphy/usain-bolt-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

/////

![ConFoo logo](../../img/confoo-logo.png)
<!-- .element: style="width: 100%;border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Vance
- Jesse
- Amanda

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

# YOU!

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct
- Any feedback would be appreciated!

=====

# THANKS!

![Jack Sparrow Thanks](../../img/giphy/thanks-jack-sparrow.gif)
<!-- .element: style="width: 75%" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)

<br />

### _Sweet ES6_, Tomorrow @ 4pm in Fontaine F

<br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- Slides are available on Twitter
- Ask questions on Twitter, via email or AMA!
