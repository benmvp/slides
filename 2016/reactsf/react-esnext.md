# React + ES.next = ♥

## Ben Ilegbodu

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ReactSF](https://twitter.com/hashtag/ReactSF)  

July 14, 2016  

NOTES:
- Posted link to slides on twitter if you want to follow along

=====

# React

/////



/////

# ECMAScript

/////



/////

## ES6/ES2015

#### Syntax

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller;margin-bottom:2em">
    <code>\_\_proto\_\_</code>  
    Arrow functions  
    Classes  
    Default parameters  
    Destructuring  
    Enhanced object literals  
    Modules  
    Rest parameters  
    Spread operator  
    Tagged templates  
    Template literals  
</div>

#### Functionality

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller">
  Array APIs  
  Block scoping  
  `for-of`  
  Generators  
  Iterators  
  Maps  
  Math APIs  
  Module loaders  
  Number APIs  
  Object APIs  
  Promises  
  Proxies  
  Reflect API  
  RegExp APIs  
  Sets  
  String APIs  
  Subclassable built-ins  
  Symbols  
  Tail calls  
  Typed arrays  
  Unicode  
  WeakMaps  
  WeakSets  
</div>

NOTES:
- Full list of features included in the ES6 specification
- That's 30+ features!

/////

## ES2016




http://www.2ality.com/2016/01/ecmascript-2016.html

/////

## ECMAScript Proposals




https://github.com/tc39/proposals

=====

## What this talk is about!



/////

## What this talk is **not** about...



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
  "role": "Sr. UI Engineer",
  "hobbies": [
    "basketball", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/family-nyc.jpg" style="width:100%;height:auto" alt="Family in NYC" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)

NOTES:
- Currently a Senior UI Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- I work on the Frontend Platform team and right now we're in the midst of a transition from Backbone/Marionette to React
- Python/Django backend, but using a Node daemon to render React components server-side

/////

<!-- .slide: data-background="url(../../img/giphy/lebron-block.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I also absolutely love basketball - both playing & watching
- But you didn't come to hear about me. At least I hope not
- You came to here about...

=====

## Agenda

0. Modules <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Classes <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Block scoping <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Destructuring <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Arrow functions <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Enhanced object literals <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Rest operator <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Spread operator <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Promises <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Default parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Array APIs <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. String APIs <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  

NOTES:

- Green for Components
- Blue for Data APIs

=====

# Components

=====

# Modules

Replace one file with many files

<br />
<br />

[2ality.com/2014/09/es6-modules-final.html](http://www.2ality.com/2014/09/es6-modules-final.html)

=====

# Classes

Replace class factories with `class` syntax

<br />
<br />

[benmvp.com/learning-es6-classes](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Now we can replace assigning to the prototype or using custom class factories with native class syntax

=====

# Block scoping

Replace `var` with `let` & `const`

<br />
<br />

[benmvp.com/learning-es6-block-level-scoping-let-const](http://www.benmvp.com/learning-es6-block-level-scoping-let-const/)

NOTES:
- In fact there are two: `let` & `const`
- Together they're called Block scoping
- With block scoping we can replace `var` with `let` & `const`

=====

# Destructuring

Replace multiple assignments with a single one

<br />
<br />

[benmvp.com/learning-es6-destructuring](http://www.benmvp.com/learning-es6-destructuring/)

NOTES:
- It's called Destructuring
- With destructuring we can reduce multiple assignments down to one
- Be advised, destructuring is probably the most "out there" syntax addition
- It's ok if you don't understand it at first

/////

<!-- .slide: data-background="url(../../img/giphy/i-hate-you-brad-pitt.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I'm afraid that after we cover destructuring, you'll feel like this...
- But stick with me...

=====

# Arrow functions

Replace anonymous functions with arrow functions

<br />
<br />

[benmvp.com/learning-es6-arrow-functions](http://www.benmvp.com/learning-es6-arrow-functions/)

NOTES:
- With arrow functions we can stop using anonymous functions

=====

# Enhanced object literals

Write less code than before

<br />
<br />

[benmvp.com/learning-es6-enhanced-object-literals](http://www.benmvp.com/learning-es6-enhanced-object-literals)

=====

# Rest operator

Replace lodash with vanilla JavaScript

<br />
<br />

[benmvp.com/learning-es6-parameter-handling](http://www.benmvp.com/learning-es6-parameter-handling/#rest-parameters/)

=====

# Data APIs

=====

# Spread operator

Replace lodash with vanilla JavaScript

<br />
<br />

[benmvp.com/learning-es6-parameter-handling](http://www.benmvp.com/learning-es6-parameter-handling/#spread-operator/)

=====

# Promises

Replace callbacks with promises

<br />
<br />

[benmvp.com/learning-es6-promises](http://www.benmvp.com/learning-es6-promises/)

=====

# Default parameters

Replace function body code with function header defaults

<br />
<br />

[benmvp.com/learning-es6-parameter-handling](http://www.benmvp.com/learning-es6-parameter-handling/#default-parameters)

NOTES:
_[4 minutes]_

- It's called default parameters
- With default parameters we can move our defaulting logic into the function header

=====

## String API

- [**`String.prototype.endsWith`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/endsWith)
- [**`String.prototype.includes`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/includes)
- [**`String.prototype.startsWith`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/startsWith)
- [`String.prototype.repeat`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/repeat)
- [`String.raw`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/raw)

NOTES:
- Just want to alert you to some new methods introduce with ES6 for `String`

=====

## Array API

- [**`Array.from`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/from)
- [`Array.of`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/of)
- [`Array.prototype.copyWithin`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
- [`Array.prototype.fill`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/fill)
- [**`Array.prototype.find`**](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/find)
- [`Array.prototype.findIndex`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/findIndex)

NOTES:
- Also some useful methods for `Array` too

=====

## Recap

0. Modules <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Classes <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Block scoping <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Destructuring <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Arrow functions <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Enhanced object literals <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Rest operator <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
0. Spread operator <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Promises <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Default parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. Array APIs <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  
0. String APIs <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->  

NOTES:
- Covered a lot so get the slides and follow the links for more details

=====



https://github.com/benmvp/react-esnext

=====

## Additional resources

- [_Learning ES6_](/learning-es6-series/)
- [Eventbrite React styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [`eslint-config-eventbrite-react`](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)

=====

# Shoutouts

/////

Devon Lindsey

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)

## We're hiring!   <!-- .element: class="fragment" -->

/////

# YOU!

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct

=====

<!-- .slide: data-background="url(../../img/giphy/thanks-jack-sparrow.gif) no-repeat center" data-background-size="contain"-->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

<br />

Code examples: [github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)
