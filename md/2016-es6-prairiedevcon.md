# Sweet ES6

<br />

## Ben Ilegbodu

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#PrairieDevCon](https://twitter.com/hashtag/prairedevcon)  
<br />
April 12, 2016  

NOTES:
- Posted link to slides on twitter if you want to follow along
- This is Sweet ECMAScript 6 aka ES6, the latest version of JavaScript
- Technically it's called ES2015, because the spec was released last year in 2015

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

![Eventbrite logo](img/eventbrite-logo.png)

NOTES:
- Currently a Senior UI Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- I work on the Frontend Platform team and right now we're in the midst of a transition from Backbone/Marionette to React
- Python/Django backend, but using a Node daemon to render React components server-side

/////

<!-- .slide: data-background="url(img/giphy/james-harden-pot-cook.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I also absolutely love basketball - both playing & watching
- But you didn't come to hear about me. At least I hope not
- You came to here about...

=====

# ECMAScript 6

<br />
<br />

[benmvp.com/learning-es6-series](http://www.benmvp.com/learning-es6-series)

NOTES:
_[2 minutes]_

- So let's talk about it
- Show of hands:
  1. Heard of ECMAScript 6 before today?
  1. Played around with it?
  1. Using in live code?
- Got a pretty diverse audience
- Newbies: nice intro
- Experienced: nugget or 2
- Blog has details

/////

#### Sugar <!-- .element: style="color:blue;" -->  

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller;margin-bottom:2em">
  <code>\_\_proto\_\_</code>  
  Arrow functions  
  Classes  
  Default parameters  
  Destructuring  
  Object literal shorthand  
  Modules  
  Rest parameters  
  Spread operator  
  Tagged templates  
  Template literals  
</div>

#### Spice <!-- .element: style="color:red;" -->  

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
- 2 categories: sugar & spice
  - SUGAR: Syntactic sugar. Mostly minor syntax upgrades that make code clearer
  - SPICE: Spicy new functionality like new operators, objects and APIs
- But before we talking about the features let's start with a history lesson

=====

# ECMAScript History

Looking back on two decades of JavaScript

<br />
<br />

[benmvp.com/learning-es6-history-of-ecmascript/](http://www.benmvp.com/learning-es6-history-of-ecmascript/)

NOTES:
_[4 minutes]_

/////

###### History

## May 1995

<img src="img/es6/brendan-eich.jpg" style="height: 450px" />

### Brendan Eich

<br />

Created JavaScript **_in 10 days_**

##### Mocha (May) ➜ LiveScript (Sep) ➜ JavaScript (Dec)

NOTES:

- JavaScript was created in May 1995 by Brendan Eich while at Netscape
- He reportedly developed it in 10 days
  - I find that hard to believe
  - But when you look at some of JavaScript's quirks maybe he really did?
  - Turns out he did a lot of planning before the 10 days of **implementation**
- Originally named Mocha (chosen by Netscape founder Marc Andressen)
- In September 1995, a beta version of Netscape Navigator 2.0 & renamed to LiveScript
- In December 1995, Netscape renamed it to JavaScript (with NN 2.0b3) because Java was popular at the time

/////

###### History

## November 1996

<br />

TC39 started work on ECMA-262 (ECMAScript)

NOTES:
_[5 minutes]_

- August 1996, Microsoft cloned JavaScript in IE 3.0 and called it JScript
- A standard was needed
- Netscape took JavaScript to Ecma standards organization to maintain language spec
- The Ecma Technical Committee 39 (aka TC39) began work on ECMA-262 (aka ECMAScript) in November 1996
- ECMAScript is the name of the official standard
- JavaScript is the most well-known implementation
- There's also ActionScript (Macromedia/Adobe) and JScript (Microsoft)
- But pretty much ECMAScript == JavaScript

/////

###### History

## Jun 1997 — **ES1**
## Jun 1998 — **ES2**
## Dec 1999 — **ES3**  <!-- .element: class="fragment highlight-green" data-fragment-index="0" -->  
## Dec 2009 — **ES5**  <!-- .element: class="fragment highlight-blue" data-fragment-index="1" -->  
## Jun 2015 — **ES6**  <!-- .element: class="fragment highlight-red" data-fragment-index="2" -->  
## Jun 2016 — **ES7**

NOTES:
_[6 minutes]_

- First version of ECMAScript spec was released in `June 1997`
- ECMAScript 2 was released a year later with only minor changes
- 18 months later ECMAScript 3 (**[NEXT]**) was released
  - Included features like regular expressions, try/catch & numeric formatting
  - ES3 is the version of JavaScript in IE8
- ES5 was released in `December 2009` (**[NEXT]**)
  - It's in all of our modern browsers
  - Features: strict mode, JSON, `.map()/.forEach()`, `O.keys()`, property accessors
  - 10 year difference was rift which caused ES4 to be lost spec
- ES6, what we're here for, released in `June 2015` (**[NEXT]**)
  - Another big gap because spec is so big
  - ES Harmony ➜ ES.next ➜ ES6 ➜ ES2015
  - Yearly cadence
- ES7 will be released in `June 2016`
  - Only will have 2 features

=====

# ES6 Features

<br />
<br />

[benmvp.com/learning-es6-goals-features-ecmascript-6/](http://www.benmvp.com/learning-es6-goals-features-ecmascript-6/)

NOTES:
_[8 minutes]_

/////

## Agenda

1. Block scoping <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->  
1. Default parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Destructuring <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Rest parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Spread operator <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. `for-of` <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->
1. Arrow functions <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Template literals <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Classes <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Object literal shorthand <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. String APIs <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->
1. Array APIs  <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->

NOTES:
- Here's what we'll be covering
- Focusing on the syntactic sugar features **[NEXT]** because they are the ones your more likely to use immediately to make your code clearer
- Spicy features -> whole talk about generators
- We're going to cover these 10 features in less than 40 minutes
  - Buckle your seat belts!

=====

How can we clean/shorten this code up?

```js
function log(msg, opts) {
  var type, delay, useColor;

  if (!opts)
    opts = {};

  type = opts.type || 'info';
  delay = opts.delay;
  useColor = opts.color === undefined ? true : opts.color;

  // log message
}

log('Hi!');
log('Hi!', {type: 'error'});
log('Hi!', {type: 'warn', color: false});
```
<!-- .element: class="large" -->

NOTES:
_[3 minutes]_

- Take a look at this code for a bit while I talk
- It's a function that will log a message
  - There are a few options on how the message will be logged
- I'm sure we've all written code like this
- It's not bad but it feels like it could be cleaner.
- Let's try to fix these problems with some ES6 features
- The first issue is the separate declarations from assignments
- Ideally we'd move the declarations to after we default `options`
  - But we need to keep `var` declarations on top to be safe from `var` hoisting
  - The JS interpreter essentially moves all `var` declarations to the top of the function
- What we need is for a variable declaration that does __not__ hoist
- There's an ES6 feature for that!

/////

# Block scoping

Replace `var` with `let` & `const`

<br />
<br />

[benmvp.com/learning-es6-block-level-scoping-let-const/](http://www.benmvp.com/learning-es6-block-level-scoping-let-const/)

NOTES:
- In fact there are two: `let` & `const`
- Together they're called Block scoping
- With block scoping we can replace `var` with `let` & `const`

/////

Unified declarations with assignments!

```js
function log(msg, opts) {
  if (!options)
    options = {};

  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;
}
```
<!-- .element: class="large" -->

-----

#### Before

```js
function log(msg, opts) {
  var type, delay, useColor;

  if (!opts)
    opts = {};

  type = opts.type || 'info';
  delay = opts.delay;
  useColor = opts.color === undefined ? true : opts.color;
}
```

NOTES:

- Now with `let` we can safely move the declarations down w/ the assignments
- No more worries about variable hoisting

/////

<!-- .slide: data-background="url(img/giphy/unimpressed-squidward.gif) no-repeat center" data-background-size="contain"-->

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

Use `Object.freeze()` for objects!

<!-- .element: class="fragment" -->

Use [Immutable.js](https://facebook.github.io/immutable-js/)!

<!-- .element: class="fragment" -->

NOTES:
- `const` is pretty straightforward
- Can’t change a value that is declared `const`
- Must assign an initial value if declared `const`
- One interesting thing is that if an object is `const` its properties are not
  - You can still assign to them
  - Need to use `Object.freeze`
  - Or Immutable.js from Facebook

/////

```js
function log(msg, opts) {
  if (!options)
    options = {};

  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;

  // log message
}

log('Hi!');
log('Hi!', {type: 'error'});
log('Hi!', {type: 'warn', color: false});
```
<!-- .element: class="large" -->

NOTES:
- Back to our code...
- One problem down, a few more to go
- It'd be nice if we didn't have to default `opts` in code
- It'd also be nice if it were clear to function callers that `opts` does get defaulted
- There's an ES6 feature for that!

=====

# Default parameters

Replace function body code with function header defaults

<br />
<br />

[benmvp.com/learning-es6-parameter-handling/](http://www.benmvp.com/learning-es6-parameter-handling/#default-parameters)

NOTES:
_[4 minutes]_

- It's called default parameters
- With default parameters we can move our defaulting logic into the function header

/////

Defaulting logic in header!

```js
function log(msg, opts = {}) {
  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;
}
```
<!-- .element: class="large" -->

-----

#### Before  

```js
function log(msg, opts) {
  if (!options)
    options = {};

  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;
}
```
<!-- .element: class="large" -->

NOTES:
_[5 minutes]_

- `opts` is now defaulted to an empty object in the function header
- Nothing earth-shattering. We're used to this from other programming languages
- However...

/////

```js
function getWidth() {
  console.log('getWidth');
  return 7;
}
function makeRect(w=getWidth(), h=w*2, opts={color:'red'}) {
  console.log(w, h, opts);

  // create rectangle
}
```
<!-- .element: class="large" -->

```
> makeRect()
getWidth
7  14  {color:'red'}

> makeRect(17)
17  34  {color:'red'}

> makeRect(4, 11)
4  11  {color:'red'}

> makeRect(2, 1, {color:'blue'})
2  1  {color:'blue'}
```

NOTES:
_[6 minutes]_

- ...take a look at this code and corresponding console output
- Unlike other programming languages that support default values (like C#), a default value in ES6 does not have to be a primitive value
  - It can be an `Object`, expression or even a functional call
- But function calls aren’t executed if the variable doesn’t need to be defaulted
  - As you can see in the sample terminal on the right, `getWidth` isn’t called when a value for `width` is specified
- Another thing to note, is that the default value for `height` is an expression that uses the `width` parameter
  - You’re free to use the value of any parameter that comes before
- Lastly, you can have non defaults after default parameters

/////

```js
function log(msg, opts = {}) {
  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;

  // log message
}

log('Hi!');
log('Hi!', {type: 'error'});
log('Hi!', {type: 'warn', color: false});
```
<!-- .element: class="large" -->

NOTES:

- But back to the code we're trying to fix
- With the multiple assignments we're essentially mapping object property values that may or may not exist to variables
- There's an ES6 feature for that!

=====

# Destructuring

Replace multiple assignments with a single one

<br />
<br />

[benmvp.com/learning-es6-destructuring/](http://www.benmvp.com/learning-es6-destructuring/)

NOTES:
_[7 minutes]_

- It's called Destructuring
- With destructuring we can reduce multiple assignments down to one
- Be advised, destructuring is probably the most "out there" syntax addition
- It's ok if you don't understand it at first

/////

<!-- .slide: data-background="url(img/giphy/i-hate-you-brad-pitt.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I'm afraid that after we cover destructuring, you'll feel like this...
- But stick with me...

/////

Single assignment statement!

```js
function log(msg, opts = {}) {
  let {type='info', delay, color: useColor=true} = opts;

  // log message
}
```
<!-- .element: class="large" -->

<br />

-----

#### Before

```js
function log(msg, opts = {}) {
  let type = opts.type || 'info';
  let delay = opts.delay;
  let useColor = opts.color === undefined ? true : opts.color;

  // log message
}
```
<!-- .element: class="large" -->

NOTES:
_[8 minutes]_

- So now with object destructuring, we can collapse multiple assignments in to one
- Uses an object literal pattern to map properties of an object into multiple variables
- Doing 3 things here!
  1. Declaring 3 variables
  2. Assigning variables from object properties
  3. Defaulting when `undefined`
- But we still have the problem of not knowing what properties in `opts` are supported without looking at the function body
- There's an ES6 feature for that!

/////

Named parameters!

```js
function log(msg, {type='info', delay, color: useColor=true} = {}) {
  // log message
}
```
<!-- .element: class="large" -->

<br />

-----

#### Before

```js
function log(msg, opts = {}) {
  let {type='info', delay, color: useColor=true} = opts;

  // log message
}
```
<!-- .element: class="large" -->

NOTES:
_[10 minutes]_

- It's called object destructuring again! lol
- Object destructuring can also be done in function headers to simulate named parameters
- Now, not only is `opts` defaulted in the function header, but it's immediately destructured into the variables the function cares about
- And now anyone looking at the function header can tell what properties matter

/////

### After

```js
function log(msg, {type='info', delay, color: useColor=true} = {}) {
  // log message
}
```
<!-- .element: class="large" -->

-----


### Before

```js
function log(msg, opts) {
  var type, delay, useColor;

  if (!opts)
    opts = {};

  type = opts.type || 'info';
  delay = opts.delay;
  useColor = opts.color === undefined ? true : opts.color;

  // log message
}
```

NOTES:
_[11 minutes]_

- All of our code has moved into the function header!

/////

<!-- .slide: data-background="url(img/giphy/no-way-mickey-mouse.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- How many people find destructuring to actually make the code _less_ readable?
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
let [, mo, day, yr] = /^(\d\d)-(\d\d)-(\d\d)$/.exec('03-11-16');
    // mo='03', day='11', yr='16'
```
<!-- .element: class="large" -->

```js
function hi(a, [b, , d]) {
    // a='hello', b=1, d=3
}
hi('hello', [1, 2, 3]);
```
<!-- .element: class="large" -->

### Array destructuring

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

# Quick Hits

=====

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
<!-- .element: class="large" -->

Parameters list is unclear

NOTES:
- We have here a `join` method that takes a separator string followed by an unlimited number of parameters to join
- The fact that `join` takes more than one parameter is unclear let alone that it accepts an arbitrary number of them
- Because `join` uses the `separator` parameter the implementation has to start at index `1` of `arguments`
- And even if it could start at 0, `arguments` is only array-like so it doesn't have the `join` method that arrays have
- **NEED:** is an easy way to get an array of the parameters after `separator`
- And guess what? There's an ES6 feature for that

/////

# Rest parameters

Replace `arguments` with an array

<br />
<br />

[benmvp.com/learning-es6-parameter-handling/](http://www.benmvp.com/learning-es6-parameter-handling/#rest-parameters)

/////

Clearer function signature!

```js
function join(separator, ...values) {
  return values.join(separator);
}

// output: tic-tac-toe
join('-', 'tic', 'tac', 'toe');
```
<!-- .element: class="large" -->

-----

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
  - The rest parameter is an `Array` containing the rest of the parameters
  - Hence the name!
- Because `values` is a true array in the example, we can call join on it
- It’s also much **clearer** to see that `join()` takes an infinite number of parameters
- Rest parameter should pretty much replace all uses of the `arguments` keyword!

/////

Destructuring + rest parameters!

```js
let list = [9, 8, 7, 6, 5];
let [first, ...rest] = list;

// output: 9  [8, 7, 6, 5]
console.log(first, rest);
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way
```js
var list = [9, 8, 7, 6, 5],
    first = list[0],
    rest = list.slice(1);

// output: 9  [8, 7, 6, 5]
console.log(first, rest);
```
<!-- .element: class="large" -->

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
<!-- .element: class="large" -->

`Math.max.apply`???

NOTES:
_[21 minutes]_

- `Math.max` accepts an arbitrary number of numeric parameters and returns the maximum one
- If you want to get the maximum value of an array of numbers, you have to call `Math.max.apply`
- `apply` converts the array of values into a sequence of parameters
- But it's kind of esoteric
  - Plus you have to specify `null` as the context
- Maybe there's an ES6 feature for this?

/////

# Spread operator

Replace `apply` with the spread operator

<br />
<br />

[benmvp.com/learning-es6-parameter-handling/](http://www.benmvp.com/learning-es6-parameter-handling/#spread-operator)

/////

No more `apply`!

```js
let arrayOfValues = [33, 2, 9];
let maxValueFromArray = Math.max(...arrayOfValues);

// output: 33
console.log(maxValueFromArray);
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way

```js
var arrayOfValues = [33, 2, 9],
    maxValueFromArray = Math.max.apply(null, arrayOfValues);

// output: 33
console.log(maxValueFromArray);
```
<!-- .element: class="large" -->

NOTES:
- Instead of calling `apply` we can use the spread operator
- It's 3 dots preceding a parameter in a function call
- The spread operator _spreads_ out the array into individual parameters

/////

Spread operator  
Array &#8594; multiple parameters (function call)

```js
let arrayOfValues = [33, 2, 9];
let maxValueFromArray = Math.max(...arrayOfValues);
    // just like: Math.max(33, 2, 9)
```
<!-- .element: class="large" -->

-----

Rest operator  
Multiple parameters &#8594; array (function header)

```js
function join(separator, ...values) {
  // values = ['tic', 'tac', 'toe']
}

join('-', 'tic', 'tac', 'toe');
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

No more `concat`!

```js
let start = ['do', 're'];
let middle = ['mi', 'fa', 'so'];
let end = ['la', 'ti'];
let scaleFromLiteral = [...start, ...middle, ...end];

// output: ['do', 're', 'mi', 'fa', 'so', 'la', 'ti']
console.log(scaleFromLiteral);
```
<!-- .element: class="large" -->

-----

#### ES5 way

```js
let start = ['do', 're'];
let middle = ['mi', 'fa', 'so'];
let end = ['la', 'ti'];
let scaleFromConcat = start.concat(middle).concat(end);

// output: ['do', 're', 'mi', 'fa', 'so', 'la', 'ti']
console.log(scaleFromConcat);
```
<!-- .element: class="large" -->


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
<!-- .element: class="large" -->

NOTES:
_[24 minutes]_

- Over the last 2 decades of JavaScript, developers have iterated over array elements using the basic `for` loop
- You have to:
  - Keep track of the counter variable `i`
  - Control when the loop ends

/////  


ES3: `for` loop (revised)

```js
var list = [8, 3, 11, 9, 6],
    length = list.length,
    i;

for (i = 0; i < length; i++) {
  console.log(list[i]);
}
```
<!-- .element: class="large" -->

NOTES:
- Technically, since `i` is hoisted, you should define it at the top of the function
- The `length` of `list` gets retrieved w/ every iteration so we should store it
- No one wants to write loops like this!

/////

`for-in` does not work with arrays!

```js
var list = [8, 3, 11, 9, 6],
    i;

// DON'T DO THIS!!!!
for (i in list) {
  console.log(list[i]);
}
```
<!-- .element: class="large" -->

![Dikembe Mutombo No No No](img/giphy/no-no-no-mutombo.gif) <!-- .element: style="width:50%" -->

NOTES:
- You may be tempted to use the `for-in` loop to iterate over an array because it exists in other languages like Python
- But it has problems
- `for-in` can iterate in an arbitrary order
- The values on the iteration variable are actually strings not numbers!
  - So adding numbers to them results in concatenation not addition
- Any enumerable keys on the array will also be iterated over
- `for-in` was designed to iterate over regular objects with string keys only
  - Not arrays
- Don't do it!!!

/////

ES5: `forEach` method

```js
var list = [8, 3, 11, 9, 6];

list.forEach(function(value, i) {
  console.log(value);
});
```
<!-- .element: class="large" -->

What about `break`, `continue` & `return`?

<!-- .element: class="fragment" -->

NOTES:
- ES5 introduced the `forEach` method on arrays
- It’s a more succinct syntax.
  - You no longer need the counter variable and it will read all values until the end
- But what if you want to `break` out of the loop or `continue` to the next value?
  - That would be a syntax error because there’s no loop control
- What if you want to `return`?
  - You’d be returning from the `forEach` callback function, not stopping iteration
- So basically we'd like to combine the benefits of `for` and `forEach` together
- There's an ES6 feature for that!

/////

# `for-of`

Replace `for` and `forEach` with `for-of`

<br />
<br />

[benmvp.com/learning-es6-for-of-loop/](http://www.benmvp.com/learning-es6-for-of-loop/)

/////

ES6: `for-of`

```js
let list = [8, 3, 11, 9, 6];

for (let value of list) {
  console.log(value);
}
```
<!-- .element: class="large" -->

<br />

-----

#### Before

```js
var list = [8, 3, 11, 9, 6],
    length = list.length,
    i;

for (i = 0; i < length; i++) {
  console.log(list[i]);
}
```
<!-- .element: class="large" -->

NOTES:
- It’s still succinct because it doesn’t need a counter variable and reads to the end just like `forEach`
- It also supports `break`, `continue` and `return` unlike `forEach`
- `for-of` is for arrays and `for-in` is for objects
- Now JavaScript has a similar loop control structure that mirrors what you’d see in C#, Python or Java

===== <!-- .slide: data-transition="fade" -->

```js
'use strict';

MyObj.prototype.update = function() {
	$.get(this._url).done(function(responseData) {

		this._data = responseData;
	});
};
```
<!-- .element: class="large" -->

Where's the bug?

NOTES:

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
<!-- .element: class="large" -->

Undefined `this`!

NOTES:
- `this` is `undefined` in the callback function in strict mode
- `this` is the global scope (window) in loose mode
- Something that newbies scratch their head about
- Experienced JavaScript developers still run into it
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
<!-- .element: class="large" -->

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
<!-- .element: class="large" -->

ES5 fix

NOTES:
- `bind()` was introduced in ES5 and it creates a new function, passing the specified `this`
- Underscore and other shim have a bind method so it can work with ES3 browsers
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

Arrow functions works how you would expect!

```js
MyObj.prototype.update = function() {
	$.get(this._url).done(responseData => {
		// `this` uses "lexical scoping"
		this._data = responseData;
	});
};
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way

```js
MyObj.prototype.update = function() {
  $.get(this._url).done((function(responseData) {
    this._data = responseData;
  }).bind(this)); // pass in proper `this` context
};
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
$.ajax({url: 'test.html', cache: false})
    .done(html => {
        $('#results').append(html);
        console.log(html);
    });
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

```js
var first = 'Ben', last = 'Ilegbodu';

console.log('He said, "It\'s your fault!"');
    // He said, "It's your fault!"

console.log('Name: ' + last + ', ' + (15 + 16));
    // Name: Ilegbodu, 31

console.log('This is multi-line text, so\n' +
    'that newline characters are not\n' +
    'needed. Whitespace is respected\n');
```
<!-- .element: class="large" -->

Good ol' string concatenation

NOTES:

- Let's jump to another issue
- We usually don’t build string in JS anymore
- But we do sometimes have to provide messages to the user that have dynamic data

To make this easier, ES6 introduces...

/////

# Template literals

Replace string concatenation with template literals

<br />
<br />

[benmvp.com/learning-es6-template-literals-tagged-templates/](http://www.benmvp.com/learning-es6-template-literals-tagged-templates/)

NOTES:
- With template literals, we can stop using string concatenation

/////

String interpolation + multi-line!

```js
let first = 'Ben', last = `Ilegbodu`;

console.log(`He said, "It's your fault!"`);
    // He said, "It's your fault!"

console.log(`Name: ${last}, ${15 + 16}`);
    // Name: Ilegbodu, 31

console.log(`This is multi-line text, so
    that newline characters are not
    needed. Whitespace is respected
`);
```
<!-- .element: class="large" -->

NOTES:
- ES6 template literals are a brand new type of string literal, delimited by backticks (`` ` ``)
  - That’s not a typo!
  - That character to the left of the 1 key
  - Because of backticks, you no longer need to escape single or double quotes
- Template literals natively support string interpolation (token substitution)
  - Any JavaScript expression can be substituted inside ${ }
  - It will ultimately be coerced into a string
- Multi-line strings are now supported as well
  - Any whitespace you put will be in the string, including tabs and newlines
- You can actually always use template literals, but I tend to only use them when interpolating


=====

```js
function Todo(content, completed) {
    this.content = content;
    this.completed = completed;
}
Todo.prototype.toString = function() {
    return 'Content: ' + this.content +
        '\nCompleted: ' + this.completed;
};

var myTodo = new Todo('Learn ES6', true);
console.log(myTodo.toString());
```
<!-- .element: class="large" -->

Create classes via constructor functions

NOTES:
_[32 minutes]_

- Hitting the home stretch now
- Does anybody these days create "classes" using vanilla JavaScript these days?
- I think Angular 1 code might have
- Only done them as interview questions

/////

```js
var Todo = Backbone.Model.extend({
    toString: function() {
        return 'Content: ' + this.get('content') +
            '\nCompleted: ' + this.get('completed');
    }
});

var myTodo = new Todo({content: 'Learn ES6', completed: true});
console.log(myTodo.toString());
```
<!-- .element: class="large" -->

Create classes via class factories

NOTES:
- Instead we create classes using class factory methods provided by our favorite library
- Here's an example in Backbone
- We create a class by calling the `extend` static method on `Backbone.Model`
- We pass a giant object literal that has all the methods or properties to define
- Typically these methods will do more work than just create the class
  - They'll do some processing of the data prior to creating the class
- In the case of `Backbone.Model.extend()` it sets up a bucket of attributes you can set on the model

/////

# Classes

Replace class factories with `class` syntax

<br />
<br />

[benmvp.com/learning-es6-classes/](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Now we can replace assigning to the prototype or using custom class factories with native class syntax

/////

New ES6 `class` keyword

```js
class Todo {
    constructor(content, completed) {
        this.content = content;
        this.completed = completed;
    }
    toString() {
        return `Content: ${this.content}
            Completed: ${this.completed}`;
    }
}
```
<!-- .element: class="large" -->

NOTES:
- ES6 introduces the `class` keyword that defines a JavaScript "class"
- This isn't something new; it's just syntactic sugar over the ES5 constructor function
- But I feel like it's way more syntax friendly
- Methods within a class are just the name followed by parentheses. No need for `function` keyword
- The constructor is a special named method called `constructor`

/////

```js
function ColorTodo(content, completed, color) {
    Todo.call(this, content, completed);
    this.color = color;
}
ColorTodo.prototype = new Todo();

ColorTodo.prototype.toString = function() {
    return Todo.prototype.toString.call(this) +
        '\nColor: ' + this.color;
};

let myColorTodo = new ColorTodo('Learn ES6', true, 'red');
console.log(myColorTodo.toString());
```
<!-- .element: class="large" -->

Extending classes with **ES3/ES5**

NOTES:
- This is how you extend classes in ES3
- I'm assuming no one here has done this
- And this is actually the simplistic version without safety checks in ES5
- Just looking at the code it's hard to reason about what's going on here
- It's not all that clear that we're defining a `ColorTodo` class to inherit from `Todo`

/////

```js
class ColorTodo extends Todo {
    constructor(content, completed, color) {
        super(content, completed);
        this.color = color;
    }
    toString() {
        return `${super.toString()}
			Color: ${this.color}`;
    }
}

let myColorTodo = new ColorTodo('Learn ES6', true, 'red');
console.log(myColorTodo.toString());
```
<!-- .element: class="large" -->

Extending classes with **ES6**

NOTES:
- The ES6 class syntax also supports extending or inheriting classes using the `extends` keyword
- Within the constructor, you can just call `super()` to call the base class' constructor
- You **must** call `super()` before you can access `this` in the constructor
- Similarly you can override methods in inherited classes and call base methods by calling `super.` as we have in the `toString()` method
- To me, this is far clearer than the ES5 approach

/////

ES6 static methods

```js
class Todo {
    ...

    static add() {

    }
}
```
<!-- .element: class="large" -->

-----

#### ES5 way

```js
function Todo(content, completed) {
    ...
}
Todo.add = function() {

}
```
<!-- .element: class="large" -->

NOTES:
- ES6 class syntax also supports static methods with the `static` keyword
- The static method is defined within the `class` container
- In ES5 you would just add a named function directly to the constructor function

/////

ES6 class structure

```js
class MyClass extends BaseClass {
    constructor() { }
    methodOne() { }
    methodTwo() { }
    static staticMethodA() { }
    static staticMethodB() { }
}
```
<!-- .element: class="large" -->

<br />

-----

#### Class factories <!-- .element: class="fragment" data-fragment-index="0" -->  

```js
var MyClass = BaseClass.extend({
    toString: function() { }
});
MyClass.add = function() { };
```
<!-- .element: class="fragment large" data-fragment-index="0" -->  

NOTES:
- Here's the complete structure of ES6 classes
- I really like the new syntax & try to use it all the time
- But there seems to be a lot of folks in the community who don't like them
- They prefer to still use the class factories **[NEXT]** provided by their favorite library
- This because classes as defined by ES6 spec are incomplete
- But despite deficiencies, I still feel classes are worthwhile
- It's clear that there was a need to make them easier because every library has its own abstraction
- Class syntax provides a single standard that we can then improve on

/////

## ES6 class drawbacks

<br />

No properties support!

<br />

```js
class Todo {
    static todoCount = 0;
    completed = false;

    constructor() {
        console.log(this.completed);
        console.log(Todo.todoCount);
    }
}
```
<!-- .element: class="large" -->

[ES Class Fields & Static Properties](https://github.com/jeffmo/es-class-fields-and-static-properties) (Stage 1)

<!-- .element: style="font-size:smaller" -->

NOTES:
- Static & instance properties aren't supported in ES6
- In our previous examples we assigned properties in the `constructor`
- It's the only way to know that certain properties are defined
- Defining properties makes it clear what properties are supported and allows us to provide defaults
- There is a proposal to add support that's currently only in Stage 1

/////

## ES6 class drawbacks

<br />

No mix-ins support!

<br />

```js
class Person {
    @readonly
    name() { return `${this.first} ${this.last}` }
}
```
<!-- .element: class="large" -->

[Class & Property Decorators](https://github.com/wycats/javascript-decorators) (Stage 1)

<!-- .element: style="font-size:smaller" -->

NOTES:
- With class factories we can use mix-ins to mix in other helpers methods into a class
- This is because the class was defined from an object literal
- With mix-ins we just add more functions to the literal before the class is actually created
- ES6 classes don't support this in their syntax
- However, there is a spec proposal for decorators that can solve similar problems & also currently sits at Stage 1

/////

## ES6 class drawbacks

<br />

Interoperability challenges!

<br />

```js
class Todo extends Backbone.Model {

}
```
<!-- .element: class="large" -->

NOTES:
- Because ES6 classes are just syntactic sugar of constructor functions they _should_ be interoperable with ES5 clases
- You should technically be able to use `extends` with a JavaScript class defined using constructor functions like in our example above
- However, most class factory functions (i.e. `Backbone.Model.extends()`) do a lot more processing before creating the derived class so it doesn't always work
- Depends on the library
- React has a class factory function for creating its components in ES5, but they've also put a lot of work in also making it ES6 class friendly. Other libraries need to follow suit
- Ember & Angular 2 have done the same

=====

```js
var Car = Backbone.Model.extend({
    evaluate: function(condition) {
        var value;

        ...

        return {
            value: value,
            condition: condition
        };
    }
});
```
<!-- .element: class="large" -->

NOTES:
_[39 minutes]_

- For our final feature, let's revisit class factories
- Remember we're passing a big object literal that contains the class configuration
- Defining a `Car` class that has an `evaluate` method
- Within the method we pass in `condition` & define the `value` variable
- There is some computation to determine `value`
- The result of `evaluate` is returning an object literal with keys the same as the variable name
- There's nothing _really_ wrong with this but...

/////

# Object literal shorthand

Write less code than before

<br />
<br />

[benmvp.com/learning-es6-enhanced-object-literals/](http://www.benmvp.com/learning-es6-enhanced-object-literals/)

/////

Object literals shorthand

```js
const Car = Backbone.Model.extend({
    evaluate(condition) {
        let value;

        return {
            value,
            condition
        };
    }
});
```

-----

#### ES5 way

```js
var Car = Backbone.Model.extend({
    evaluate: function(condition) {
        var value;

        return {
            value: value,
            condition: condition
        };
    }
});
```

NOTES:
- With ES6 we have object literal shorthand
- Remember we're passing a big object literal to `Backbone.Model.extend()`
- When specify methods we can get rid of `: function` using method shorthand
  - Just have method name and parameters (like `class` syntax)
- Within `evaluate`, because the object literal has keys that match the variables, we can just list the keys using property value shorthand
- This applies to **all** object literals, not just when they're used with class factories
- But if you either can't or don't want to use ES6 classes, you can still benefit from more succinct syntax with class factories

=====

# Just for fun!

/////

## String API

`String.prototype.startsWith`

`String.prototype.endsWith`

`String.prototype.includes`

`String.prototype.repeat`

`String.raw`

NOTES:
- Just want to alert you to some new methods introduce with ES6 for `String`

/////

## Array API

`Array.from`

`Array.of`

`Array.prototype.find`

`Array.prototype.findIndex`

`Array.prototype.copyWithin`

`Array.prototype.fill`

NOTES:
- Also some useful methods for `Array` too

=====

## Review

1. Block scoping <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->  
1. Default parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Destructuring <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Rest parameters <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Spread operator <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. `for-of` <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->
1. Template literals <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Arrow functions <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Classes <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. Object literal shorthand <!-- .element: class="fragment highlight-blue" data-fragment-index="0" -->
1. String APIs <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->
1. Array APIs  <!-- .element: class="fragment highlight-red" data-fragment-index="0" -->

NOTES:
- As a reminder, here's what we covered to make our code clearer and more succinct
- I know I went through it pretty quickly, so if you didn't get it at all, they're recording this talk so you can always revisit later

=====

# Using ES6 now

Native execution vs. Transpiling

<br />
<br />

[benmvp.com/learning-es6-using-es6-right-now/](http://www.benmvp.com/learning-es6-using-es6-right-now/)

NOTES:
- Before we wrap up, let's quickly talk about how we can use these features now

/////

## Native JavaScript engine support

<br />
<br />

<div style="display:flex;align-items:flex-end;justify-content:space-between;">
	<div style="flex:0 0 10%;">
	  ![Google Chrome Logo](img/google-chrome-logo.png)
	  97%
	</div>
	<div style="flex:0 0 10%">
	  ![Mozilla Firefox Logo](img/mozilla-firefox-logo.png)
	  85%
	</div>
	<div style="flex:0 0 10%">
	  ![Microsoft Edge Logo](img/microsoft-edge-logo.png)
	  83%
	</div>
	<div style="flex:0 0 10%">
	  ![Apple Safari Logo](img/apple-safari-logo.png)
	  56%
	</div>
	<div style="flex:0 0 10%">
	  ![Opera Logo](img/opera-logo.png)
	  97%
	</div>
	<div style="flex:0 0 10%">
	  ![Webkit Logo](img/webkit-logo.png)
	  90%
	</div>
	<div style="flex:0 0 10%">
	  ![NodeJS Logo](img/nodejs-logo.png)
	  58%
	</div>
	<div style="flex:0 0 10%">
	  ![iOS 9 Logo](img/ios9-logo.png)
	  56%
	</div>
</div>

<br />
<br />

[ECMAScript 6 Compatibility Table](http://kangax.github.io/compat-table/es6/)

NOTES:
- ES6 support is pretty mixed. Chrome Canary is at 97% while Safari is at an abysmal 54%
- Node 5 is lagging behind, although Node 6 should have significantly more features
- It's already April of 2016 and ES2016 spec is coming soon
  - They haven't even finished ES2015 yet!
- I think this is why they decided to go to a yearly cadence to keep specs from being too big
- You may notice IE missing from the list. None of them support ES6
- Only option is transpiling

/////

### Transpiling ES6 &#8594; ES3/ES5

![Babel ES6 Live Transpiling](img/es6/babel-es6-transpile.gif)

NOTES:
- Transpiling lets you compile your ES6 code down to ES3/ES5 code for cross-browser compatibility
- So basically what you would do is write your code in ES6
- Then in your build step when converting SASS to vanilla CSS, minifying and so forth
- You would also run the transpiler to convert your ES6 code to ES5

/////

## Transpilers

<div style="display:flex; align-items:flex-end; justify-content:space-between;">
    <div style="flex:0 0 25%">
      [![Traceur Logo](img/es6/traceur-logo.png)](https://github.com/google/traceur-compiler)
      [Traceur](https://github.com/google/traceur-compiler)  
      60%
    </div>
    <div style="flex:0 0 25%">
      [![Babel Logo](img/es6/babel-logo.png)](https://babeljs.io/)   
      [Babel](https://babeljs.io/)   
      73%
    </div>
    <div style="flex:0 0 25%">
      [![TypeScript Logo](img/es6/typescript-logo-square.png)](http://www.typescriptlang.org/)  
      [TypeScript](http://www.typescriptlang.org/)  
      59%
    </div>
</div>

NOTES:
- There are 3 major ES6 transpilers
- Traceur
- Babel
- TypeScript
- As you can see, Babel has the most support
- I actually prefer it over the others, but they more or less accomplish the same tasks
- If you visit the websites they have interactive transpilers you can play around with
- The previous animation was the Babel online REPL
- Babel is super popular because it also supports React's JSX syntax

=====

## Additional Resources

- **[_Learning ES6_](/learning-es6-series/) by Ben Ilegbodu**
- [ES6 Katas](http://es6katas.org/) by Wolfram Kriesing
- [_Exploring ES6_](http://exploringjs.com/es6/) by Axel Rauschmayer
- [_Understanding ECMAScript 6_](https://leanpub.com/understandinges6/) by Nicholas C. Zakas
- [_ES6 in Depth_](https://hacks.mozilla.org/category/es6-in-depth/) by Jason Orendorff
- [_ES6 in Depth_](http://ponyfoo.com/articles/tagged/es6-in-depth) by Nicolas Bevacqua

NOTES:
_[45 minutes]_

- Shameless plug!
- You can also check out my blog where I go into detail about every feature I covered
- Other great books & blogs about ES6 too!

=====

# Shoutouts

/////

![Nation JS Node Day](img/nationjs-logo.jpg)   <!-- .element: style="width: 50%;height: 50%" -->

/////

![Eventbrite logo](img/eventbrite-logo.png)

## We're hiring!   <!-- .element: class="fragment" -->

/////

# YOU!

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct

=====

<!-- .slide: data-background="url(img/giphy/thanks-jack-sparrow.gif) no-repeat center" data-background-size="contain"-->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

NOTES:
- Slides are on my Twitter profile and blog
