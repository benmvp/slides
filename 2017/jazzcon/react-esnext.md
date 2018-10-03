# React + ES.next = ♥

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@Jazz_Con](https://twitter.com/hashtag/Jazz_Con)    

<br />

March 24, 2017  

NOTES:
- My name is Ben Ilegbodu
- Super excited to talk about my two favorite things
- React and what I'm calling ES.next
- And how they go so well together
- Posted link to slides on twitter so you can follow-up afterwards
- Gonna show lots of potentially new syntax and you'll need to look at it longer than I can show to get through everything

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: white 4px" -->

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

## What this talk is **not** about... 😐

<br />

- Why to use React
- How to develop in React
- Every detail about ES2015+
- How to transpile ES2015+

NOTES:
- Just so we're clear...

/////

## What this talk is about! 😄

<br />

- Learning ES2015+ ➜ ➜ ➜ applying in React
- Lots of code
- Fast-paced!

NOTES:
- However!

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
		<img src="../../img/family/family-tahoe-beach-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family on the beach at Lake Tahoe" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Senior UI Engineer and Frontend Platform Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Like to call it Ticketmaster but for the people!
- Many conferences use it for registration
- I work on the Frontend Platform team and right now we're in the midst of a transition from Backbone/Marionette to React

/////

<!-- .slide: data-background="url(../../img/giphy/james-harden-pot-cook.gif) no-repeat center" data-background-size="contain" -->

NOTES:
- I also absolutely love basketball - both playing & watching
- But you didn't come to hear about me. At least I hope not
- You came to here about...

=====

## Agenda

0. Modules
0. Classes
0. Block scoping
0. Destructuring
0. Spread operator
0. Arrow functions
0. Promises
0. Async functions

NOTES:
- Here's the agenda
- One of the things I like about React is that it's basically JavaScript, outside JSX & lifecycle things
- So in the little time we have together wanted to focus on these features
- Reason picking these features is because they'll help write clear & concise code
- They target a wide range of audiences
- Will see other features along the way that I will explain quickly

/////

![React tutorial in ES.next screenshot](../../img/react-esnext/react-esnext-app.png)
<!-- .element: style="width: 75%"-->

NOTES:
- The code we'll be looking at derives from the original React tutorial
- Basically a TODO app masquerading as a commenting app

=====

# Let's start easy

=====

How can we modularize this code?

```js
// globals: React, ReactDOM, Remarkable, jQuery

var Comment = React.createClass({
    // code using Remarkable dependency
})
var CommentList = React.createClass({
    // code using Comment
})
var CommentForm = React.createClass({
    // code w/ no dependencies
})
var App = React.createClass({
    // code using CommentForm & CommentList
})
ReactDOM.render(<App url="/api/comments" pollInterval={2000} />,
    document.getElementById('app'))
```
<!-- .element: class="large" -->

NOTES:
- Start with birds-eye view
- One big JS file
- Relying on `React`, `ReactDOM` & other dependencies being included by `<script>` tags in global scope
- React is all about reusable & composable components, but these aren't really reusable
- Also going to need data/API/utility libraries
- This obviously isn't scalable

/////

# Modules

Replace one file with many files

<br />
<br />

[_ECMAScript 6 Modules: the final syntax_](http://www.2ality.com/2014/09/es6-modules-final.html)

/////

###### Modules

`/components/Comment.js`
```js
import React from 'react'
import Remarkable from 'remarkable'

var Comment = React.createClass({
    // code using Remarkable module
})

export default Comment
```

`/components/CommentList.js`
```js
import React from 'react'
import Comment from './Comment'

var CommentList = React.createClass({
    // code using Comment
})

export default CommentList
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
import React from 'react'
import CommentList from '../components/CommentList'
import CommentForm from '../components/CommentForm'

var App = React.createClass({
    // code using CommentForm & CommentList
})

export default App
```

`/index.js`
```js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './containers/App'

ReactDOM.render(
  <App url="/api/comments" pollInterval={2000} />,
  document.getElementById('app')
)
```

NOTES:
- Skipping `CommentForm` - nothing special
- `App.js` is similar to `CommentList.js`. It imports both `CommentList` & `CommentForm`
- `index.js` is now its own file pulling in `React`, `ReactDOM` and `App`. It's the only file that's not a module

=====

Class factory creates component

```js
var App = React.createClass({
  propTypes: {
    url: React.PropTypes.string.isRequired,
	pollInterval: React.PropTypes.number
  },
  getDefaultProps: function() {
    return {pollInterval: 5000}
  },
  getInitialState: function() {
    return {comments: []}
  },
  componentDidMount: function() { },
  componentWillUnmount: function() { },
  _handleCommentSubmit: function(comment) { },
  render: function() { }
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

[_Learning ES6: Classes_](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Now we can replace assigning to the prototype or using custom class factories with native class syntax

/////

ES6 class structure

```js
class MyClass extends BaseClass {
  constructor() { }
  static staticMethodA() { }
  static staticMethodB() { }
  methodOne() { }
  methodTwo() { }
}
```
<!-- .element: class="large" -->

NOTES:
- `class` keyword
- `extends` base class
- supports `constructor`, instance & `static` methods
- doesn't support properties (yet)

/////

###### Classes

React with ES6 classes!

```js
class App extends React.PureComponent {
  constructor() {
    this.state = {comments: []}
  }

  componentDidMount() { }
  componentWillUnmount() { }
  _handleCommentSubmit(comment) { }

  render() { }
}
App.propTypes = {
  url: React.PropTypes.string.isRequired,
  pollInterval: React.PropTypes.number
}
App.defaultProps = {pollInterval: 5000}
```
<!-- .element: class="large" -->

NOTES:
- `class` keyword
- `extends` `React.Component`
- `propTypes` now added afterwards as static properties
- Methods don't have `function` keyword
- Have to `.bind(this)` (no more auto-binding)
- React had to do a lot of work to make this all work
- `this.state` in `constructor` instead of `getInitialState`
- Annoying that static properties have to be defined after

/////

###### Classes

```js
class App extends React.PureComponent {
  static propTypes = {
    url: React.PropTypes.string.isRequired,
    pollInterval: React.PropTypes.number
  }
  static defaultProps = {pollInterval: 5000}

  state = {author: '', text: ''}

  componentDidMount() { }
  componentWillUnmount() { }

  _handleCommentSubmit(comment) { }

  render() { }
}
```
<!-- .element: class="large" -->

[Public class fields](https://tc39.github.io/proposal-class-public-fields/) (Stage 2)

NOTES:
- Using class property declarations we can bring everything within the `class` definition

/////

###### Classes

Named imports + immediate export!

```js
import React, {PureComponent} from 'react'

export default class App extends PureComponent {

}
```
<!-- .element: class="large" -->

<br />

-----

##### Before

```js
import React from 'react'

class App extends React.PureComponent {

}

export default App
```
<!-- .element: class="large" -->

NOTES:
- We can pull out the named imports, `Component` & `PropTypes`
- Can also immediately export the class as `default`

=====

<!-- .slide: data-background="url(../../img/giphy/clumsy-digging.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- Now that we've got the scaffolding out of the way
- Let's dig deeper by honing into a problem

/////

Let's get to work!

```js
// App.js
_handleCommentSubmit(comment) {
  var comments = this.state.comments
  var newComment = comment
  var newComments

  newComment.id = Date.now()

  newComments = comments.concat([newComment])
  this.setState({comments: newComments})

  $.ajax({
    url: this.props.url,
    type: 'POST',
    data: comment,
    success: function(resJson) {
       this.setState({comments: resJson})
    }.bind(this),
    error: function(xhr, status, err) {
      this.setState({comments})
      console.error(this.props.url, status, err.toString())
    }.bind(this)
  })
}
```
<!-- .element: class="small" -->

NOTES:
- Want to just focus on this one method in top-level App container component
- Handles submission of the form via AJAX (w/ optimistic updates)
- Uses `concat` to maintain immutability when adding `newComment`
- Uses jQuery to make AJAX call
- Ugly use of `.bind()` in callbacks
- We'll use the features to modernize things
- Will go on some tangents though...

=====

[`var` hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting)

```js
// App.js

_handleCommentSubmit(comment) {
  var comments = this.state.comments
  var newComment = comment
  var newComments

  newComment.id = Date.now()

  newComments = comments.concat([newComment])

  // remaining code
}
```
<!-- .element: class="large" -->

/////

# Block scoping

Replace `var` with `let` & `const`

<br />
<br />

[_Learning ES6: Block Scoping with let & const_](http://www.benmvp.com/learning-es6-block-level-scoping-let-const/)

NOTES:
- In fact there are two: `let` & `const`
- Together they're called Block scoping
- With block scoping we can replace `var` with `let` & `const`

/////

###### Block scoping

```js
_handleCommentSubmit(comment) {
  let comments = this.state.comments
  let newComment = comment

  newComment.id = Date.now()

  let newComments = comments.concat([newComment])
}
```
<!-- .element: class="large" -->

-----

#### Before

```js
_handleCommentSubmit(comment) {
  var comments = this.state.comments
  var newComment = comment
  var newComments

  newComment.id = Date.now()

  newComments = comments.concat([newComment])
}
```

/////

<!-- .slide: data-background="url(../../img/giphy/unimpressed-squidward.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- But really this is pretty unimpressive
- Bug fix masquerading as a feature
- It's really how `var` should've worked all along
- More so fixing a deficiency rather than supplying new functionality

/////

`const`

```js
const NAME_KEY = 'name';
const data = {key: 'adam', value: 'eve'};
const token;  // ReferenceError for not assigning a value

NAME_KEY = 'key'; // TypeError for changing a const value

data.key = 'moses'; // mutations are not an error!
```
<!-- .element: class="large" -->

Use [`Object.freeze()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/freeze) for objects!

<!-- .element: class="fragment" -->

Use [Immutable.js](https://facebook.github.io/immutable-js/) or [`seamless-immutable`](https://github.com/rtfeldman/seamless-immutable)!

<!-- .element: class="fragment" -->

NOTES:
- `const` is pretty straightforward
- Can’t change a value that is declared `const`
- Must assign an initial value if declared `const`
- One interesting thing is that if an object is `const` its properties are not
  - You can still assign to them
  - Need to use `Object.freeze`
  - Or Immutable.js from Facebook
  - This probably why other type-safe languages prevent `const` objects

=====

```js
// App.js
_handleCommentSubmit(comment) {
  let comments = this.state.comments;
  let newComment = comment;

  newComment.id = Date.now();

  let newComments = comments.concat([newComment]);
  this.setState({comments: newComments});

  $.ajax({
    url: this.props.url,
    type: 'POST',
    data: comment,
    success: function(resJson) {
      this.setState({comments: resJson});
    }.bind(this),
    error: function(xhr, status, err) {
      this.setState({comments});
      console.error(this.props.url, status, err.toString());
    }.bind(this)
  });
}
```
<!-- .element: class="small" -->

NOTES:
- Want to just focus on this one method in top-level App container component
- Handles submission of the form via AJAX (w/ optimistic updates)
- Because of time constraints already has some ES6: class syntax, `let`, object literal, shorthand, etc.
- Uses `concat` to maintain immutability when adding `newComment`
- Uses jQuery to make AJAX call
- Ugly use of `.bind()` in callbacks
- We'll use the 5 features to modernize things

=====

```js
// App.js

_handleCommentSubmit(comment) {
	let comments = this.state.comments

	// remaining code
}
```
<!-- .element: class="large" -->

NOTES:

- Let's jump right in
- Want to focus on the first statement
- Pulling out the `comments` property from `this.state` and assigning it to a variable with the same name

/////

# Destructuring

Replace multiple assignments with a single one

<br />
<br />

[_Learning ES6: Destructuring_](http://www.benmvp.com/learning-es6-destructuring/)

NOTES:
- It's called Destructuring
- With destructuring we can reduce multiple assignments down to one
- Be advised, destructuring is probably the most "out there" syntax addition
- It's ok if you don't understand it at first

/////

<!-- .slide: data-background="url(../../img/giphy/i-hate-you-brad-pitt.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I'm afraid that after we cover destructuring, you'll feel like this...
- Really just shooting the messenger
- But stick with me...

/////

<!-- .slide: data-background="url(../../img/giphy/brad-pitt-dancing.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- Eventually I think you'll be super excited about them

/////

###### Destructuring

"DRY-er" assignment!

```js
// App.js

_handleCommentSubmit(comment) {
	let {comments} = this.state

	// remaining code
}
```
<!-- .element: class="large" -->

-----

##### Before

```js
_handleCommentSubmit(comment) {
	let comments = this.state.comments

	// remaining code
}
```
<!-- .element: class="large" -->

NOTES:
- Uses object literal pattern
- Removes the duplication of `comments`
- But we're only seeing one variable declared, so we're not seeing the full power of destructuring
- So let's look at a different example in `CommentForm` with more properties in `this.state`

/////

###### Destructuring

Object destructuring!

```js
// before
let author = this.state.author
let text = this.state.text

// after
let {author, text} = this.state
```
<!-- .element: class="large" -->

<br />

```js
// before
let authorName = this.state.author
let fullText = this.state.text

// after
let {author: authorName, text: fullText} = this.state
```
<!-- .element: class="large" -->

NOTES:
- We can also create a differently named variable

/////

###### Destructuring

Named parameters!

```js
// after
function MyComponent({children, style}) {
    return (
        <div style={style}>{children}</div>
    )
}

// before
function MyComponent(props) {
    return (
        <div style={props.style}>{props.children}</div>
    )
}
```
<!-- .element: class="large" -->

```js
<MyComponent style="dark">Stateless func!</MyComponent>
```
<!-- .element: class="large" -->

NOTES:
- React supports stateless functions which receive the `props` as a parameter
- You can immediately destructure `props` into the properties you need

/////

### Array destructuring

```js
let [a, b, c] = [8, true, 11];
    // a=8, b=true, c=11
let [a, b, c = 9] = ['no'];
    // a='no', b=undefined, c=9
let [, mo, day, yr] = /^(\d\d)-(\d\d)-(\d\d)$/.exec('03-24-17');
    // mo='03', day='24', yr='17'
```
<!-- .element: class="large" -->

```js
function hi(a, [b, , d]) {
    // a='hello', b=1, d=3
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
      netWorth: netWorthThousands=0
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

=====

```js
// App.js

_handleCommentSubmit(comment) {
	let {comments} = this.state

	// assignment, not a copy!
	let newComment = comment

	// also mutating `comment` param!
	newComment.id = Date.now()

	// clone `comments` + append `newComment`
	let newComments = comments.concat([newComment])

	// setState + ajax stuffs
}
```
<!-- .element: class="large" -->

NOTES:
- Here's more of our code, annotated a bit
- Adding `id` property to `comment` to create `newComment` (except we're mutating)
- Then appending `newComment` to `comments` via `concat` to maintain immutability
- This is a common pattern in React to never mutate objects or arrays

/////

# Spread operator

Maintain immutability with the spread operator

<br />
<br />

[_Learning ES6: Parameter handling_](http://www.benmvp.com/learning-es6-parameter-handling/#spread-operator)

/////

###### Spread operator

Maintain immutability!

```js
_handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = {...comment, id: Date.now()}
	let newComments = [...comments, newComment]

	// setState + ajax stuffs
}
```
<!-- .element: class="large" -->

-----

##### Before

```js
_handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = comment

	newComment.id = Date.now()

	let newComments = comments.concat([newComment])
}
```
<!-- .element: class="large" -->

/////

`Math.max.apply`???

```js
var maxValueNormal = Math.max(33, 2, 9),
    arrayOfValues = [33, 2, 9],
    maxValueFromArray = Math.max.apply(null, arrayOfValues)

// output: 33  33
console.log(maxValueNormal, maxValueFromArray)
```
<!-- .element: class="large" -->

NOTES:
_[21 minutes]_

- `Math.max` accepts an arbitrary number of numeric parameters and returns the maximum one
- If you want to get the maximum value of an array of numbers, you have to call `Math.max.apply`
- `apply` converts the array of values into a sequence of parameters
- But it's kind of esoteric
  - Plus you have to specify `null` as the context
- Maybe there's an ES6 feature for this?

/////

###### Spread operator

No more `apply`!

```js
let arrayOfValues = [33, 2, 9]
let maxValueFromArray = Math.max(...arrayOfValues)

// output: 33
console.log(maxValueFromArray)
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way

```js
var arrayOfValues = [33, 2, 9],
    maxValueFromArray = Math.max.apply(null, arrayOfValues)

// output: 33
console.log(maxValueFromArray)
```
<!-- .element: class="large" -->

NOTES:
- Instead of calling `apply` we can use the spread operator
- It's 3 dots preceding a parameter in a function call
- The spread operator _spreads_ out the array into individual parameters

/////

###### Spread operator

Creating an array

```js
// verbose
let values = new Array(2, 3, 4)

// shorthand
let values = [2, 3, 4]
```
<!-- .element: class="large" -->

------

Spreading into an array

```js
// [1, 2, 3, 4, 5]
let verbose = new Array(1, ...values, 5)

// [1, 2, 3, 4, 5]
let shorthand = [1, ...values, 5]
```
<!-- .element: class="large" -->

NOTES:
- So what does this have to do w/ maintaining immutability?

/////

###### Spread operator

Spread operator with object literals!

```js
let warriors = {Steph: 95, Klay: 82, Draymond: 79}
let newWarriors = {
    ...warriors,
    Kevin: 97
}
```
<!-- .element: class="large" -->

-----

#### ES5 way

```js
let warriors = {Steph: 95, Klay: 82, Draymond: 79}
let newWarriors = _.assign({}, warriors, {
    Kevin: 97
})
```
<!-- .element: class="large" -->

[Spread Properties](https://github.com/sebmarkbage/ecmascript-rest-spread) (Stage 3)

NOTES:
- Now we copy objects while adding new properties in one object literal definition
- It's a Stage 3 ES feature
- The ES5 way was to use `_.assign()`
- ES6 did introduce Object.assign() to handle this as well, but I'll always prefer syntax

/////

###### Spread operator

[JSX spread attributes](https://facebook.github.io/react/docs/jsx-spread.html)!

```js
function TextInput({type, defaultValue, inputAttrs}) {
  return (
    <input
      {...inputAttrs}
      type={type}
      defaultValue={defaultValue}
    />
  )
}
```
<!-- .element: class="large" -->

NOTES:
- Similar to object spread, are JSX spread attributes
- It allows you to take an object and make all of its properties attributes on a component
- I tend to avoid it in favor of being explicit about the attributes I'm setting

/////

###### Spread operator

```js
_handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = {...comment, id: Date.now()}
	let newComments = [...comments, newComment]

	// setState + ajax stuffs
}
```
<!-- .element: class="large" -->

-----

##### Before

```js
_handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = comment

	newComment.id = Date.now()

	let newComments = comments.concat([newComment])

	// setState + ajax stuffs
}
```

NOTES:
- So now these lines make a bit more sense knowing how the spread operator works

=====

Where's the bug?

```js
_handleCommentSubmit(comment) {
	// initializations

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resComments) {

			this.setState({comments: resComments})
		}
	})
}
```
<!-- .element: class="large" -->


NOTES:
- Can anyone spot the mistake in this code?
- It's a modified version of the ajax call to submit the comment
- We're passing a callback to `success` of the `ajax` request
- The callback calls `this.setState` with the returned data
- And no the bug is not using `jQuery`

///// <!-- .slide: data-transition="fade" -->

Undefined [`this`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/this)!

```js
_handleCommentSubmit(comment) {
	// initializations

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resComments) {
			// `this` is undefined!
			this.setState({comments: resComments})
		}
	})
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
_handleCommentSubmit: function(comment) {
    var self = this // store reference to `this`

	// initializations

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resComments) {
			// `self` is available in scope
            self.setState({comments: resComments})
		}
	})
}
```
<!-- .element: class="large" -->

NOTES:
- In ES3, we solved this by storing a reference to `this` in a variable so that it’s available in the scope of the anonymous function
- Works, but pretty much every method has to assign `self` variable

/////

ES5 fix

```js
// in App.js

_handleCommentSubmit: function(comment) {
	// initializations

    $.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resComments) {
            this.setState({comments: resComments})
		}.bind(this) // pass in proper `this` context
	})
}
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

[_Learning ES6: Arrow functions_](http://www.benmvp.com/learning-es6-arrow-functions/)

NOTES:
- With arrow functions we can stop using anonymous functions

/////

###### Arrow functions

Arrow functions works how you would expect!

```js
$.ajax({
	url: this.props.url,
	data: comment,
	success: (resJson) => {
		this.setState({comments: resJson})
	}
})
```
<!-- .element: class="large" -->

-----

#### ES5 way

```js
$.ajax({
	url: this.props.url,
	data: comment,
	success: function(resJson) {
		this.setState({comments: resJson})
	}.bind(this) // pass in proper `this` context
})
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
let squares = [1, 2, 3].map(value => value * value)
```
<!-- .element: class="large" -->

```js
let sum = [9, 8, 7, 6].reduce((prev, value) => prev + value, 0)
```
<!-- .element: class="large" -->

```js
setTimeout(() => {
	console.log('delayed for 1 second')
	console.log('using arrow function')
}, 1000)
```
<!-- .element: class="large" -->

```js
const alertUser = (message) => {
	alert(message)
})
```
<!-- .element: class="large" -->

```js
const MyComponent = ({children, style}) => (
    <div style={style}>{children}</div>
)
```
<!-- .element: class="large" -->

NOTES:
- You’ll find that arrow functions come in handy most when used as a callback function.
  - The various higher-order functional programming array methods that were introduced with ECMAScript 5 (like `map`, `forEach`, `reduce`, etc.) work well with arrow functions.
  - Arrow functions can also be used as callback functions for event handlers (like `click`, `keydown`, etc)
- This also shows the different formats of arrow functions
  - Parentheses can be omitted if there is one parameter
  - Curly braces can be omitted if there's just a single `return` line
- The last example is a stateless function using arrow functions with header destructuring

=====

Parameters list is unclear

```js
function join(separator) {
  var values = []

  // arguments is not an array, just "array-like"
  for (var i = 1; i < arguments.length; i++) {
    values.push(arguments[i])
  }

  return values.join(separator)
}

// output: tic-tac-toe
join('-', 'tic', 'tac', 'toe')
```
<!-- .element: class="large" -->

NOTES:
- Ok, let's go on a small tangent
- Let me set the stage
- We have here a `join` method that takes a separator string followed by an unlimited number of parameters to join
- The fact that `join` takes more than one parameter is unclear let alone that it accepts an arbitrary number of them
- Because `join` uses the `separator` parameter the implementation has to start at index `1` of `arguments`
- And even if it could start at 0, `arguments` is only array-like so it doesn't have the `join` method that arrays have
- **NEED:** is an easy way to get an array of the parameters after `separator`
- And guess what? There's an ES6 feature for that

/////

# Rest operator

Replace `arguments` with an array

<br />
<br />

[_Learning ES6: Parameter handling_](http://www.benmvp.com/learning-es6-parameter-handling/#rest-parameters/)

/////

###### Rest operator

Clearer function signature!

```js
const join = (separator, ...values) => values.join(separator)

// output: tic-tac-toe
join('-', 'tic', 'tac', 'toe')
```
<!-- .element: class="large" -->

-----

#### Before

```js
function join(separator) {
  var values = []

  // arguments is not an array, just "array-like"
  for (var i = 1; i < arguments.length; i++) {
    values.push(arguments[i])
  }

  return values.join(separator)
}
```

NOTES:
- That's it!
- The three dots, called the rest operator, before the parameter make it a rest parameter
  - The rest parameter is an `Array` containing the rest of the parameters
  - Hence the name!
- Because `values` is a true array in the example, we can call join on it
- It’s also much **clearer** to see that `join()` takes an infinite number of parameters
- Rest parameter should pretty much replace all uses of the `arguments` keyword!

/////

###### Rest operator

### Rest operator
Multiple parameters ➞ array (function header)

```js
// values = ['tic', 'tac', 'toe']
const join = (separator, ...values) => values.join(separator)

join('-', 'tic', 'tac', 'toe')
```
<!-- .element: class="large" -->

-----

### Spread operator
Array ➞ multiple parameters (function call)

```js
let arrayOfValues = [33, 2, 9]
let maxValueFromArray = Math.max(...arrayOfValues)
    // just like: Math.max(33, 2, 9)
```
<!-- .element: class="large" -->

NOTES:
- Spread operator & rest operator look the exact same
- The spread operator works w/ function _call_ parameters
  - Takes an array literal and converts each element to individual parameters
- The rest operator works w/ function _header_ parameters
  - Takes individual parameters and puts them together into an array
- They are opposites of each other

/////

###### Rest operator

Object destructuring + rest operator!

```js
const MyComponent = ({type, value, ...restProps}) => {
  // `restProps` has everything in props
  // except `type` & `value`

  // render stuffs
}
```
<!-- .element: class="large" -->

[Rest Properties](https://github.com/sebmarkbage/ecmascript-rest-spread) (Stage 3)

NOTES:
- Rest properties are coming in soon to ECMAScript. They're in Stage 3
- Not in ES2015, not ES2016, but future JavaScript (maybe ES2017)

=====

<!-- .slide: data-background="url(../../img/giphy/fireman-ladder-exercise.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- We've talked about destructuring, spread operator & arrow functions
- Let's take things up a level now

/////

```js
_handleCommentSubmit(comment) {
	// initializations

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: (resJson) => {
			this.setState({comments: resJson})
		},
		error: (xhr, status, err) => {
			this.setState({comments})
			console.error(this.props.url, status, err.toString())
		}
	})
}
```
<!-- .element: class="large" -->

NOTES:
- Made the ajax call a bit better with arrow functions
- It's fine, but I don't like using jQuery, especially just for ajax
- Including it could lead to improper React development, relying too much on refs
- In addition, callbacks are so 2013
- There's gotta be something better!

/////

# Promises

Replace callback-style programming with promises

<br />
<br />

[_Learning ES6: Promises_](http://www.benmvp.com/learning-es6-promises/)

NOTES:
- With promises we can stop using callback-style programming
- This is where we start to ratchet it up a bit

/////

###### Promises

New [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) + Promises

```js
_handleCommentSubmit(comment) {
  // initializations

  fetch(this.props.url, {
    method: 'POST',
    body: JSON.stringify(comment)
  })
    .then((res) => res.json())
    .then((resJson) => {
      this.setState({comments: resJson})
	})
    .catch((ex) => {
      console.error(this.props.url, ex)
    })
}
```
<!-- .element: class="large" -->

Promises are the future of asynchronous programming

NOTES:
- We can replace jquery ajax with Fetch browser API which gives us `window.fetch`
- Instead of taking callback functions, it's promised-based so it returns a promise object
- Pretty much all future asynchronous APIs will be promised-based
- Because promises are more flexible than callbacks
- How so...?

/////

###### Promises

Passing promises + chaining reactions

```js
const fetchJson = (path, options) => (
  fetch(`${DOMAIN}${path}`, options)
    .then((res) => res.json())
)
```
<!-- .element: class="large" -->

```js
const fetchComments = () => fetchJson('/api/comments')
```
<!-- .element: class="large" -->

```js
const getUniqueCommentAuthors = () => (
  fetchComments()
    .then((comments) => comments.map(({author}) => author))
    .then((authors) => _.uniq(authors))
	.catch((ex) => console.error('Something bad happened', ex))
)
```
<!-- .element: class="large" -->

```js
getUniqueCommentAuthors()
	.then((uniqueAuthors) => { this.setState({uniqueAuthors}) })
```
<!-- .element: class="large" -->

NOTES:
- Let's take a look at what a typical set of API utils might look like
- This shows the power of promises
- At the bottom we have a function that gets the unique set of comment authors
- It does that by making a call to `fetchComments` that returns a promise
- We set that `fetchComments` actually returns the result of `fetchJson`
- The promise that `fetch` returns is "resolved" when the API request returns
- The `then` & `catch` are called "reactions"
- If the request is successful, `then` it'll convert the response to JSON
- If the request is unsuccessful OR the JSON parsing fails, then `console.error`

/////

###### Promises

Converting callback-style to Promises

```js
const sleep = (delay = 0) => (
    new Promise((resolve) => {
        setTimeout(resolve, delay)
    })
)

sleep(3000)
  .then(() => getUniqueCommentAuthors())
  .then((uniqueAuthors) => { this.setState({uniqueAuthors}) })
```
<!-- .element: class="large" -->

Sleep function... in JavaScript!

/////

###### Promises

Converting callback-style to Promises

```js
const readFile = (filePath) => (
	new Promise((resolve, reject) => {
		fs.readFile(filePath, (err, data) => {
			if (err) { reject(err) }
			resolve(data)
		})
	})
)

readFile('path/to/file')
  .then((data) => console.log('Here is the data', data))
  .catch((ex) => console.error('Arg!', ex))
```
<!-- .element: class="large" -->

Friendlier Node file system methods!

/////

###### Promises

Simultaneous async requests as single Promise

```js
Promise.all([
	fetchComments(),
	fetchPosts(),
	fetchUsers()
])
  .then((responses) => {
	  let [comments, posts, users] = responses

	  this.setState({
		  comments,
		  posts,
		  users
	  })
  })
```
<!-- .element: class="large" -->

=====

```js
_handleCommentSubmit(comment) {
  // initializations

  fetch(this.props.url, {
    method: 'POST',
    body: JSON.stringify(comment)
  })
    .then((res) => res.json())
    .then((resJson) => this.setState({comments: resJson}))
    .catch((ex) => {
      this.setState({comments})
      console.error(this.props.url, ex)
    })
}
```
<!-- .element: class="large" -->

NOTES:
- So hopefully I've convinced you in that short time that Promises are better than callback-style programming
- Because you can chain promises, instead of having callback-hell there's just a flat level of chains
- However, you're still passing anonymous functions
- Asynchronous programming still makes you write code control flow differently
- Until...

/////

# Async Functions

Use normal control flow with `async`/`await`

<br />
<br />

[_Exploring ES2016 and ES2017: Async functions_](http://exploringjs.com/es2016-es2017/ch_async-functions.html)

NOTES:
- With async functions we can use normal control flow with `async`/`await`

/////

###### Async Functions

Synchronous control flow!

```js
async _handleCommentSubmit(comment) {
	// initializations
	try {
		let res = await fetch(this.props.url, {
			method: 'POST',
			body: JSON.stringify(comment)
		})
		newComments = await res.json()
	} catch (ex) {
		console.error(this.props.url, ex)
		newComments = comments
	}

	this.setState({comments: newComments})
}
```
<!-- .element: class="large" -->

How does this all work???

NOTES:
- So here we are: no more anonymous arrow functions
- We have asynchronous code because we're making a `fetch` but it looks like normal synchronous code
- The key are the new `async` & `await` keywords being introduced in ES2017
- Declare the function/method as `async`
- Then in your code any function that returns a promise can use `await`
- The code literally sits there until the promise is resolved; then it gets assigned
- It's non-blocking (control is returned to event loop), but it waits
- And you handle exceptions the same way you always do, with a `try-catch`
- How does this all work?

/////

<!-- .slide: data-background="url(../../img/giphy/shia-magic.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- It's basically magic... well it's probably the closest thing we have to magic in JavaScript
- If you take a peek at all Babel has to do you'll see that it's basically magic
- But in reality async functions bring together Promises & Generators for synchronous control flow

/////

###### Async Functions

```js
const funWithAsync = async () => {
  let uniqueAuthors = await getUniqueCommentAuthors()

  await sleep(1500)

  let packageInfo = JSON.parse(await readFile('./package.json'))

  await sleep(3000)

  let [comments, posts, users] = await Promise.all([
    fetchComments(),
    fetchPosts(),
    fetchUsers()
  ])

  return 42
}
```
<!-- .element: class="large" -->

NOTES:
- Remember all of our Promise-based functions from earlier
- Well inside of an `async` function, we can `await` all of their values
- Return values are always promises so 42 will get wrapped in a promise
- This means something else can `await` `funWithAsync` in sync control flow
- That's the power of async functions

/////

<!-- .slide: data-background="url(../../img/giphy/mind-blown.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- If you're at all like me, this is how you're feeling

=====

### Before

```js
// App.js
_handleCommentSubmit(comment) {
	let comments = this.state.comments;
	let newComment = comment;
	let newComments;

	newComment.id = Date.now();

	newComments = comments.concat([newComment]);
	this.setState({comments: newComments});

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resJson) {
			this.setState({comments: resJson});
		}.bind(this),
		error: function(xhr, status, err) {
			this.setState({comments});
			console.error(this.props.url, status, err.toString());
		}.bind(this)
	});
}
```
<!-- .element: class="small" -->

NOTES:
- So if you recall this was our original code
- And with everything we learned, it turned into...

/////

### After

```js
// App.js
async _handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = {...comment, id: Date.now()}
	let newComments = [...comments, newComment]

	this.setState({comments: newComments})

	try {
		let res = await fetch(this.props.url, {
			method: 'POST',
			body: JSON.stringify(comment)
		})
		newComments = await res.json()
	} catch(ex) {
		console.error(this.props.url, ex)
		newComments = comments
	}

	this.setState({comments: newComments})
}
```

NOTES:
- Uses destructuring, spread operator
- Promises & arrow functions behind the scenes
- And async functions front and center

=====

[![react-esnext Gitub repo](../../img/react-esnext/repo.png)](https://github.com/benmvp/react-esnext)

[github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)

NOTES:
- And to be even more helpful I crated a repo where I take the ES5 React tutorial and go step-by-step converting it to ES2015+
- Feel free to star the repo 😉

=====

## Additional resources

- [_Learning ES6_ series](/learning-es6-series/)
- [_Async functions_](http://exploringjs.com/es2016-es2017/ch_async-functions.html)
- [Eventbrite ES6+ coding style guide](https://github.com/eventbrite/javascript/tree/master/es6)
- [Eventbrite React coding style guide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite React ESLint configuration](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)

=====

![Usain Bolt Thumbs Up](../../img/giphy/usain-bolt-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

NOTES:
- So some quick shoutouts before I wrap

/////

![ReactConf 2017 logo](../../img/conf-logos/react-conf-2017-logo.png)
<!-- .element: style="width: 50%; border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Truly an honor & privilege to be here
- Two years ago I didn't even know what React was
- Last year all I wanted to do was attend _React Conf_ (_echoes_)
- And now I'm here sharing with you
- Simply amazing
- Thanks to Tom, Ben, Beth & the rest of the team for the opportunity

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I'm here in part because Eventbrite allowed my Frontend Platform team to make the transition from Backbone to React
- So thanks to the leadership for that trust
- Also thanks for continued support in speaking at conference to share what I know and what we've been doing

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:
- Thanks to you in the audience for staying and not trying to get a jump on the lunch line
- And for those tuning in too
- It's my hope that, the main reason I do this, is so you learn something new to make you a better developer
- Any feedback would be appreciated!

=====

![Jack Sparrow Thanks](../../img/giphy/thanks-jack-sparrow.gif)
<!-- .element: style="width: 80%" -->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////


# Ben Ilegbodu

<br />

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)

<br />

Code examples: [github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)

<br />

Ask me anything! [benmvp.com/ama](/ama/)

NOTES:
- Slides are available on Twitter
- Github repo
- Ask questions on Twitter, via email or AMA!
