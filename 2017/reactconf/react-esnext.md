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
- Many conferences use it for registration
- I work on the Frontend Platform team and right now we're in the midst of a transition from Backbone/Marionette to React
- Python/Django backend, but using a Node daemon to render React components server-side

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
- So in the little time we have together wanted to focus on the features you're most likely to use building apps
- And then throw in some fun at the end

/////

![React tutorial in ES.next screenshot](../../img/react-esnext/react-esnext-app.png)
<!-- .element: style="width: 75%"-->

NOTES:
- The original official React tutorial was written in ES5, presumably to make it easy to develop

/////

## ES5

```js
// App.js
_handleCommentSubmit: function(comment) {
	var comments = this.state.comments;
	var newComment = comment;
	var newComments;

	newComment.id = Date.now();

	newComments = comments.concat([newComment]);
	this.setState({comments: newComments});

	$.ajax({
		url: this.props.url,
		type: 'POST',
		data: comment,
		success: function(resComments) {
			this.setState({comments: resComments});
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
- Here's just one method in the original ES5 code
- Handles submission of the form via AJAX (w/ optimistic updates) in top-level App container component
- Uses `concat` to maintain immutability when adding `newComment`
- Uses jQuery to make AJAX call
- Ugly use of `.bind()` in callbacks

/////

## ES.next

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
		newComments = res.json()
	} catch(ex) {
		console.error(this.props.url, ex)
		newComments = comments
	}

	this.setState({comments: newComments})
}
```

NOTES:
- This version is a little bit shorter
- But leverages lots of new ES goodies
- You may notice the `async` & `await` keywords for async functions
- Those ellipses are the spread operator
- All the `var` statements are replaced with `let` (no time to talk about that)

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
function MyComponent({style, content}) {
    return (
        <div style={style}>{content}</div>
    )
}

// before
function MyComponent(props) {
    return (
        <div style={props.style}>{props.content}</div>
    )
}
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
        <InnerComponent {...props} />
    )
}
```
<!-- .element: class="large" -->

NOTES:
- Similar to object spread, are JSX spread attributes
- It allows you to take an object and make all of its properties attributes on a component
- I tend to avoid it in favor of being explicit about the attributes I'm setting

/////

```js
_handleCommentSubmit(comment) {
	let {comments} = this.state
	let newComment = {...comment, id: Date.now()}
	let newComments = [...comments, newComment]

	// state setting + ajax stuffs
}
```
<!-- .element: class="large" -->

=====

## Recap

0. Destructuring
0. Spread operator
0. Arrow functions
0. Promises
0. Async functions

NOTES:
- So here's what we discussed
- I kind of cheated and only talked about the first 8, but I have helpful links for the others
- Feel free to grab the slides

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
