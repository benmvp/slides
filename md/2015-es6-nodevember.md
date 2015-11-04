# Sugar & Spice and everything nice about ES6

## Ben Ilegbodu

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](http://www.benmvp.com/) | [#nodevember](https://twitter.com/hashtag/nodevember)

NOTES:
- ES6 is the latest version of JavaScript
  - Technically it’s called ECMAScript 2015 because the specification was finalized earlier this year
  - But most people just refer to it still as ES6
- Before we dive in quick show of hands:
  - How many people have heard of ECMAScript 6 before today?
  - How many have played around with it?
  - How many people are using it now in live code?
- Giving a talk to an audience w/ diverse knowledge is a fun challenge
- For the newbies who are afraid to admit they thought ECMAScript was a skin disease, this will be a good ES6 primer for you
- For the intermediate folks, I'm hoping I'll fill in any gaps in knowledge you may have
- For the advanced folks who may know ES6 more than me, feel free to zone out on Slack
  - J/K! Hopefully there'll be a nugget or 3 that you can take away
  - Also, my blog goes into the nitty gritty details for all of the features

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
- Any of you who registered for Nodevember used Eventbrite to buy your ticket
- I work on the team that’s actual rebuilding that page you used to buy your tickets into something beautiful & responsive

=====

# ECMAScript 6

NOTES:
_[2 minutes]_

/////

## Everything you can do in ES6, you can already do in ES5*

NOTES:
- So we can just leave it at that?

/////

# Thanks!

NOTES:
- I could just thank you for coming

/////

# Questions?

## Ben Ilegbodu

[benmvp.com](http://www.benmvp.com/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp/)

NOTES:
- And we can spend the remaining 28 minutes asking questions
- J/K!
- Transpilers work because there's actually a way to write ES6 code in ES5, right?
- But in all seriousness, I think ES6 is JavaScript putting on its big kid pants and having a syntax more comprable to the other popular programming languages
- I do think learning ES6 is worthwhile, otherwise I wouldn't be giving this talk
- While you may not be doing anything particularly new, it will be much easier to do it
- Speaking of transpilers...

=====

# Using ES6 now

Native execution vs. Transpiling

NOTES:
_[3 minutes]_

/////

## Native JavaScript engine support

- Google Chrome - 65%
- Mozilla Firefox - 72%
- Microsoft Edge - 84%  <!-- .element: class="fragment highlight-green" -->
- Safari 9 - 54%
- Opera - 65%
- Webkit - 71%
- Node 5 - 59%
- iOS 9 - 54%

[ECMAScript 6 Compatibility Table](http://kangax.github.io/compat-table/es6/)

NOTES:
- The official ECMAScript 6 spec was finalized in June of this year
- The various JavaScript engines are feverishly implementing ES6 features
- Because ECMAScript 2016 is coming next year!
- There's only a handful of features that all the modern engines support
- And of course that's excluding any of the IE browsers. None of them support ES6
- Only option is transpiling

/////

## Transpiling

### ES6 &#8594; ES3/ES5

- [Traceur](https://github.com/google/traceur-compiler) - 59%
- [Babel](https://babeljs.io/) - 71%   <!-- .element: class="fragment highlight-green" -->
- [TypeScript](http://www.typescriptlang.org/) - 51%

NOTES:
- “Transpilers” let you compile your ES6 code down to ES3/ES5 code for cross-browser compatibility
- ES5 is the JavaScript that is supported in all major browsers. It was released in 2009
- However IE8 doesn’t support ES5. It only supports ES3, which was released in 1999
- There are 3 major ES6 transpilers
  - Traceur
  - Babel
  - TypeScript
- As you can see, Babel has the most support
- I actually prefer it over the others, but they more or less accomplish the same tasks
- So basically what you would do is write your code in ES6
  - Then in your build step when converting SASS to vanilla CSS, minifying and so forth
  - You would also run the transpiler to convert your ES6 code to ES5
- If you visit the websites they have interactive transpilers you can play around with

=====

# ES6 Features

NOTES:
_[5 minutes]_

/////

#### Sugar

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller;margin-bottom:2em">
	\_\_proto\_\_  
	Array APIs  
	Arrow functions  
	Block scoping  
	Classes  
	Default parameters  
	Destructuring  
	Enhanced literals  
	Modules  
	Rest parameters  
	Spread operator  
	String APIs  
	Tagged templates  
	Template literals  
</div>

#### Spice

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller">
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
  Subclassables  
  Symbols  
  Tail calls  
  Typed arrays  
  Unicode  
  WeakMaps  
  WeakSets  
</div>

NOTES:
- Here is the full list of features included in the ES6 specification
- That's 30+ features!
- I've broken them up into 2 categories: sugar & spice
  - Hence the name of the talk
  - SUGAR: New functionality is syntactic sugar. Mostly minor syntax upgrades that make code clearer
  - SPICE: Spicy new functionality like new operators, objects and APIs

/////

## Agenda

Block scoping  
Default parameters  
Destructuring  
Rest parameters  
Spread operator  
`for-of` operator  
Template literals  
Arrow functions  
Enhanced object literals  
String APIs  
Array APIs   

NOTES:
- We'll be covering about ⅓ of the features
- Because of time constraints, we'll focus more on the sugar features
- Really would like to talk about spicier features like promises, iterators and generators
- But not enough time
- So instead going to focus on features you're more likely to leverage right away and which will help you write clearer code
- Buckle up your seat belts, we're going to cover 10+ features in less than 25 minutes

=====

```js
function notify(msg, options) {
  var type, timeout, canClose;

  if (!options)
    options = {};

  type = options.type || 'info';
  timeout = options.timeout;
  canClose = options.close === undefined ? true : options.close;

  // display notification
}

notify('Hi!');
notify('Hi!', {type:'error'});
notify('Hi!', {type:'warn', canClose:false});
```

How can we clean/shorten this code up?

NOTES:
_[6 minutes]_

- Take a look at this code for a bit while I talk
- It's a function that will display a notification message
  - There are a few options on how the message will be displayed
- I'm sure we've all written code like this
- It's not bad but it feels like it could be cleaner.
- Let's try to fix these problems with some ES6 features
- The first issue is the separate declarations from assignments
- Ideally we'd move the declarations to after we default `options`
  - But we need to keep `var` declarations on top to be safe from `var` hoisting
- What we need is for a variable declaration that does __not__ hoist
- There's an ES6 feature for that!

/////

# Block scoping

Replace `var` with `let` & `const`

NOTES:
- In fact there are two: `let` & `const`
- Together they're called Block scoping
- With block scoping we can replace `var` with `let` & `const`

/////

Unified declarations with assignments!

```js
function notify(msg, options) {
  if (!options)
    options = {};

  let type = options.type || 'info';
  let timeout = options.timeout;
  let canClose = options.close === undefined ? true : options.close;
}
notify('Hi!');
notify('Hi!', {type:'error'});
notify('Hi!', {type:'warn', canClose:false});
```

#### Before

```js
function notify(msg, options) {
  var type, timeout, canClose;

  if (!options)
    options = {};

  type = options.type || 'info';
  timeout = options.timeout;
  canClose = options.close === undefined ? true : options.close;
}
```

NOTES:

- Now with `let` we can safely move the declarations down w/ the assignments
- No more worries about variable hoisting
- `const` works similarly except you cannot change the value of a variable declared `const`

- One problem down, a few more to go
- It'd be nice if we didn't have to default `options` in code
- It'd also be nice if it were clear to function callers that `options` does get defaulted
- There's an ES6 feature for that!

=====

# Default parameters

Replace function body code with function header defaults

NOTES:
_[9 minutes]_

- It's called default parameters
- With default parameters we can move our defaulting logic into the function header

/////

Defaulting logic in header!

```js
function notify(msg, options = {}) {
  let type = options.type || 'info';
  let timeout = options.timeout;
  let canClose = options.close === undefined ? true : options.close;

  // display notification
}
notify('Hi!');
notify('Hi!', {type:'error'});
notify('Hi!', {type:'warn', canClose:false});
```

#### Before  

```js
function notify(msg, options) {
  if (!options)
    options = {};

  let type = options.type || 'info';
  let timeout = options.timeout;
  let canClose = options.close === undefined ? true : options.close;

  // display notification
}
```

NOTES:
- `options` is now defaulted to an empty object in the function header
- Nothing earth-shattering. We're used to this from other programming languages
- However...

/////

```js
function getWidth() {
  console.log('getWidth');
  return 7;
}
function drawRect(width = getWidth(), height = width * 2,
  options = {color:'red'}) {
  // draw rectangle
}
```

```
> drawRect()
 getWidth
 7  14  {color:'red'}

> drawRect(17)
 17  34  {color:'red'}

> drawRect(4,11)
 4  11  {color:'red'}

> drawRect(2,1,{color:'blue'})
 2  1  {color:'blue'}
```

NOTES:
- ...take a look at this code and corresponding console output
- Unlike other programming languages that support default values (like C#), a default value in ES6 does not have to be a primitive value
  - It can be an `Object`, expression or even a functional call
- But function calls aren’t executed if the variable doesn’t need to be defaulted
  - As you can see in the sample terminal on the right, `getWidth` isn’t called when a value for `width` is specified
- Another thing to note, is that the default value for `height` is an expression that uses the `width` parameter
  - You’re free to use the value of any parameter that comes before

/////

```js
function notify(msg, options = {}) {
  let type = options.type || 'info';
  let timeout = options.timeout;
  let canClose = options.close === undefined ? true : options.close;

  // display notification
}

notify('Hi!');
notify('Hi!', {type:'error'});
notify('Hi!', {type:'warn', canClose:false});
```

NOTES:
- But back to the code we're trying to fix
- With the multiple assignments we're essentially mapping object property values that may or may not exist to variables
- There's an ES6 feature for that!

=====

# Destructuring

Replace multiple assignments with a single one

NOTES:
_[11 minutes]_

- It's called Destructuring
- With destructuring we can reduce multiple assignments down to one
- Be advised, destructuring is probably the most "out there" syntax addition
- It's ok if you don't understand it at first

/////

Single assignment statement!

```js
function notify(msg, options = {}) {
  let {type='info', timeout, close: canClose=true} = options;

  // display notification
}
```

#### Before

```js
function notify(msg, options = {}) {
  let type = options.type || 'info';
  let timeout = options.timeout;
  let canClose = options.close === undefined ? true : options.close;

  // display notification
}
```

NOTES:
- So now with object destructuring, we can collapse multiple assignments in to one
- But we still have the problem of not knowing what properties in `options` are supported without looking at the function body
- There's an ES6 feature for that!

/////

Named parameters!

```js
function notify(msg, {type='info', timeout, close:canClose=true} = {}){
  // display notification
}

notify('Hi!');
notify('Hi!', {type:'error'});
notify('Hi!', {type:'warn', canClose:false});
```

#### Before

```js
function notify(msg, options = {}) {
  let {type='info', timeout, close: canClose=true} = options;

  // display notification
}
```

NOTES:
- It's called object destructuring again! lol
- Object destructuring can also be done in function headers to simulate named parameters
- Now, not only is `options` defaulted in the function header, but it's immediately destructured into the variables the function cares about
- And now anyone looking at the function header can tell what properties matter

/////

### After

```js
function notify(msg, {type='info', timeout, close:canClose=true} = {}){
  // display notification
}
```

### Original

```js
function notify(msg, options) {
  var type, timeout, canClose;

  if (!options)
    options = {};

  type = options.type || 'info';
  timeout = options.timeout;
  canClose = options.close === undefined ? true : options.close;

  // display notification
}
```

NOTES:
- All of ur code has moved into the function header!
- How many people find destructuring to make the code less readable?
  - You're not alone!
  - I feel the same way too!
  - Of all the ES6 syntactic sugar features, destructuring seems the least readable to me
  - But I hope that as we all get familiar with the syntax, it'll become more readable
- Let's go ahead and take a look at array destructuring while we're here...

/////

```js
let [a, b, c] = [8, true, 11];
    // a=8, b=true, c=11
let [a, b, c=9] = ['no'];
    // a='no', b=undefined, c=9
let [, yr, mo, day] = /^(\d\d\d\d)-(\d\d)-(\d\d)$/.exec('2015-11-14');
    // yr='2015', mo='11', day='14'
```

```js
function hi(a, [b, , d]) {
    // a='hello', b=1, d=3
}
hi('hello', [1, 2, 3]);
```

### Array destructuring

NOTES:
- Array destructuring works much the same way as object destructuring
- The main difference is:
  - Array destructuring uses an array literal pattern on the left hand side of the assignment
  - And the order in the pattern determines the assignment matching
- The first example maps all the entries into variables
- Second example shows how defaulting works with array destructuring
- Third example is a real-world use case with regular expression matches
  - Don't need to maintain the intermediate array
- The final example shows how you can destructure an array parameter similar to what we did with object destructuring for named parameters

- Now let's move on to a new problem...

=====

# Quick Hits

NOTES:
- Let's quickly look at some other ES6 features
- We're going to move pretty quickly through the rest of these

===== <!-- .slide: data-transition="fade" -->

```js
function join(separator) {
  var values = [];

  // arguments is not an array, just "array-like"
  for (var i = 1; i < arguments.length; i++) {
      values.push(arguments[i]);
  }

  return values.join(separator);
}

// output: tic-tac-toe
join('-', 'tic', 'tac', 'toe');
```

Parameters list is unclear

NOTES:
_[15 minutes]_

- We have here a `join` method that takes a separator string followed by an unlimitted number of parameters to join
- The fact that `join` takes more than one parameter is unclear let alone that it accepts an arbitrary number of them
- Because `join` uses the `separator` parameter the implementation has to start at index `1` of `arguments`
- And even if it could start at 0, arguments is only array-like so it doesn't have the `join` method that arrays have
- What we need is an easy way to get an array of the parameters after `separator`
- And guess what? There's an ES6 feature for that

/////

# Rest parameters

Replace `arguments` with an array

/////

Clearer function signature!

```js
function join(separator, ...values) {
  return values.join(separator);
}

// output: tic-tac-toe
join('-', 'tic', 'tac', 'toe');
```

#### Before

```js
function join(separator) {
  var values = [];

  // arguments is not an array, just "array-like"
  for (var i = 1; i < arguments.length; i++) {
      values.push(arguments[i]);
  }

  return values.join(separator);
}
```

NOTES:
- That's it!
- The three dots, called the rest operator, before the parameter make it a rest parameter
  - The rest parameter is an Array containing the rest of the parameters
  - Hence the name!
- Because `values` is a true array in the example, we can call join on it
- It’s also much clearer to see that `join()` takes an infinite number of parameters
- Rest parameter should pretty much replace all uses of the `arguments` keyword!

/////

Destructuring + rest parameters!

```js
let list = [9, 8, 7, 6, 5];
let [first, ...rest] = list;

// output: 9  [8, 7, 6, 5]
console.log(first, rest);
```

#### Old way
```js
var list = [9, 8, 7, 6, 5],
    first = list[0],
    rest = list.slice(1);

// output: 9  [8, 7, 6, 5]
console.log(first, rest);
```

NOTES:
- One last thing with rest parameters
- They can be combined with array destructuring to replace `slice`

- Now, let's take a look at yet another problem

=====

```js
var maxValueNormal = Math.max(33, 2, 9),
    arrayOfValues = [33, 2, 9],
    maxValueFromArray = Math.max.apply(null, arrayOfValues);

// output: 33  33
console.log(maxValueNormal, maxValueFromArray);
```

`Math.max.apply`???

NOTES:
_[17 minutes]_

- `Math.max` accepts an arbitrary number of numeric parameters and returns the maximum one
- If you want to get the maximum value of an array of numbers, you have to call `Math.max.apply`
- `apply` converts the array of values into a sequence of parameters
- But it's kind of esoteric
  - Plus you have to specify `null` as the context
- Maybe there's an ES6 feature for this?

/////

# Spread operator

Replace `apply` with the spread operator

/////

No more `apply`!

```js
let arrayOfValues = [33, 2, 9];
let maxValueFromArray = Math.max(...arrayOfValues);

// output: 33  33
console.log(maxValueFromArray);
```

#### Before

```js
var arrayOfValues = [33, 2, 9],
    maxValueFromArray = Math.max.apply(null, arrayOfValues);

// output: 33
console.log(maxValueFromArray);
```

NOTES:
- Instead of calling `apply` we can use the spread operator
- It's 3 dots preceeding a parameter in a function call
- The spread operator _spreads_ out the array into individual parameters

/////

No more `concat`! 

```js
let start = ['do', 're'];
let middle = ['mi', 'fa', 'so'];
let end = ['la', 'ti'];
let scaleFromLiteral = [...start, ...middle, ...end];

// output: ['do', 're', 'mi', 'fa', 'so', 'la', 'ti']
console.log(scaleFromLiteral);
```

#### Old way

```js
let start = ['do', 're'];
let middle = ['mi', 'fa', 'so'];
let end = ['la', 'ti'];
let scaleFromConcat = start.concat(middle).concat(end);

// output: ['do', 're', 'mi', 'fa', 'so', 'la', 'ti']
console.log(scaleFromConcat);
```


NOTES:
- When we spread multiple arrays into an array literal we're constructing a new array with all of those values
- Therefore using the spread operator within an array literal can replace using `concat`

- All this talk of arrays reminds me of another problem...

=====

ES3: `for` loop

```js
var list = [8, 3, 11, 9, 6];

for (var i = 0; i < list.length; i++) {
  console.log(list[i]);
}
```

NOTES:
_[20 minutes]_

- Over the last 2 decades of JavaScript, developers have iterated over array elements using the basic `for` loop
- You have to keep track of the counter variable `i` AND control when the loop ends

/////

`for-in` does not work with arrays!

```js
var list = [8, 3, 11, 9, 6];

// DON'T DO THIS!!!!
for (var i in list) {
  console.log(list[i]);
}
```

NOTES:
- You may be tempted to use the `for-in` loop to iterate over an array, but it has problems
- `for-in` can iterate in an arbitrary order
- The values on the iteration variable are actually strings not numbers!
  - So adding numbers to them results in concatenation not addition
- Any enumerable keys on the array will also be iterated over
- `for-in` was designed to iterate over regular objects with string keys only
  - Not arrays

/////

ES5: `forEach` method

```js
var list = [8, 3, 11, 9, 6];

list.forEach(function(value, i)) {
  console.log(value);
};
```

What about `break`, `continue` & `return`?

<!-- .element: class="fragment" data-fragment-index="0" -->

NOTES:
- ES5 introduced the `forEach` method
- It’s a more succinct syntax.
  - You no longer need the counter variable and it will read all values until the end
- But what if you want to `break` out of the loop or `continue` to the next value?
  - That would be a syntax error because there’s no loop control
- What if you want to `return`?
  - You’d be returning from the `forEach` callback function, not stopping iteration
- So basically we'd like to combine the benefits of `for` and `forEach` together
- There's an ES6 feaure for that!

/////

# `for-of`

Replace `for` and `forEach` with `for-of`

/////

ES6: `for-of`

```js
let list = [8, 3, 11, 9, 6];

for (let value of list) {
  console.log(value);
}
```

#### Before

```js
var list = [8, 3, 11, 9, 6];

for (var i = 0; i < list.length; i++) {
  console.log(list[i]);
}
```

NOTES:
- It’s still succinct because it doesn’t need a counter variable and reads to the end just like `forEach`
- It also supports `break`, `continue` and `return` unlike `forEach`
- `for-of` is for arrays and `for-in` is for objects
- Now JavaScript has a similar loop control structure that mirrors what you’d see in C#, Python or Java

=====

```js
var first = 'Ben',
	last = 'Ilegbodu';

// output: He said, "It's your fault!
console.log('He said, "It\'s your fault!"');

// output: Name: Ilegbodu, 31
console.log('Name: ' + last + ', ' + (15 + 16));
    
console.log('This is multi-line text, so\n' +
    'that newline characters are not\n' +
    'needed. Whitespace is respected\n');
```

Good ol' string concatenation

NOTES:
_[22 minutes]_

- We usually don’t build string in JS anymore
- But we do sometimes have to provide messages to the user that have dynamic data

To make this easier, ES6 introduces...

/////

# Template literals

Replace string concatentation with template literals

NOTES:
- With template literals, we can stop using string concatentation

/////

String interpolation + multi-line!

```js
let first = 'Ben', last = `Ilegbodu`;

// output: He said, "It's your fault!
console.log(`He said, "It's your fault!"`);

// output: Name: Ilegbodu, 31
console.log(`Name: ${last}, ${15 + 16}`);

console.log(`This is multi-line text, so
    that newline characters are not
    needed. Whitespace is respected
`);
```

#### Before

```js
var first = 'Ben', last = 'Ilegbodu';

console.log('He said, "It\'s your fault!"');

console.log('Name: ' + last + ', ' + (15 + 16));
    
console.log('This is multi-line text, so\n' +
    'that newline characters are not\n' +
    'needed. Whitespace is respected\n');
```

NOTES:
- ES6 template literals are a brand new type of string literal, delimited by backticks (`)
  - That’s not a typo!
  - That character to the left of the 1 key
  - Because of backticks, you no longer need to escape single or double quotes
- Template literals natively support string interpolation (token substitution)
  - Any JavaScript expression can be substituted inside ${ }
  - It will ultimately be coerced into a string
- Multi-line strings are now supported as well
  - Any whitespace you put will be in the string, including tabs and newlines
- One of the few features supported by all modern browsers
- We’ll see more examples of template literals as we look at other features

===== <!-- .slide: data-transition="fade" -->

```js
'use strict';

MyObj.prototype.update = function() {
	$.get(this._url).done(function(responseData) {
		this._data = responseData;
	});
};
```

Where's the bug?

NOTES:
_[24 minutes]_

- Can anyone spot the mistake in this code?
- We're passing a callback to `done` of the `get` ajax request

///// <!-- .slide: data-transition="fade" -->

```js
'use strict';

MyObj.prototype.update = function() {
	$.get(this._url).done(function(responseData) {
		// `this` is undefined!
		this._data = responseData;
	});
};
```

Undefined `this`!

NOTES:
- `this` is `undefined` in the callback function in strict mode
- `this` is the global scope (window) in loose mode
- _[Water break]_

/////

```js
MyObj.prototype.update = function() {
	var self = this; // store reference to `this`

	$.get(self._url).done(function(responseData) {
		// `self` is available in scope
		self._data = responseData;
	});
};
```

ES3 fix

NOTES:
- In ES3, we solved this by storing a reference to `this` in a variable so that it’s available in the scope of the anonymous function
- Works but pretty much every method has to assign `self` variable

/////

```js
MyObj.prototype.update = function() {
	$.get(this._url).done((function(responseData) {
		this._data = responseData;
	}).bind(this)); // pass in proper `this` context
};
```

ES5 fix

NOTES:
- `bind()` was introduced in ES5 and it creates a new function, passing the specified `this`
- Underscore and other libraries have a bind method so it can work with ES3
- Works, but messy syntax

/////

# Arrow functions

Replace anonymous functions with arrow functions

NOTES:
- With arrow functions we can stop using anonymous functions

/////

Arrow functions works how you would expect!

```js
MyObj.prototype.update = function() {
	$.get(this._url).done(responseData => {
		// `this` uses "lexical scoping"
		this._data = responseData;
	});
};
```

#### Before

```js
'use strict';

MyObj.prototype.update = function() {
  $.get(this._url).done(function(responseData) {
    // `this` is undefined!
    this._data = responseData;
  });
};
```


NOTES:
- Arrow functions in ES6 solve this problem
- Arrow functions use what’s called “lexical scoping” for `this`
  - It's implicitly “inherited” from the enclosing scope, which in our case would be the class method
  - Essentially arrow functions work how you would expect it to
- You’ll find that arrow functions come in handy most when used as a callback function. 
  - The various higher-order functional programming array methods that were introduced with ECMAScript 5 (like `map`, `forEach`, `reduce`, etc.) work well with arrow functions.
  - Arrow functions can also be used as callback functions for event handlers (like `click`, `keydown`, etc),

=====

```js
var MyView = Backbone.ItemView.extend({
    serializeData: function() {
        var quantity = this._calculateQuantity(),
            canChange = this._canChangeQuantity();
        return {
            quantity: quantity,
            canChange: canChange
        };
    },
    _calculateQuantity: function() { return 7; },
    _canChangeQuantity: function() { return true; }
});
```

NOTES:
_[26 minutes]_

- Take a look at this code
- It's extending a `Backbone.ItemView` by passing additional methods to be defined on the new class in an object literal
- There are 4 methods. The methods themselves aren't all that important
- Now take a look at the `serializeData` method.
  - It returns an object literal where the keys and variable names match
- There's actually nothing really wrong with this code, but...
- There's still an ES6 feature for that! :)

/////

# Enhanced object literals

Write less code in object literals

/////

Object literal shorthand!

```js
const MyView = Backbone.View.extend({
    serializeData() {
        let quantity = this._calculateQuantity(),
            canChange = this._canChangeQuantity();

        // {quantity: 7, canChange: true}
        return {quantity, canChange};
    },
    _calculateQuantity() { return 7; },
    _canChangeQuantity() { return true; }
});
```

#### Before

```js
var MyView = Backbone.ItemView.extend({
    serializeData: function() {
        var quantity = this._calculateQuantity(),
            canChange = this._canChangeQuantity();

        return {quantity: quantity, canChange: canChange};
    },
    _calculateQuantity: function() { return 7; },
    _canChangeQuantity: function() { return true; }
});
```

NOTES:
- Those with a keen eye will notice that the methods look a little different
  - They are missing the colon and `function` keyword
  - This is method shorthand syntax with enhanced object literals
  - Whenever you're adding a function to an object literal you can omit `:function`
  - Just the name and the parameters are needed
- You might also notice the returned object literal in `serializeData`
  - It looks like we're creating an object literal with keys but no values
  - What the interpreter is doing is looking in the scope for a variable with the same name
  - If it finds it, its variable becomes the value of the key
  - If it doesn't find one, it's a ReferenceError
  - This is property value shorthand syntax with enhanced object literals
- Simple enough, right?

/////

```js
function predictChampion(league, year) {
    // output: league WNBA year 2016
    console.log('league', league, 'year', year);

    // output: league=WNBA  year=2016
    console.log(`league=${league}`, `year=${year}`);

    // output: {league: 'WNBA', year: 2016}
    console.log({league, year});
}

predictChampion('WNBA', 2016);
```

Pro tip!

NOTES:
- Quick tip!
- I don't really use the JavaScript debugger much
- I prefer to do `console.log` debugging for an array of reasons
- Sometimes when I want to log the value of multiple variables at the same time but also include a label
- Here are 3 different ways it can be accomplished
  - The first way is the old-school way
  - The second way leverages template literals
  - But my favorite is the 3rd way that uses property value shorthand for object literals
  - Super short to write and is basically just wrapping in `{}`

=====

## String API

`str.startsWith`

`str.endsWith`

`str.includes`

`str.repeat`

`String.raw`

NOTES:
_[28 minutes]_

- Just want to alert you to some new methods introduce with ES6 for `String`

=====

## Array API

`Array.from`

`Array.of`

`arr.find`

`arr.findIndex`

`arr.copyWithin`

`arr.fill`

NOTES:
- Also some useful methods for `Array` too

=====

## Iterators & Generators

Enable complex asynchronous programming with `function*` and `yield`

`async` / `await`

<!-- .element: class="fragment" data-fragment-index="0" -->

NOTES:
_[28.5 minutes]_

- I really want to quickly mention iterators & generators
- They are far too complex to even try to explain in the remaining time
- They do enable complex asynchronous programming
- Generators will serve as foundation for `async` & `await` features coming with ES2016

/////

![Nicholas Young](img/nicholas-young-callbackless-asynchrony.jpg)

## Nicholas Young

Callback-less Asynchrony: ES6, Generators, and the next wave of JavaScript development

NOTES:
- But one of my fellow speakers Nicholas Young will be talking all about generators right after me!
- So don't leave this room!

=====

## Review

Block scoping  
Default parameters  
Destructuring  
Rest parameters  
Spread operator  
`for-of` operator  
Template literals  
Arrow functions  
Enhanced object literals  
String APIs  
Array APIs   

NOTES:
_[29 minutes]_

- As a reminder, here's what we covered to make our code clearer or shorter

=====

## Additional Resources

* [*Learning ES6*](http://www.benmvp.com/2015/08/the-learning-es6-series.html) by [Ben Ilegbodu](https://twitter.com/benmvp)
* [ES6 Katas](http://es6katas.org/) by [Wolfram Kriesing](https://twitter.com/wolframkriesing)
* [*Exploring ES6*](http://exploringjs.com/es6/) by [Axel Rauschmayer](https://twitter.com/rauschma)
* [*Understanding ECMAScript 6*](https://leanpub.com/understandinges6/) by [Nicholas C. Zakas](https://twitter.com/slicknet)
* [*ES6 in Depth*](https://hacks.mozilla.org/category/es6-in-depth/) by [Jason Orendorff](https://twitter.com/jorendorff)
* [*ES6 in Depth*](http://ponyfoo.com/articles/tagged/es6-in-depth) by [Nicolas Bevacqua](https://twitter.com/nzgb)

NOTES:
_[29.5 minutes]_

- If you didn't catch all that I covered, you can check out my blog where I go into detail about every feature I covered
- Other great books & blogs about ES6 too!

=====

# Shoutouts

/////

![Nodevember flyer](img/nodevember.png)

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
[github/benmvp](https://github.com/benmvp/)