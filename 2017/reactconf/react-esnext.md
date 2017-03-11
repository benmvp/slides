# React + ES.next = ♥

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#reactconf](https://twitter.com/hashtag/reactconf)    

<br />

March 13, 2017  

NOTES:
- My name is Ben Ilegbodu
- Super excited to talk about my two favorite things
- React and what I'm calling ES.next
- And how they go so well together
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

0. Destructuring
0. Spread operator
0. Arrow functions
0. Promises
0. Async functions

NOTES:
- Here's the agenda
- One of the things I like about React is that it's basically JavaScript, outside JSX & lifecycle things
- So in the little time we have together wanted to focus on these features
- Reason picking these 5 features is because they'll help write clear & concise code
- They target a wide range of audiences
- Will see other features along the way that I will explain quickly

/////

![React tutorial in ES.next screenshot](../../img/react-esnext/react-esnext-app.png)
<!-- .element: style="width: 75%"-->

NOTES:
- The original official React tutorial was written in ES5, presumably to make it easy to develop

/////

Let's get to work!

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
			this.setState({comments: comments});
			console.error(this.props.url, status, err.toString());
		}.bind(this)
	});
}
```
<!-- .element: class="small" -->

NOTES:
- Want to just focus on this one method in top-level App container component
- Handles submission of the form via AJAX (w/ optimistic updates)
- Because of time constraints already has some ES6: class syntax, `let`, etc.
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
- Converted the `let` declarations to `var`, removed those unnecessary semicolons
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

	// state setting + ajax stuffs
}
```
<!-- .element: class="large" -->

NOTES:
- Here's more of our code, annotated a bit
- Adding `id` property to `comment` to create `newComment` (except we're mutating)
- Then appending `newComment` to `comments` via `concat` to maintain immutability

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
let array = new Array(2, 3, 4)

// shorthand
let array = [2, 3, 4]
```
<!-- .element: class="large" -->

------

Spreading into an array

```js
// [1, 2, 3, 4, 5]
let verbose = new Array(1, ...array, 5)

// [1, 2, 3, 4, 5]
let shorthand = [1, ...array, 5]
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
function WrapperComponent(props) {
    return (
        <InnerComponent
			{...props}
			style="light"
			size="large"
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
}
```
<!-- .element: class="large" -->

NOTES:
- So now these lines make a bit more sense knowing how the spread operator works

===== <!-- .slide: data-transition="fade" -->

Where's the bug?

```js
_handleCommentSubmit(comment) {
	// initializations

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resJson) {

			this.setState({comments: resJson})
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
		success: function(resJson) {
			// `this` is undefined!
			this.setState({comments: resJson})
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
		success: function(resJson) {
			// `self` is available in scope
            self.setState({comments: resJson})
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
_handleCommentSubmit: function(comment) {
	// initializations

    $.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resJson) {
            this.setState({comments: resJson})
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
		error: function(xhr, status, err) => {
			this.setState({comments: comments});
			console.error(this.props.url, status, err.toString())
		}
	});
}
```
<!-- .element: class="large" -->

NOTES:
- So this is what our AJAX call looks like
- It's fine, but I don't like using jQuery, especially just for ajax
- Including it could lead to proper React development, relying too much on refs
- In addition, callbacks are so 2013
- There's gotta be something better!

/////

# Promises

Replace callbacks with promises

<br />
<br />

[_Learning ES6: Promises_](http://www.benmvp.com/learning-es6-promises/)

NOTES:
- With promises we can stop using callback functions
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
      this.setState({comments});
      console.error(this.props.url, ex);
    });
}
```
<!-- .element: class="large" -->

NOTES:
- We can replace jquery ajax with Fetch browser API which gives us `window.fetch`
- Instead of taking callback functions, it's promised-based so it returns a promise
- Pretty much all future asynchronous APIs will be promised-based
- Because promises are more flexible than callbacks
- How so...?

/////

###### Promises

Passing promises + chaining reactions

```js
const fetchJson = (path) => (
  fetch(`${DOMAIN}${path}`)
    .then((res) => res.json())
)
```
<!-- .element: class="large" -->

```js
const fetchComments = () => fetchJson('/comments')
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

Converting callbacks to Promises

```js
const wait = (delay = 0) => (
    new Promise((resolve) => {
        setTimeout(resolve, delay)
    })
)

wait(3000)
  .then(() => getUniqueCommentAuthors())
```
<!-- .element: class="large" -->

Sleep function... in JavaScript!

/////

###### Promises

Converting callbacks to Promises

```js
const readFile = (filePath) => (
	new Promise((resolve, reject) => {
		fs.readFile(filePath, (err, data) => {
			if (err) reject(err)
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

Simultaneous async requests

```js
Promise.all([
	fetchComments(),
	fetchPosts(),
	fetchUsers()
])
  .then(([comments, posts, users]) => {
	  console.log(comments)
	  console.log(posts)
	  console.log(users)
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
      this.setState({comments});
      console.error(this.props.url, ex);
    });
}
```
<!-- .element: class="large" -->

NOTES:
- So hopefully I've convinced you in that short time that Promises are better than callback-style programming
- Because you can chain promises, instead of having callback-hell there's just a flat level of chains
- However, you're still passing anonymous functions
- Asynchronous programming still makes you write code control flow differently
- Until...

=====

[![react-esnext Gitub repo](../../img/react-esnext/repo.png)](https://github.com/benmvp/react-esnext)

[github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)

NOTES:
- And to be even more helpful I crated a repo where I take the ES5 React tutorial and go step-by-step converting it to ES2015+
- Feel free to star the repo 😉

=====

## Additional resources

- [React official tutorial](https://facebook.github.io/react/tutorial/tutorial.html)
- [_Learning ES6_ series](/learning-es6-series/)
- [_Async functions_](http://exploringjs.com/es2016-es2017/ch_async-functions.html)
- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
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
-

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:
- It's my hope that, the main reason I do this, is so you learn something new to make you a better developer
- Any feedback would be appreciated!

=====

![Jack Sparrow Thanks](../../img/giphy/thanks-jack-sparrow.gif)
<!-- .element: style="width: 80%" -->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)

<br />

Code examples: [github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)

<br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- Slides are available on Twitter
- Github repo
- Ask questions on Twitter, via email or AMA!
