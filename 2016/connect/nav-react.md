# Navigating the React Ecosystem

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@connect_js](https://twitter.com/connect_js)  

<br />

October 21, 2016  

NOTES:
- My name is Ben Ilegbodu
- Posted link to slides on twitter if you want to follow along

=====

ben-ilegbodu.json

<div style="display:flex">
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

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Frontend Engineering Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences & events use it for registration
- I work on our Frontend Platform team and we're wrapping up a huge push to transition from Backbone/Marionette to React
- But I've been in the industry for a while now

=====

```html
<html>
    <head>
        <title>My Awesome site!</title>
        <link rel="styles.css" />
        <script src="script.js"></script>
    </head>
    <body>
        <!-- Lots o' markup -->
    </body>
</html>
```
<!-- .element: class="large" -->

NOTES:
- When I first started building websites they looked much like this
- Pretty much all markup with a little bit of CSS and even less JavaScript
- Scripts were vanilla JS (no `jQuery`) and were still in the `<head>`

/////

## image of "best view in IE 5"

NOTES:
- And we could get away with targeting specific versions of specific browsers

/////

## image of old Yahoo!

NOTES:
- And for the most part, company websites were built the same way
- You could actually read their source and understand
- No minification nor obfuscation
- No DevTools so it was the primary way of learning

/////

## screenshot of latest Yahoo!

NOTES:
- Company websites started getting more complex as browsers got more advanced
- We realized we could replace Flash w/ web code
- Started building SPAs w/ AJAX; whole Web 2.0 craze

/////

## image of jQuery logo

NOTES:

- At first we used used jQuery, but we quickly realized that wasn't enough for our needs
- Still had to write a lot of JS

/////

## YUI logo
## Angular logo
## Ember logo

"walled gardens" ~[Nicholas C. Zakas](https://twitter.com/slicknet)

NOTES:
- First came the full-fledged JavaScript frameworks
- Nicholas C. Zakas calls them “walled gardens”
- Back then: YUI
- Now: Angular & Ember
- But folks started feeling like this frameworks were too large & inflexible
- They were easy to get started with, but hard to configure to suite your needs

/////

## Micro Libraries

![React logo](../../img/react/react-logo.png)
<!-- .element: style="width: 45%;border: 0; background: none; margin: 0; box-shadow: none;" class="fragment" -->

NOTES:
- A huge movement towards micro libraries instead
- Instead of a full framework, have micro-libraries that are added together to create the architecture you need
- Positives: Get a lot of control, so you can pick and choose different pieces suited specifically to your needs.
- Negatives: Big upfront cost of evaluating each of the pieces. You need to know the pieces in the first place!
- React is such a micro-library.

=====

## React ecosystem

## image/diagram of ecosystem

NOTES:
- If you're new to React you might hear that on top of learning React, you need to know ES6, Redux, inline styles, server-side rendering, etc.
- It can be so overwhelming
- So I want to walk through the different "levels" in the React ecosystem so you can get an idea of how to prioritize what to learn

=====

## image/diagram of ecosystem

## React

NOTES:
- At the core of this ecosystem obviously is React

/////

<div style="display:flex;align-items:center;justify-content:space-around;">
    <img src="../../img/react/react-logo.png" style="background:none;box-shadow:none;border:none"/>
    <div>
        <h2><a href="https://facebook.github.io/react/docs/reusable-components.html#stateless-functions">Functional & Reactive</a></h2>
        <h2><a href="https://facebook.github.io/react/docs/interactivity-and-dynamic-uis.html#components-are-just-state">Uni-directional</a></h2>
        <h2><a href="https://facebook.github.io/react/docs/jsx-in-depth.html">JSX</a></h2>
        <h2><a href="https://facebook.github.io/react/docs/reconciliation.html">Virtual DOM</a></h2>
        <h2><a href="https://facebook.github.io/react/docs/top-level-api.html">Narrow API</a></h2>
    </div>
</div>

NOTES:
- Learn React and learn it _really_ well
- React is highly functional & reactive with a uni-directional data flow
- If you're used to MVC with Backbone or Ember, it'll take some time to wrap your head around the concepts
- Then of course there's JSX syntax
- Ensuring that you're fully leveraging the Virtual DOM and not directly manipulating DOM nodes takes time
- But thankfully the API is really narrow so there's not that much learn.
- More about _how_ as opposed to _what_

/////

![React tutorial in ES.next screenshot](../../img/react-esnext/react-esnext-app.png)

[React official tutorial](https://facebook.github.io/react/docs/tutorial.html) app

NOTES:
- 

=====

![Usain Bolt Thumbs Up](../../img/giphy/usain-bolt-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

/////

![Real World React logo](../../img/react-sans-node/real-world-react.jpg)
<!-- .element: style="width: 50%;border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## We're [hiring](https://www.eventbrite.com/careers/)!
<!-- .element: class="fragment" -->

NOTES:

/////

# YOU!

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct

=====

# THANKS!

![Aladdin Thanks](../../img/giphy/thanks-aladdin.gif)
<!-- .element: style="width: 60%" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

<br />

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

<br />

[#RWReact](https://twitter.com/hashtag/RWReact)  
