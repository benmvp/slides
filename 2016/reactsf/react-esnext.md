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

How can we modularize this code?

```js
var Comment = React.createClass({
    // code using Remarkable dependency
});
var CommentList = React.createClass({
    // code using Comment
});
var CommentForm = React.createClass({
    // code
});
var App = React.createClass({
    // code using CommentForm & CommentList
});
ReactDOM.render(
    <App />,
    document.getElementById('app')
);
```
<!-- .element: class="large" -->

NOTES:
- Start with birds-eye view
- One big JS file
- Relying on `React`, `ReactDOM` & other dependencies being include by `<script>` tags in global scope
- React is all about reusable & composable components, but these aren't really reusable
- Also going to need data/API/utility libraries
- This obviously isn't scalable

/////

# Modules

Replace one file with many files

<br />
<br />

[2ality.com/2014/09/es6-modules-final.html](http://www.2ality.com/2014/09/es6-modules-final.html)

/////

###### Modules

`/components/Comment.js`
```js
import React from 'react';
import Remarkable from 'remarkable';

var Comment = React.createClass({
    // code using Remarkable module
});

export default Comment;
```

`/components/CommentList.js`
```js
import React from 'react';
import Comment from './Comment';

var CommentList = React.createClass({
    // code using Comment
});

export default CommentList;
```

NOTES:
- After some Babel & Webpack magic...
- We have separate files that use ES6 `import` & `export`
- Explicitly using `React` & `Remarkable`
- `Comment.js` exports `Comment` as default `export`, so...
- `CommentList` component can `import` as default
- Exporting implicitly makes the file a module enabling it be reused

/////

###### Modules

`/containers/App.js`
```js
import React from 'react';
import CommentList from '../components/CommentList';
import CommentForm from '../components/CommentForm';

var App = React.createClass({
    // code using CommentForm & CommentList
});

export default App;
```

`/index.js`
```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './containers/App';

ReactDOM.render(
    <App url="//localhost:3000/api/comments" pollInterval={2000} />,
    document.getElementById('app')
);
```

NOTES:
- Skipping `CommentForm` - nothing special
- `App.js` is similar to `CommentList.js`. It imports both `CommentList` & `CommentForm`
- `index.js` is now its own file pulling in `React`, `ReactDOM` and `App`. It's the only file that's not a module

/////

<!-- .slide: data-background="url(../../img/giphy/unimpressed-squidward.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- Chances are if you're using React, you're already modularizing your code, so this is nothing new
- Starting slow, trying to tackle the overall structure first before delving into smaller features

=====

Class factory creates component

```js
var CommentForm = React.createClass({
    propTypes: {
        onCommentSubmit: React.PropTypes.func.isRequired
    },
    _handleSubmit: function() {
        // form submission handling
    },
    getInitialState: function() {
        return {author: '', text: ''};
    },
    render: function() {
        <form onSubmit={this._handleSubmit} />
    }
});
```
<!-- .element: class="large" -->

NOTES:
- Now lets take a look at `CommentForm`
- The React component is a JS "class" with static properties & methods
- `React.createClass` is a class factory function that takes a huge object literal and creates the class
- This is certainly better than creating a class "manually" via constructor functions
- It basically allows for a lot of "magic" to happen before the class is actually created
- Callback handlers are auto-bound

/////

# Classes

Replace class factories with `class` syntax

<br />
<br />

[benmvp.com/learning-es6-classes](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Now we can replace assigning to the prototype or using custom class factories with native class syntax

/////

###### Classes

ES6 classes!

```js
class CommentForm extends React.Component {
    getInitialState() {
        return {author: '', text: ''};
    }
    _handleSubmit() {
        // form submission handling
    }
    render() {
        <form onSubmit={this._handleSubmit.bind(this)} />
    }
}
CommentForm.propTypes = {
    onCommentSubmit: React.PropTypes.func.isRequired
};
```
<!-- .element: class="large" -->

NOTES:
- `class` keyword
- `extends` `React.Component`
- `propTypes` now added afterwards as static properties
- Methods don't have `function` keyword
- Have to `.bind(this)` (no more auto-binding)
- React had to do a lot of work to make this all work
- Annoying that static properties have to be defined after

/////

###### Classes

```js
class CommentForm extends React.Component {
    static propTypes = {
        onCommentSubmit: React.PropTypes.func.isRequired
    }
    state = {author: '', text: ''}

    _handleSubmit() {
        // form submission handling
    }
    render() {
        <form onSubmit={this._handleSubmit.bind(this)} />
    }
}
```
<!-- .element: class="large" -->

[ES Class Fields & Static Properties](https://github.com/jeffmo/es-class-fields-and-static-properties) (Stage 1)

NOTES:
- Using class property declarations we can bring everything within the `class` definition

/////

###### Classes

Named imports + immediate export!

```js
import React, {Component, PropTypes} from 'react';

export default class CommentForm extends Component {
    static propTypes = {
        onCommentSubmit: PropTypes.func.isRequired
    }
    state = {author: '', text: ''}

    render() {
        <form onSubmit={this._handleSubmit.bind(this)} />
    }
}
```
<!-- .element: class="large" -->

NOTES:
- We can pull out the named imports, `Component` & `PropTypes`
- Can also immediately export the class as `default`

/////

###### Classes

Pull out `INITIAL_STATE` as a constant

```js
import React, {Component, PropTypes} from 'react';

var INITIAL_STATE = {author: '', text: ''};

export default class CommentForm extends Component {
    static propTypes = {
        onCommentSubmit: PropTypes.func.isRequired
    }
    state = INITIAL_STATE

    render() {
        <form onSubmit={this._handleSubmit.bind(this)} />
    }
}
```
<!-- .element: class="large" -->

NOTES:
- One last thing, is to pull out the initial state into a constant variable so that later you can reset the state when the form is submitted
- But what if there was a way to really make it a constant...

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

/////

###### Block scoping

Real constants!

```js
import React, {Component, PropTypes} from 'react';

const INITIAL_STATE = {author: '', text: ''};

export default class CommentForm extends Component {
    static propTypes = {
        onCommentSubmit: PropTypes.func.isRequired
    }
    state = INITIAL_STATE

    render() {
        <form onSubmit={this._handleSubmit.bind(this)} />
    }
}
```
<!-- .element: class="large" -->

NOTES:
- We use `const` because it's a constant! Finally!
- Variable declared `const` cannot be reassigned
- Also a variable declared `const` must be initialized

/////

###### Block scoping

[`var` hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)

```js
_handleSubmit(e) {
    e.preventDefault();

    var author = this.state.author;
    var text = this.state.text;

    if (!text || !author) {
        return;
    }

    this.props.onCommentSubmit({author: author, text: text});
    this.setState(INITIAL_STATE);
}
```
<!-- .element: class="large" -->

NOTES:
- Let's zoom into the `_handleSubmit` method
- We've got a couple of `var` declarations up top
- We really want to call `e.preventDefault()` immediately, but `var` declarations need to be first because of variable hoisting
- No time to explain variable hoisting

/////

###### Block scoping

No more variable hoisting!

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

/////

###### Block scoping

Don't [`prefer-const`](http://eslint.org/docs/rules/prefer-const)!

```js
_handleSubmit(e) {
    e.preventDefault();

    const author = this.state.author;
    const text = this.state.text;

    if (!text || !author) {
        return;
    }

    this.props.onCommentSubmit({author: author, text: text});
    this.setState(INITIAL_STATE);
}
```
<!-- .element: class="large" -->

NOTES:
- There's a popular trend to always use `const` when you can and only use `let` when you need to reassign
- I'm personally against this trend because it dilutes what `const` means
- I believe it's kind of a way to simulate immutability, but it's not at all
- We don't do this in other programming languages
- Plus, just because a variable is `const`, doesn't mean it can't be changed. If it's an object, properties cn be changed

=====

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

<!-- .slide: data-background="url(../../img/giphy/i-hate-you-brad-pitt.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I'm afraid that after we cover destructuring, you'll feel like this...
- But stick with me...

/////

###### Destructuring

Single assignment statement!

```js
_handleSubmit(e) {
    e.preventDefault();

    let {author, text} = this.state;

    if (!text || !author) {
        return;
    }

    this.props.onCommentSubmit({author: author, text: text});
    this.setState(INITIAL_STATE);
}
```
<!-- .element: class="large" -->

NOTES:
- With destructuring we can combine the two statements into one

/////

###### Destructuring

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

###### Destructuring

Named parameters!

```js
// before
function MyComponent(props) {
    return (
        <div style={props.style}>{props.content}</div>
    );
}

// after
function MyComponent({style, content}) {
    return (
        <div style={style}>{content}</div>
    );
}
```
<!-- .element: class="large" -->

NOTES:
- If you've got a stateless function you can immediately destructure `props` into the properties you need

/////

###### Destructuring

Array destructuring

```js
let [first, second, third] = [8, true, 11];
    // first=8, second=true, third=11
let [first, second, third] = ['no'];
    // first='no', second=undefined, third=undefined
let [, mo, day, yr] = /^(\d\d)-(\d\d)-(\d\d)$/.exec('05-06-16');
    // mo='05', day='06', yr='16'
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

###### Destructuring

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

===== <!-- .slide: data-transition="fade" -->

Where's the bug?

```js
_loadCommentsFromServer() {
    $.ajax({
        url: this.props.url,
        success: function(comments) {
            this.setState({comments: comments});
        }
    });
}
```
<!-- .element: class="large" -->

NOTES:

- Let's take jump to a different piece of code
- `_loadCommentsFromServer` method in App.js
- Can anyone spot the mistake in this code?
- We're passing a callback to `success` of the `ajax` request
- The callback calls `this.setState` with the returned data

///// <!-- .slide: data-transition="fade" -->

Undefined [`this`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/this)!

```js
_loadCommentsFromServer() {
    $.ajax({
        url: this.props.url,
        success: function(comments) {
            // `this` is undefined!
            this.setState({comments: comments});
        }
    });
}
```
<!-- .element: class="large" -->

NOTES:
- `this` is `undefined` in the callback function in strict mode
- `this` is the global scope (window) in loose mode
- Something that newbies scratch their head about
- Experienced JavaScript developers still run into it
- _[Water break]_

/////

ES3 fix

```js
_loadCommentsFromServer: function() {
    var self = this; // store reference to `this`

    $.ajax({
        url: this.props.url,
        success: function(comments) {
            // `self` is available in scope
            self.setState({comments: comments});
        }
    });
};
```
<!-- .element: class="large" -->

NOTES:
- In ES3, we solved this by storing a reference to `this` in a variable so that it’s available in the scope of the anonymous function
- Works, but pretty much every method has to assign `self` variable

/////

ES5 fix

```js
_loadCommentsFromServer: function() {
    $.ajax({
        url: this.props.url,
        success: function(comments) {
            this.setState({comments: comments});
        }
    }).bind(this); // pass in proper `this` context
};
```
<!-- .element: class="large" -->

NOTES:
- `bind()` was introduced in ES5 and it creates a new function, passing the specified `this`
- Underscore and other shim have a bind method so it can work with ES3 browsers
- This is what the React tutorial does
- Works, but messy syntax
- We need something better!

/////

# Arrow functions

Replace anonymous functions with arrow functions

<br />
<br />

[benmvp.com/learning-es6-arrow-functions/](http://www.benmvp.com/learning-es6-arrow-functions/)

NOTES:
- With arrow functions we can stop using anonymous functions

/////

###### Arrow functions

Arrow functions works how you would expect!

```js
$.ajax({
    url: this.props.url,
    success: (comments) => {
        this.setState({comments: comments});
    }
});
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way

```js
$.ajax({
    url: this.props.url,
    success: function(comments) {
        this.setState({comments: comments});
    }
}).bind(this); // pass in proper `this` context
```
<!-- .element: class="large" -->


NOTES:
- Arrow functions in ES6 solve this problem
- Arrow functions use what’s called “lexical scoping” for `this`
  - It's implicitly “inherited” from the enclosing scope, which in our case would be the class method
  - Essentially arrow functions work how you would expect it to
- An arrow function is literally an arrow (fat arrow) between parameters and body

/////

###### Arrow functions

```js
let squares = [1, 2, 3].map(value => value * value);
```
<!-- .element: class="large" -->

```js
let sum = [9, 8, 7, 6].reduce((prev, value) => prev + value, 0);
```
<!-- .element: class="large" -->

```js
$('button').click(e => {
  alert('Hello world!');
});
```
<!-- .element: class="large" -->

```js
setTimeout(() => {
  console.log('delayed for 1 second');
  console.log('using arrow function');
}, 1000);
```
<!-- .element: class="large" -->

```js
const MyComponent = ({style, content}) => {
    return (
        <div style={style}>{content}</div>
    );
}
```
<!-- .element: class="large" -->

NOTES:
- You’ll find that arrow functions come in handy most when used as a callback function.
  - The various higher-order functional programming array methods that were introduced with ECMAScript 5 (like `map`, `forEach`, `reduce`, etc.) work well with arrow functions.
  - Arrow functions can also be used as callback functions for event handlers (like `click`, `keydown`, etc)
- This also shows the different formats of arrow functions
  - Perentheses can be omitted if there is one parameter
  - Curly braces can be omitted if there's just a single `return` line

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
- [React Fundamentals Workshop](https://github.com/benmvp/react-workshop)

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
