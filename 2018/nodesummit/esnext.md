<!-- .slide: data-state="title-page" -->

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 45%;">
		<img src="../../img/esnext/zac-ong-467632-unsplash.jpg" style="width:100%;height:auto;" alt="Man breakdancing in front of a crowd" class="plain" />
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>ES.next features that'll make ya 💃🕺🏾!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#NodeSummit](https://twitter.com/hashtag/NodeSummit)</p>

  <br />

  <p>July 24, 2018</p>
  
  
  </div>
</div>

NOTES:
- ES.next is just future JavaScript

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->


# Recap
<!-- .element: style="margin-top: 4em; -webkit-text-stroke: black 5px; color: white; font-size: 4em" -->

NOTES:
- Before we jump into what's coming up next
- Let's take a quick walk down memory lane

/////

## ES6/ES2015

#### Syntax

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller;margin-bottom:1em">
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

<div style="columns:3;-webkit-columns:3;-moz-columns:3;font-size:smaller;margin-bottom:1em">
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

**Node 6+ support! 😎**

NOTES:
- Full list of features included in the ES6 specification
- That's 30+ features!
- Works with Node 6 and higher

/////

## ES7/ES2016

<br />

- [`Array.prototype.includes`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes)
- [Exponentiation operator (`**`)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Exponentiation_(**)

<br />

**Node 8+ support! 😎**

NOTES:
- With ES6 they moved to a yearly release cadence so they won't have this huge dump of features
- Not much happened in ES2016 as everyone was catching their breath
- `Array.prototype.includes` works with Node 6+
- Exponentiation with Node 8+

/////

## ES2017

<br />

- [`async` / `await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function) 🔥
- [`Object.values`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Object/values) / [`Object.entries`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/entries)
- `String.prototype.(`[`padStart`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart)/[`padEnd`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd)`)`
- [`Object.getOwnPropertyDescriptors`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptors)
- [Trailing function commas](http://2ality.com/2015/11/trailing-comma-parameters.html)
- [Shared memory and atomics](http://2ality.com/2017/01/shared-array-buffer.html)

<br />

**Node 8+ support! 😎**

NOTES:
- Async functions were the big feature of ES2017
  * Many folks thought it'd be in ES7
- We got string padding so no more `leftpad` node module!
- Available in Node 8+

=====
<!-- .slide: data-background="url(../../img/esnext/jake-hills-389-unsplash.jpg) no-repeat center" data-background-size="cover" -->

# ES.next
<!-- .element: style="margin-top: 2.5em; -webkit-text-stroke: black 5px; color: white; font-size: 4em" -->

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 6px; color: white; font-size: 5em" -->

NOTES:
- But first, would like everyone to stand up!
- Squats counting down from 10 to 1
- Now turn to your neighbors, introduce yourself & say hi

/////

## me.json

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 35%;">
		<img src="../../img/family-tahoe-2018-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family at Tahoe in 2018" />
	</div>
	<div style="flex:0 0 60%;">
		<pre class="large"><code class="lang-json">
{
  "name": "Ben Ilegbodu",
  "priorities": [
    "Jesus", "family", "work"
  ],
  "location": "Pittsburg, CA",
  "work": "Eventbrite",
  "role": "Principal Frontend Engineer",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
</div>

NOTES:
/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I'm a Principal Frontend Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- Probably heard of us before; apparently Reactathon organizers haven't because they used one of our competitors
- Part of our Frontend Platform team
- We don't typically work on end-user features, but building the frontend platform that other devs build on top of
- Two main objectives: frontend infrastructure & component library

/////

<!-- .slide: data-background="url(../../img/giphy/james-harden-wesley-johnson-ankles.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- Even though I've now lived in the Bay Area for over 15 years, I was born and raised in Houston, Texas
- So I'm a die-hard Rockets fan
- And this is gonna be our year

=====

<!-- .slide: data-background="url(../../img/esnext/jake-hills-389-unsplash.jpg) no-repeat center" data-background-size="cover" -->

# ES.next
<!-- .element: style="margin-top: 2.5em; -webkit-text-stroke: black 5px; color: white; font-size: 4em" -->

=====

<!-- .slide: data-background="url(../../img/esnext/nordwood-themes-467442-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Spec was just finalized 2 weeks ago!
- Wanna show a couple of features I'm excited about

/////

[Spread Properties](http://2ality.com/2016/10/rest-spread-properties.html)

```js
const warriors = {steph: 95, kd: 97, klay: 82, dray: 79}
const newWarriors = {
  ...warriors,
  boogie: 86,
}
```
<!-- .element: class="large" -->

-----

#### Pre-ES2018 way

```js
const warriors = {steph: 95, kd: 97, klay: 82, dray: 79}
const newWarriors = Object.assign({}, warriors, {
  boogie: 86,
})
```

<br />

**Node 8+ support! 😎**

NOTES:
- ES6/ES2015 gave us the ability to use spread operator in arrays & destructuring for objects
- Now we can officially use spread operator for objects
- Now we copy objects while adding new properties in one object literal definition
- ES2015 introduced `Object.assign()` but you have to make sure to have the empty object first

- You may be surprised that this just now becoming official
- We've had this for over a year in Node 8
- And I've been using this in React for over 2 years
- It had been in the proposal process for a while

/////

[Rest Properties](http://2ality.com/2016/10/rest-spread-properties.html)

```js
const calcWins = (warriors) => {
  const {steph, kd, klay, dray, boogie, ...whoCares} = warriors
  // `whoCares` is an object with rest of warriors players
}
```
<!-- .element: class="large" -->

-----

#### Pre-ES2018 way

```js
const calcWins = (warriors) => {
  const {steph, kd, klay, dray, boogie} = warriors
  const whoCares = _.omit(warriors, ['steph', 'kd', 'klay', 'dray', 'boogie'])
}
```

<br />

**Node 8+ support! 😎**

NOTES:
- Flip side of the coin is rest properties
- Rest operator with destructuring gives us the rest of players as an object
  * Could be empty
- We could've used destructuring to get out the players we cared about
- But had to use `_.omit` to get the rest

/////

Object destructuring + rest operator in function header FTW!

```js
const calc = ({steph, kd, klay, dray, boogie, ...whoCares}) => {
  // `whoCares` is an object with rest of warriors players
}
```
<!-- .element: class="large" -->

<br />

**Node 8+ support! 😎**

NOTES:
- Can move the whole destructuring + rest into the function header
- Named parameters!

/////

[`Promise.prototype.finally`](http://2ality.com/2017/07/promise-prototype-finally.html)

```js
let connection;
db.open()
  .then((conn) => {
      connection = conn
      return connection.select({ name: 'Jane' })
  })
  .catch( ... )
  .finally(() => {
      connection.close()
  })
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 185px; top: 533px"></div>


<br />

**Node 10+ support! 😎**

NOTES:
- There's now a 3rd method on `Promise` called `.finally()`
- It gets called no matter if things succeed or if there's an error
- Like with `try`-`catch`-`finally` this is a great place to do clean up

- Actually works with Node 8 if you turn on a flag

/////

[`Promise.prototype.finally`](http://2ality.com/2017/07/promise-prototype-finally.html)

```js
let connection;
db.open()
  .then((conn) => {
      connection = conn
      return connection.select({ name: 'Jane' })
  })
  .catch( ... )
  .then(() => {
      connection.close()
  })
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 185px; top: 533px"></div>

<br />

Do we really need `.finally()`??

NOTES:
- You may be wondering how this is any different than sticking `.then()` on the end instead
- There are 3 main differences:
  * If the `.catch()` threw an error, the last `.then()` wouldn't get called
  * If you didn't have a `.catch()` at all and there was an error, the last `.then()` wouldn't get called
  * `.finally()` passes the value from the last `.then()` through automatically

/////

## ES2018

<br />

- [Rest/Spread Properties](http://2ality.com/2016/10/rest-spread-properties.html)
- [`Promise.prototype.finally`](http://2ality.com/2017/07/promise-prototype-finally.html)
- [Template Literal Revision](http://2ality.com/2016/09/template-literal-revision.html)
- [Asynchronous iteration](http://2ality.com/2016/10/asynchronous-iteration.html)
- [`RegExp` named capture groups](http://2ality.com/2017/05/regexp-named-capture-groups.html)
- Other regular expression features

<br />

**Node 10+ support! 😎**

NOTES:
- Full list of features in ES2018
- The spec was just finalized 2 weeks ago
- Folks are pretty excited about async interation and some of the regex improvements

=====

<!-- .slide: data-background="url(../../img/esnext/joanna-kosinska-129039-unsplash.jpg) no-repeat center" data-background-size="cover" -->

# ECMAScript
# Proposal Process

NOTES:
- May be wondering how features get bundled in yearly releases
- 4-stage process
- Features have to be in the final stage by February 1st of the release year
- Basically the January meeting of the year is when it is finalized
- Gets released in July
- ES2018 was just officially released

=====

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 45%;">
		<img src="../../img/esnext/jari-hytonen-538885-unsplash.jpg" style="width:100%;height:auto;" alt="4 kittens climbing out of a basket" class="plain" />
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>Stage 4</h1>
  <h2>(Finished)</h2>

  <ul style="margin-top: 2em">
    <li>In ES2019</li>
    <li>Spec is complete</li>
    <li>2+ real implementations</li>
  </ul>
  
  
  </div>
</div>

NOTES:
- Stage 4 is the final stage
- Feature will be in the next release
- Specification is complete
- Has two compatible implementations which pass additional acceptance test suite
- Has significant in-the-field experience with **shipping** implementations, such as that provided by two independent VMs
- Spec is not expected to change except for wording edits to spec

- Let's take a look at one example...

/////

## Handling exceptions 😔

```js
let jsonData;

try {
  jsonData = JSON.parse(str); 
} catch(ex) {
  jsonData = DEFAULT_DATA;
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 373px"></div>

<br />

I don't care about `ex`! 😫

NOTES:
- Have you ever written code like this with a `try`-`catch`?
- It...
- In the `catch`, you don't care about the exception
  * Either because it doesn't matter or you know what it is
- But we still have to provide a variable for it!
  * Omitting is a syntax error
- Unused variable lint rules have to make special concessions for this!

/////

## Handling exceptions 😀

```js
let jsonData;

try {
  jsonData = JSON.parse(str); 
} catch {
  jsonData = DEFAULT_DATA;
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 373px"></div>

<br />

[Proposal: Optional catch binding](http://2ality.com/2017/08/optional-catch-binding.html) (**Node 10+ support! 😎**)

NOTES:
- Now with **optional catch binding** now we don't need to specify `ex`
- Something that exists in many other languages
- There's a whole Github issue bikeshedding on necessity of the proposal

=====

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 45%;">
		<img src="../../img/esnext/fabian-burghardt-84752-unsplash.jpg" style="width:100%;height:auto;" alt="Three horses standing close to each other and looking at the camera" class="plain" />
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>Stage 3</h1>
  <h2>(Candidate)</h2>

  <ul style="margin-top: 2em">
    <li><em>Maybe</em> next release</li>
    <li>Spec is complete</li>
    <li>Needs implementations</li>
  </ul>
  
  </div>
</div>

NOTES:
- Specification is considered complete
  * Spec will only change based upon implementations necessitating one
- Needs real-world implementations which pass additional acceptance test suite
- May be in ES2019, may not
- Object rest/spread sat in Stage 3 for nearly 2 years

/////

## Classes in JavaScript 😕

```js
class SelectField extends React.Component {
  constructor(props) {
    super(props)
    this.state = { ... }
  }

  _getOptions() { ... }

  render() {
    const options = this._getOptions()
    ...
  }
}
SelectField.propTypes = { ... }
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 80px; top: 878px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 308px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 483px"></div>

NOTES:
- ES2015 syntax introduced class syntax in JavaScript
  * Great start, but lacked some important qualities
  * The ability to declare/initialize fields
  * Mark fields/methods as private
- Here's a React component written using a JS class
- **First:** Static `propTypes` added to the class afterwards
- **Second:** Declaring a instance field called `state` w/in the `constructor()`
- **Third:** Declaring a "private" method called `_getOptions()`
  * Not truly private, just a convention. Still accessible
  * There are other ways to make things private using `Symbol` or `WeakMap` but are verbose
- With 3 new Stage 3 proposals we can make this more legit!

/////

## Classes in JavaScript 😐

```js
class SelectField extends React.Component {
  static propTypes = { ... }

  constructor(props) {
    super(props)
    this.state = { ... }
  }
  _getOptions() { ... }
  render() {
    const options = this._getOptions()
    ...
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 80px; top: 198px"></div>

[Proposal: Static class features](https://github.com/tc39/proposal-static-class-features/)

NOTES:
- First we can bring that static declaration from outside the class to inside
- We use the `static` keyword for the field
- ES2015 had `static` methods, but now this proposal adds static fields
- It's possible if you've been doing React that you've already been using this for `propTypes`
- Folks have been using this feature since it was introduced at Stage 1
- We can go further! What about the `state` declaration?

/////

## Classes in JavaScript 😀

```js
class SelectField extends React.Component {
  static propTypes = { ... }

  state = { ... }

  _getOptions() { ... }

  render() {
    const options = this._getOptions()
    ...
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 80px; top: 308px"></div>

[Proposal: Class fields](http://2ality.com/2017/07/class-fields.html)

NOTES:
- We can move that `state` declaration and initialization outside of the `constructor`
  * In fact we don't need the `constructor` at all now!
- It makes the `class` more declarative to because we can see all of the properties it defined
  * Instead of having to hunt w/in the `constructor` or other methods
- FYI these class fields get initialized **before** the `constructor` is run
- Probably have seen/used this before too
- The class is looking really nice, but we can do more!
- `_getOptions` is only "private" by convention

/////

## Classes in JavaScript 😁

```js
class SelectField extends React.Component {
  static propTypes = { ... }

  state = { ... }

  #getOptions() { ... }

  render() {
    const options = this.#getOptions()
    ...
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 80px; top: 423px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 593px"></div>

[Proposal: Private methods](https://github.com/tc39/proposal-private-methods)

NOTES:
- We can use the `#` to signal that the `getOptions` method is private
- It can no longer be accessed outside of the class; truly private
- **NOTE:** You can make fields private too; even `static` & private
- Maybe wondering why using `#` instead of `private` keyword
  * Read explanations and I _think_ it boils down to how these private fields/methods are implemented
  * The `#` in `this.#getOptions` helps the interpreter know where to find the data

=====

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 35%;">
		<img src="../../img/esnext/harshil-gudka-616909-unsplash.jpg" style="width:100%;height:auto;" alt="Two giraffes in the safari" class="plain" />
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>Stage 2</h1>
  <h2>(Draft)</h2>

  <ul style="margin-top: 2em">
    <li>Formalize the specification</li>
    <li><em>Should</em> eventually release</li>
  </ul>
  
  </div>
</div>

NOTES:
- Committee expects the feature to be developed and eventually included in the standard (not guaranteed)
- There's a _rough_ spec coming in
- Objective is to formalize the spec
- There should really only be incremental changes to the spec
- Still a gamble to use
- There's nothing sitting at Stage 2 that I really am excited about
- There are Class Decorators, but I'm not a big fan of those

=====

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 35%;">
		<img src="../../img/esnext/ian-robinson-218271-unsplash.jpg" style="width:100%;height:auto;" alt="Tiger staring at camera at Edinburgh Zoo" class="plain" />
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>Stage 1</h1>
  <h2>(Proposal)</h2>

  <ul style="margin-top: 2em">
    <li>Has a "champion"</li>
    <li>Identify problem + solution</li>
    <li>Spec can/will change</li>
  </ul>
  
  </div>
</div>

NOTES:
- Has a "champion"
- Text outlining the problem & potential solution
- Example usages & high-level API
- Discussion of implementation challenges
- Committee expects to devote time to examining the problem space, solutions and cross-cutting concerns
- Make the case for the addition
- Spec can change drastically as its being formalized
- **HUGE** gamble to use
- There are some fun ones here

/////

## Conditional property accessing 😔

```js
const address = user.address
```
<!-- .element: class="large" -->

```js
const address = user && user.address
```
<!-- .element: class="large fragment" -->

```js
const address = (user || {}).address
```
<!-- .element: class="large fragment" -->

```js
const address = user ? user.address : undefined
```
<!-- .element: class="large fragment" -->

```js
const address = user == null ? user.address : undefined
```
<!-- .element: class="large fragment" -->

NOTES:
- In JS we can access properties simply
- But what happens if `user` may be `null` or `undefined`?
- You have to check it first
- There are several ways we can do this

/////

## Conditional deep property accessing 😭

```js
const street = user.address.street
```
<!-- .element: class="large" -->

```js
const street = user && user.address && user.address.street
```
<!-- .element: class="large fragment" -->

```js
const street = ((user || {}).address || {}).street
```
<!-- .element: class="large fragment" -->

```js
const street = user 
  ? (user.address ? user.address.street : undefined)
  : undefined
```
<!-- .element: class="large fragment" -->

NOTES:
- And what if you have to go multiple levels deep?
- It gets even more gnarly

/////

## Conditional property accessing 😀

After
```js
const address = user?.address
```
<!-- .element: class="large" -->

Before
```js
const address = user == null ? user.address : undefined
```

<br />

After
```js
const street = user?.address?.street
```
<!-- .element: class="large" -->

Before
```js
const street = user && user.address && user.address.street
```

<br />

[Proposal: Optional chaining](https://github.com/tc39/proposal-optional-chaining)

NOTES:
- The optional chaining operator is: `?.`
- If the expression before it is `undefined`/`null` it'll short-circuit and return that
  * Otherwise it'll return whatever is after

/////

## Conditional function calls 😉

After
```js
user?.update()
```
<!-- .element: class="large" -->

Before
```js
user && user.update()
```

<br />

After
```js
update?.()
```
<!-- .element: class="large" -->

Before
```js
update && update()
```

<br />

[Proposal: Optional chaining](https://github.com/tc39/proposal-optional-chaining)

NOTES:
- Can also use the optional chaining operator with functions
- **First:** Check to see if the object exists and if it does call the expected method
- **Second** If you just have a function reference you can check before calling it!

=====

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 45%;">
    <a href="https://twitter.com/rachsmithtweets/status/892478598765887488/" target="_blank">
		  <img src="../../img/esnext/rachel-smith-stage-0-tweet.png" style="width:100%;height:auto;" alt="hey you can use stage 0 features down here" class="plain" />
    </a>
	</div>
	<div style="flex:0 0 45%;">
  
  <h1>Stage 0</h1>
  <h2>(Strawman)</h2>

  <ul style="margin-top: 2em">
    <li>No real spec</li>
    <li>Public for feedback</li>
    <li>Don't get 🔥!</li>
  </ul>
  
  </div>
</div>

NOTES:
- Of course there's a stage 0
- It's basically public so others can give feedback
- There's no real spec
- It'd be downright criminal for you to use stage 0
- Decorators were stage 0 after ES2015, and so many folks were burned
- Don't even really wanna show any
- Some have been here since 2014!
- None were really interesting...

=====

## Using it now

<div style="display:flex; align-items:flex-end; justify-content:space-between; margin-top: 2em">
    <div style="flex:0 0 45%">
      <a href="https://babeljs.io/" target="_blank">
        <img src="../../img/es6/babel-logo.png" alt="" class="plain" />
      </a>
      <br />
      <a href="https://babeljs.io/" target="_blank">
        Babel
      </a>
    </div>
    <div style="flex:0 0 45%">
      <a href="http://www.typescriptlang.org/" target="_blank">
        <img src="../../img/es6/typescript-logo-square.png" alt="" class="plain" />
      </a>
      <br />
      <a href="http://www.typescriptlang.org/" target="_blank">TypeScript</a>
    </div>
</div>

NOTES:
- The way to use features now before they are standard is w/ transpilers
- Generally safe to use Stage 3 & higher
- TypeScript tends to **only** support Stage 3 and higher
- Babel is more configurable with presets & plugins that allow you to use features down to Stage 0
  * At your own risk

=====

# Recap

<br />

- [Rest/Spread Properties](http://2ality.com/2016/10/rest-spread-properties.html) (ES2018) ![](../../img/nodejs-logo.png) <!-- .element: class="plain" style="width: 5%; vertical-align: middle; margin: 0" -->
- [`Promise.prototype.finally`](http://2ality.com/2017/07/promise-prototype-finally.html) (ES2018) ![](../../img/nodejs-logo.png) <!-- .element: class="plain" style="width: 5%; vertical-align: middle; margin: 0" -->
- [Optional catch binding](http://2ality.com/2017/08/optional-catch-binding.html) (ES2019) ![](../../img/nodejs-logo.png) <!-- .element: class="plain" style="width: 5%; vertical-align: middle; margin: 0" -->
- [Static class features](https://github.com/tc39/proposal-static-class-features/) (Stage 3)
- [Class fields](http://2ality.com/2017/07/class-fields.html) (Stage 3)
- [Private methods](https://github.com/tc39/proposal-private-methods) (Stage 3)
- [Optional chaining](https://github.com/tc39/proposal-optional-chaining) (Stage 1)

NOTES:
- Recap of the features we discussed
- First three are available in Node 10+ right now!
- Pretty sure the class features will be available in next major version
  * Already exist in Chrome

/////

## Resources

<br />

- [ECMAScript Github Repo](https://github.com/tc39/ecma262)
- [ES2016+ Compatibility Table](http://kangax.github.io/compat-table/es2016plus/)
- [ES.next Compatibility Table](http://kangax.github.io/compat-table/esnext/)
- [ECMAScript Living Spec](https://tc39.github.io/ecma262/)
- [TC39 Proposal Process](https://tc39.github.io/process-document/)
- [TC39 Meeting Notes](https://github.com/rwaldron/tc39-notes)
- [ECMAScript Test Suite](https://github.com/tc39/test262)

=====

# THANKS!

![Jack Sparrow Thanks](../../img/giphy/thanks-jack-sparrow.gif)
<!-- .element: style="width: 50%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So that's it!
- Ask questions on Twitter, via email or AMA!
- Thanks!
