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

## Level 0 - React

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
- But thankfully the API is really narrow so there's not that much learn
- More about _how_ as opposed to _what_
- You can build a lot of great UIs with just JSX & the React API

/////

![React tutorial in ES.next screenshot](../../img/react-esnext/react-esnext-app.png)

[React official tutorial](https://facebook.github.io/react/docs/tutorial.html) app

NOTES:
- With the official React tutorial you can learn how to use React by including a couple of script tags
- It's written in ES5, so you don't even have to worry about having to transpile ES6
- However...

=====

## image/diagram of ecosystem

## Level 1 - JavaScript

NOTES:
- React IMO is even easier to write with ES6+
- Outside of the JSX syntax, React is just JavaScript, so learning ES6+ makes writing it easier
- Chances are if you learn React, you're gonna learn it with some ES6+ concepts

/////

## Useful ES2015+ features w/ React

- Modules
- Classes
- Spread operator
- Destructuring
- Block scoping
- Arrow functions
- Object literal shorthand
- and more...

NOTES:
- Let's take a super quick look at some features

/////

```js
_handleSubmit(e) {
    e.preventDefault();

    let author = this.state.author;
    let text = this.state.text;

    if (!text || !author) {
        return;
    }

    this.props.onCommentSubmit({author: author, text: text});
    this.setState(INITIAL_STATE);
}
```
<!-- .element: class="large" -->

NOTES:
- Back to our code using `let`
- You will see that we're pulling out `author` & `text` from `this.state` and assigning to variables of the same name

/////

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

Single assignment statement + object literal shorthand!

```js
_handleSubmit(e) {
    e.preventDefault();

    let {author, text} = this.state;

    if (!text || !author) {
        return;
    }

    this.props.onCommentSubmit({author, text});
    this.setState(INITIAL_STATE);
}
```
<!-- .element: class="large" -->

NOTES:
- With destructuring we can combine the two statements into one
- Also using object literal shorthand!

/////

Object destructuring!

```js
// before
let author = this.state.author;
let text = this.state.text;

// after
let {author, text} = this.state;
```
<!-- .element: class="large" -->

```js
// before
let authorName = this.state.author;
let fullText = this.state.text;

// after
let {author: authorName, text: fullText} = this.state;
```
<!-- .element: class="large" -->

NOTES:
- We can also create a differently named variable

/////

Named parameters + arrow functions!

```js
// before
function MyComponent(props) {
    return (
        <div style={props.style}>{props.content}</div>
    );
}

// after
const MyComponent = ({style, content}) => (
    <div style={style}>{content}</div>
);
```
<!-- .element: class="large" -->

NOTES:
- If you've got a stateless function you can immediately destructure `props` into the properties you need

/////

Array destructuring

```js
let [first, second, third] = [8, true, 11];
    // first=8, second=true, third=11
let [first, second, third] = ['no'];
    // first='no', second=undefined, third=undefined
let [, mo, day, yr] = /^(\d\d)-(\d\d)-(\d\d)$/.exec('10-18-16');
    // mo='10', day='28', yr='16'
```
<!-- .element: class="large" -->

```js
function hi(greeting, [first, , third]) {
    // greeting='hello', first=1, third=3
}
hi('hello', [1, 2, 3]);
```
<!-- .element: class="large" -->

NOTES:
- Array destructuring works much the same way as object destructuring
- The main difference is:
  - Array destructuring uses an array literal pattern on the left hand side of the assignment
  - And the order in the pattern determines the assignment matching
- Focus on the third example which is a real-world use case with regular expression matches
  - Don't need to maintain the intermediate array
- Works kind of how tuples work in Python
- Work in function headers too!

/////

```js
let {
    name,
    nicknames: [primaryNick],
    misc: {
      netWorth: netWorthThousands
    }
  } = {
    name: 'Sean Combs',
    nicknames: ['Puffy', 'Puff Daddy', 'Diddy'],
    misc: {
      netWorth: 735000,
      birthdate: '1969-11-04'
    }
  };
```
<!-- .element: class="large" -->

Object + array + nested destructuring!

NOTES:
- You thought destructuring was unreadable
- What about when you combine object & array destructuring?
- And what about when you also leverage nested destructuring?
- Your brain explodes! That's what.
- This conveys the point that just because you _can_ do it doesn't mean you _should_
- You can revisit this slide if you really want to try and understand what's going on

/////

## [React + ES.next = ♥](https://www.youtube.com/watch?v=Fs4bJr1b7UU&list=PLQ0rErbcJANon4Dyy32o2EZnhHr-VWqhL&index=3)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/Fs4bJr1b7UU?list=PLQ0rErbcJANon4Dyy32o2EZnhHr-VWqhL" frameborder="0" allowfullscreen></iframe>

### Front Porch Austin 2016

NOTES:
- I gave a talk call _React + ES.next = ♥_ at Front Porch Austin earlier this year
- What I just talked about was just a small snippet of all the different features
- Feel free to watch the video (not now)

=====

## image/diagram of ecosystem

## Level 2 - Tooling

NOTES:
- Here's where things start getting a bit gnarly
- There's been a lot of talk about "JavaScript Fatigue" and a lot of it is aimed at the tooling challenge
- I think there problem is that there's so much choice and you need to know how the tools work before you can get up and running

/////

## React Dev Tools

For debugging React props & state

# SCREENSHOT

[Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) | [Firefox](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)

NOTES:
- Let's start easy
- The React Dev Tools are super helpful in debugging React props & state
- You just browse the React component tree just like the DOM tree and you can look at the component props as well as the state
- Available for Chrome & Firefox. Sorry Edge users.

/////

## Package managers

Helps you include & manage helper libraries

# [NPM logo](https://www.npmjs.com)
# [Bower logo](https://bower.io)

NOTES:
- Two major players are NPM & Bower
- But pretty much everyone uses NPM
- Never used Bower before, but have seen some older packages that area available on both
- Funniest thing: you install Bower with NPM!

/////

## NPM resources

- [Node Version Manager](https://github.com/creationix/nvm)
- [Awesome npm resources and tips](https://github.com/sindresorhus/awesome-npm)

NOTES:
- If you decide to go the npm route (you should) here are some resources

/////

## Bundler

Helps gather all the various dependencies & transpile ES6+

- Webpack
- Browserify
- Rollup
- JSPM
- RequireJS (don’t use!)

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
