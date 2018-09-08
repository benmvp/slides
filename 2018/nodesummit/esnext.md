<!-- .slide: data-state="title-page" data-background="url(../../img/esnext/atharva-tulsi-534150-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="content-overlay">
  
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
- Good afternoon!
- Want to introduce you to future JavaScript features that I'm excited about
- ES.next is just that -- future JavaScript
- And what's future today will be current very soon
- BTW: tweeted out a link to slides already

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">Recap</h1>
    <h2 style="font-size: 2.5em">(ES2015 - ES2017)</h2>
  </div>
</div>

NOTES:
- Before we jump into what's coming up next
- Let's take a quick walk down memory lane

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>ES6/ES2015</h1>

    <h4>Syntax</h4>

<div style="-webkit-columns:4;-moz-columns:4;columns:4;font-size:smaller;margin-bottom:1em">
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

<h4>Functionality</h4>

<div style="-webkit-columns:4;-moz-columns:4;columns:4;font-size:smaller;margin-bottom:1em">
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

**Node 6+ support*! 😎**

  </div>
</div>

NOTES:
- Full list of features included in the ES6 specification
- That's 30+ features!
  * Block scoping
  * Promises
  * WeakMaps
  * Arrow functions
  * Classes
  * Modules
  * etc
- Works with Node 6 and higher
  * With a few exceptions

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 45%" class="content-overlay">
  
  <h1>ES7/ES2016</h1>

    <ul style="margin-top: 2em;margin-bottom: 2em">
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/includes" target="_blank"><code>Array.prototype.includes</code></a></li>
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Arithmetic_Operators#Exponentiation_(**)" target="_blank">Exponentiation operator (<code>**</code>)</a></li>
    </ul>
  
    <p><strong>Node 8+ support! 😎</strong></p>
  </div>
</div>


NOTES:
- Moved to a yearly release cadence
  * Didn't want this huge dump of features
- "ES7" was never really a thing: ES2016
- Not much happened in ES2016 as everyone was catching their breath
- `Array.prototype.includes` works with Node 6+
- Exponentiation with Node 8+

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 55%" class="content-overlay">
  
  <h1>ES2017</h1>

    <ul style="margin-top: 2em;margin-bottom: 2em">
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function" target="_blank"><code>async</code> / <code>await</code></a> 🔥</li>
      <li>
        <a href="https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_objects/Object/values" target="_blank"><code>Object.values</code></a> /
        <a href="https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Object/entries" target="_blank"><code>Object.entries</code></a>
      </li>
      <li><code>String.prototype.(<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padStart" target="_blank">padStart</a>/<a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/padEnd" target="_blank">padEnd</a>)</code></li>
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/getOwnPropertyDescriptors" target="_blank"><code>Object.getOwnPropertyDescriptors</code></a></li>
      <li><a href="http://2ality.com/2015/11/trailing-comma-parameters.html" target="_blank">Trailing function commas</a></li>
      <li><a href="http://2ality.com/2017/01/shared-array-buffer.html" target="_blank">Shared memory and atomics</a></li>
    </ul>
  
    <p><strong>Node 8+ support! 😎</strong></p>
  </div>
</div>

NOTES:
- Just named by the year
- Async functions were the big feature of ES2017
  * Many folks thought it'd be in ES7
- We got string padding so no more `leftpad` node module!
- Available in Node 8+

=====
<!-- .slide: data-background="url(../../img/esnext/jake-hills-389-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">ES.next</h1>
  </div>
</div>

NOTES:
- OK, now let's talk about what's coming next

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But first, would like everyone to stand up!
- Gonna try to do that break dancing move from the opening slide
  * Kidding!
- Squats counting down from 10 to 1
- Now turn to your neighbors, fist bump & say hi

/////
<!-- .slide: data-background="#000 url(../../img/family-naima-wedding.png) no-repeat center" data-background-size="contain" -->

NOTES:
- I'm a Principal Frontend Engineer at Eventbrite
- Been working on FE infra writing shell scripts in Node
- Been using some of these JS features I'm showing

=====

<!-- .slide: data-background="url(../../img/esnext/jake-hills-389-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">ES.next</h1>
  </div>
</div>

NOTES:
- Okay, let's really talk about ES.next now

=====
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">ES2018</h1>
  </div>
</div>

NOTES:
- Start with ES2018
- Spec was just ratified earlier this month!
- Wanna show a couple of features I'm excited about

/////
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <h1><a href="http://2ality.com/2016/10/rest-spread-properties.html" target="_blank">Spread Properties</a></h1>
    <pre class="large"><code class="lang-javascript">const warriors = {steph: 95, kd: 97, klay: 82, dray: 79}
const newWarriors = {
  ...warriors,
  boogie: 86,
}</code></pre>

    <hr />

    <h4>Pre-ES2018 way</h4>
    <pre><code class="lang-javascript">const warriors = {steph: 95, kd: 97, klay: 82, dray: 79}
const newWarriors = Object.assign({}, warriors, {
  boogie: 86,
})</code></pre>

    <br />

    <strong>Node 8+ support! 😎</strong>
  </div>
</div>

NOTES:
- ES6/ES2015 gave us the ability to use spread operator in arrays & destructuring for objects
- Now we can "officially" use spread operator for objects
- _Explain code_
  * We copy objects while adding new properties in one object literal definition
  * ES2015 introduced `Object.assign()` but you have to make sure to have the empty object first


- You may be surprised that this just now becoming official
- We've had this for over a year in Node 8
- And I've been using this in React for over 2 years
- It had been in the proposal process for a while

/////
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">
    <h1><a href="http://2ality.com/2016/10/rest-spread-properties.html" target="_blank">Rest Properties</a></h1>
    <pre class="large"><code class="lang-javascript">const calcWins = (warriors) => {
  const {steph, kd, klay, dray, boogie, ...whoCares} = warriors
  // whoCares is an object with rest of warriors players
}</code></pre>

    <hr />

    <h4>Pre-ES2018 way</h4>
    <pre><code class="lang-javascript">const calcWins = (warriors) => {
  const {steph, kd, klay, dray, boogie} = warriors
  const whoCares = _.omit(warriors, ['steph', 'kd', 'klay', 'dray', 'boogie'])
}</code></pre>

    <br />

    <strong>Node 8+ support! 😎</strong>
  </div>
</div>

NOTES:
- Flip side of the coin is rest properties
- Rest operator with destructuring gives us the rest of players as an object
  * Could be empty
- ES6 allowed us to use destructuring to get out the players we cared about
- But had to use `_.omit` to get the rest

/////
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">
    <h1><a href="http://2ality.com/2016/10/rest-spread-properties.html" target="_blank">Rest Properties</a></h1>
    <pre class="large"><code class="lang-javascript">const calc = ({steph, kd, klay, dray, boogie, ...whoCares}) => {
  // whoCares is an object with rest of warriors players
}</code></pre>

    <br />

    <strong>Node 8+ support! 😎</strong>
  </div>
</div>


NOTES:
- Can take this one step further
- Move the whole destructuring + rest into the function header
- Just pass an object to `calc` function
- Named parameters!

/////
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <h1 style="font-size: 1.6em"><a href="http://2ality.com/2017/07/promise-prototype-finally.html" target="_blank"><code>Promise.prototype.finally</code></a></h1>
    <pre class="large"><code class="lang-javascript">let connection
db.open()
  .then((conn) => {
      connection = conn
      return connection.select({ name: 'Jane' })
  })
  .catch((() => { ... }))
  .finally(() => {
      connection.close()
  })</code></pre>

    <br />

    <strong>Node 10+ support! 😎</strong>
    <div class="code-highlight" style="height: 185px; top: 575px"></div>
  </div>
</div>

NOTES:
- One other feature
- There's now a 3rd method on `Promise` objects called `.finally()`
- It gets called no matter if things succeed or if there's an error
- Like with traditional `try`-`catch`-`finally` this is a great place to do clean up
- _Explain code_


- Actually works with Node 8 if you turn on a flag

/////
<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <h3>Do we really need <code>.finally()</code>??</h3>
    <pre class="large"><code class="lang-javascript">let connection
db.open()
  .then((conn) => {
      connection = conn
      return connection.select({ name: 'Jane' })
  })
  .catch((() => { ... }))
  .then(() => {
      connection.close()
  })</code></pre>

    <br />

    YES!
    <div class="code-highlight" style="height: 185px; top: 558px"></div>
  </div>
</div>

NOTES:
- How is this any different than sticking `.then()` on the end instead?
- There are 3 main differences:
  * If the `.catch()` threw an error, the last `.then()` wouldn't get called
  * If you didn't have a `.catch()` at all and there was an error, the last `.then()` wouldn't get called
  * `.finally()` passes the value from the last `.then()` through automatically **(go back)**

/////

<!-- .slide: data-background="url(../../img/esnext/ardian-lumi-364255-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>ES2018</h1>

    <ul style="margin-top:1em;margin-bottom:1em">
      <li><a href="http://2ality.com/2016/10/rest-spread-properties.html" target="_blank">Rest & Spread Properties</a></li>
      <li><a href="http://2ality.com/2017/07/promise-prototype-finally.html" target="_blank"><code>Promise.prototype.finally</code></a></li>
      <li><a href="http://2ality.com/2016/09/template-literal-revision.html" target="_blank">Template Literal Revision</a></li>
      <li><a href="http://2ality.com/2016/10/asynchronous-iteration.html" target="_blank">Asynchronous iteration</a></li>
      <li><a href="http://2ality.com/2017/05/regexp-named-capture-groups.html" target="_blank"><code>RegExp</code> named capture groups</a></li>
    </ul>

    <p><strong>Node 10+ support! 😎</strong></p>
  </div>
</div>

NOTES:
- Full list of features in ES2018
- The spec was just ratified earlier this month
- Folks are also pretty excited about async iteration and some of the regex improvements
  * Check out the links for more details

=====

<!-- .slide: data-background="url(../../img/esnext/joanna-kosinska-129039-unsplash.jpg) no-repeat center" data-background-size="cover" -->

# ECMAScript
# Proposal Process

NOTES:
- May be wondering how features get bundled in yearly releases?
- 4-stage process
- Features have to be in the final stage by February 1st of the release year
  * Basically the January TC39 meeting is when it is finalized
- Gets officially released in July
- ES2018 was just officially released

=====
<!-- .slide: data-background="url(../../img/esnext/liel-anapolsky-495646-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
	<div class="content-overlay" style="width: 40%">
  
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
- Work our way backwards
- Stage 4 is the final stage (`Finished`)
- Feature will be in the next release
  * A Stage 4 feature now would be in ES2019
- Specification is complete
- Has two compatible implementations which pass additional acceptance test suite
  * Feature can be in Node well before it's official like object rest/spread
- Spec is not expected to change except for wording edits to spec


- Let's take a look at one example...

/////
<!-- .slide: data-background="url(../../img/esnext/liel-anapolsky-495646-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 50%;">
    <h3>Handling exceptions 😔</h3>
    <pre class="large"><code class="lang-javascript">let jsonData

try {
  jsonData = JSON.parse(str)
} catch(ex) {
  jsonData = DEFAULT_DATA
}</code></pre>

    <br />

    I don't care about `ex`! 😫

    <div class="code-highlight" style="height: 70px; top: 382px"></div>
  </div>
</div>


NOTES:
- Have you ever written code like this with a `try`-`catch`?
- _Explain code_
- In the `catch`, you don't care about the exception
  * Either because it doesn't matter or you know what it is
- But we still have to provide a variable for it
  * Omitting `ex` is a syntax error!
- Unused variable lint rules have to make special concessions for this!

/////
<!-- .slide: data-background="url(../../img/esnext/liel-anapolsky-495646-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="http://2ality.com/2017/08/optional-catch-binding.html" target="_blank">Optional catch binding</a></h1>
    <pre class="large"><code class="lang-javascript">let jsonData

try {
  jsonData = JSON.parse(str)
} catch {
  jsonData = DEFAULT_DATA
}</code></pre>

    <br />

    <strong>Node 10+ support! 😎</strong>
    
    <div class="code-highlight" style="height: 70px; top: 453px"></div>
  </div>
</div>

NOTES:
- Now with **optional catch binding**, we don't need to specify `ex`
- Something that already exists in many other languages
- Already exists in Node 10!
- FUNNY: There's a whole Github issue bikeshedding on necessity of the proposal
  * One side: "it's not necessary always handle the error"
  * Other side: "it doesn't matter!"
  * Guess who won? My side!

=====
<!-- .slide: data-background="url(../../img/esnext/slim-emcee-ug-the-poet-truth_from_africa_photography-462985-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-start;">
	<div class="content-overlay" style="width: 40%;">
  
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
- Stage 3 (`Candidate`)
- Specification is considered complete
  * Spec will only change based upon implementations necessitating one
- Needs real-world implementations which pass additional acceptance test suite
- May be in ES2019, may not
  * Have until January 2019

- Let's look at some features...

/////
<!-- .slide: data-background="url(../../img/esnext/slim-emcee-ug-the-poet-truth_from_africa_photography-462985-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h3>Classes in JavaScript 😐</h3>
    <pre class="large"><code class="lang-javascript">class SelectField extends React.Component {
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
SelectField.propTypes = { ... }</code></pre>

    <div class="code-highlight fragment current-visible" style="height: 80px; top: 888px"></div>
    <div class="code-highlight fragment current-visible" style="height: 80px; top: 318px"></div>
    <div class="code-highlight fragment current-visible" style="height: 80px; top: 493px"></div>
  </div>
</div>


NOTES:
- ES2015 introduced class syntax in JavaScript
  * Great start, but lacked some important qualities
  * Fixed w/ a few Stage 3 features
- Here's a React component written using a JS class in ES2015
- **First:** Static `propTypes` added to the class afterwards
- **Second:** Declaring a instance field called `state` w/in the `constructor()`
- **Third:** Declaring a "private" method called `_getOptions()`
  * Not truly private, just a convention. Still accessible
  * Can make things private using `Symbol` or `WeakMap` but are verbose/convoluted
- With 3 new Stage 3 proposals we can make this more legit!

/////
<!-- .slide: data-background="url(../../img/esnext/slim-emcee-ug-the-poet-truth_from_africa_photography-462985-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="https://github.com/tc39/proposal-static-class-features/" target="_blank">Static class features</a></h1>
    <pre class="large"><code class="lang-javascript">class SelectField extends React.Component {
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
}</code></pre>

    <div class="code-highlight" style="height: 80px; top: 276px"></div>
  </div>
</div>

NOTES:
- First we can bring that static declaration from outside the class to inside
- We use the `static` keyword for the field
- ES2015 had `static` methods, but now this proposal adds static fields
- Highly likely you've been using `static` for React `propTypes`
- We've been using this feature since it was introduced at Stage 1 two years ago!


- We can go further! What about the `state` declaration?

/////
<!-- .slide: data-background="url(../../img/esnext/slim-emcee-ug-the-poet-truth_from_africa_photography-462985-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="http://2ality.com/2017/07/class-fields.html" target="_blank">Class fields</a></h1>
    <pre class="large"><code class="lang-javascript">class SelectField extends React.Component {
  static propTypes = { ... }

  state = { ... }

  _getOptions() { ... }

  render() {
    const options = this._getOptions()
    ...
  }
}</code></pre>

    <div class="code-highlight" style="height: 80px; top: 390px"></div>
  </div>
</div>

NOTES:
- Next, we can move that `state` declaration/initialization outside of the `constructor`
  * In fact we don't need the `constructor` at all now!
- It makes the `class` more declarative too 
  * We can see all of the properties it defines
  * Instead of having to hunt w/in the `constructor` or other methods
- FYI these class fields get initialized **before** the `constructor` is run
- ES2015 intoduced instance methods; now we have fields
- Probably have seen/used this before too


- The class is looking really nice, but we can do even more!
- `_getOptions` is only "private" by convention

/////
<!-- .slide: data-background="url(../../img/esnext/slim-emcee-ug-the-poet-truth_from_africa_photography-462985-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="https://github.com/tc39/proposal-private-methods" target="_blank">Private methods</a></h1>
    <pre class="large"><code class="lang-javascript">class SelectField extends React.Component {
  static propTypes = { ... }

  state = { ... }

  #getOptions() { ... }

  render() {
    const options = this.#getOptions()
    ...
  }
}</code></pre>

    <div class="code-highlight" style="height: 80px; top: 505px"></div>
    <div class="code-highlight fragment current-visible" style="height: 80px; top: 675px"></div>
  </div>
</div>


NOTES:
- Beware you might feel some kind of way about this feature


- Lastly, we can use the `#` to signal that the `getOptions` method is private
  * No longer need to complain in code reviews about testing private
- It can no longer be accessed outside of the class; truly private
- **NOTE:** You can make fields private too; even `static` & private


- This syntax is pretty controversial; especially those who use TypeScript
- Maybe wondering why using `#` instead of `private` keyword
  * Read explanations and I _think_ it boils down to how these private fields/methods are implemented
  * Private fields/methods are implemented a special way
  * **Highlight:** The `#` in `this.#getOptions` helps the interpreter know where to find the data

=====
<!-- .slide: data-background="url(../../img/esnext/sergei-gavrilov-528341-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-start">
	<div class="content-overlay" style="width: 40%;">
  
    <h1>Stage 2</h1>
    <h2>(Draft)</h2>

    <ul style="margin-top: 2em">
      <li>Formalize the specification</li>
      <li><em>Should</em> eventually release</li>
    </ul>
  
  </div>
</div>

NOTES:
- Let's keep working backwards...
- Stage 2 (`Draft`)
- Committee expects the feature to be developed and eventually included
  * not guaranteed
- There's a _rough_ spec entering into this stage
- Objective is to formalize the spec
- There should really only be incremental changes to the spec
- Still a gamble to use
- There's nothing sitting at Stage 2 that I really am excited about
- There are Class Decorators, but I'm not a big fan of those, yet
  * I lean more functional

=====
<!-- .slide: data-background="url(../../img/esnext/kunj-parekh-362219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
	<div class="content-overlay" style="width: 40%;">
  
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
- Let's jump to Stage 1 (`Proposal`)
  * The beginning stage
- Has a "champion"
  * Text outlining the problem & potential solution
  * Example usages & high-level API
  * Discussion of implementation challenges
  * Committee expects to devote time
- Make the case for the addition
- **HUGE** gamble to use
  * Spec can change drastically as its being formalized
- But there are some fun ones here

- Let's look at one...

/////
<!-- .slide: data-background="url(../../img/esnext/kunj-parekh-362219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <h3>Conditional property accessing 😔</h3>
    <pre class="large"><code class="lang-javascript">const address = user.address</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const address = user && user.address</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const address = (user || {}).address</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const address = user ? user.address : undefined</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const address = user != null ? user.address : undefined</code></pre>
  </div>
</div>

NOTES:
- In JS we can access properties simply
- But what happens if `user` may be `null` or `undefined`?
- You have to check it first
- There are several ways we can do this
  * **CLICK THROUGH**

/////
<!-- .slide: data-background="url(../../img/esnext/kunj-parekh-362219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <h3>Conditional deep property accessing 😭</h3>
    <pre class="large"><code class="lang-javascript">const street = user.address.street</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const street = user && user.address && user.address.street</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const street = ((user || {}).address || {}).street</code></pre>
    <pre class="large fragment"><code class="lang-javascript">const street = user 
  ? (user.address ? user.address.street : undefined)
  : undefined</code></pre>
  </div>
</div>

NOTES:
- And what if you have to go multiple levels deep?
- It gets even more gnarly
  * **CLICK THROUGH**

/////
<!-- .slide: data-background="url(../../img/esnext/kunj-parekh-362219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="https://github.com/tc39/proposal-optional-chaining" target="_blank">Optional chaining</a></h1>
    
    After
    <pre class="large"><code class="lang-javascript">const address = user?.address</code></pre>
    Before
    <pre><code class="lang-javascript">const address = user != null ? user.address : undefined</code></pre>
    
    <br />

    After
    <pre class="large"><code class="lang-javascript">const street = user?.address?.street</code></pre>
    Before
    <pre><code class="lang-javascript">const street = user && user.address && user.address.street</code></pre>
  </div>
</div>

NOTES:
- The optional chaining operator is: `?.`
- If the expression before it is `undefined`/`null`
  * Short-circuit and return that
  * Otherwise it'll return whatever is after
  * Much like a ternary
- Recently learned that this originated in CoffeeScript

/////
<!-- .slide: data-background="url(../../img/esnext/kunj-parekh-362219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <h1><a href="https://github.com/tc39/proposal-optional-chaining" target="_blank">Optional chaining</a></h1>
    
    After
    <pre class="large"><code class="lang-javascript">user?.update()</code></pre>
    Before
    <pre><code class="lang-javascript">user && user.update()</code></pre>
    
    <br />

    After
    <pre class="large"><code class="lang-javascript">update?.()</code></pre>
    Before
    <pre><code class="lang-javascript">update && update()</code></pre>
  </div>
</div>


NOTES:
- Can also use the optional chaining operator with functions!
- Check to see if the object exists and if it does call the expected method
- If you just have a function reference you can check before calling it!

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
- Decorators were stage 0 after ES2015
  * So many folks were burned cuz spec changed
- Don't even really wanna show any
- None were really interesting...
- Some have been here since 2014!

=====
<!-- .slide: data-background="url(../../img/esnext/clement-h-544786-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 50%;">

    <h1>Using it now</h1>

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
  </div>
</div>

NOTES:
- The way to use features now before they are standard is w/ transpilers
- Generally safe to use Stage 3 & higher
- TypeScript tends to **only** support Stage 3 and higher because the specs won't change*
- Babel is more configurable with presets & plugins that allow you to use features down to Stage 0
  * At your own risk

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">Quick Recap</h1>
  </div>
</div>

NOTES:
- Let's quickly recap of the features we discussed

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 95%;">
    <a href="http://2ality.com/2016/10/rest-spread-properties.html" target="_blank">Rest & Spread Properties</a> (ES2018)
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">const warriors = {steph: 95, kd: 97, klay: 82, dray: 79}
const newWarriors = {...warriors, boogie: 86}
const {steph, kd, klay, dray, boogie, ...whoCares} = warriors</code></pre>


    <a href="http://2ality.com/2017/07/promise-prototype-finally.html" target="_blank"><code>Promise.prototype.finally</code></a> (ES2018)
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">db.open()
  .then(() => { ... })
  .catch(() => { ... })
  .finally(() => { ... })</code></pre>


    <a href="http://2ality.com/2017/08/optional-catch-binding.html" target="_blank">Optional catch binding</a> (ES2019)
    <pre class="large"><code class="lang-javascript">try { ... }
catch { ... }</code></pre>
  </div>
</div>

NOTES:
- These three features are available in Node 10+ right now!
  * Can use in Production once Node 10 is LTS in October

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <a href="https://github.com/tc39/proposal-static-class-features/" target="_blank">Static class features</a> (Stage 3)<br />
    <a href="http://2ality.com/2017/07/class-fields.html" target="_blank">Class fields</a> (Stage 3)<br />
    <a href="https://github.com/tc39/proposal-private-methods" target="_blank">Private methods</a> (Stage 3)
    <pre class="large"><code class="lang-javascript">class SelectField extends React.Component {
  static propTypes = { ... }

  state = { ... }

  #getOptions() { ... }

  render() {
    const options = this.#getOptions()
    ...
  }
}</code></pre>
  </div>
</div>

NOTES:
- Talked about 3 features affecting classes
- Pretty sure the class features will be available in next Node major version
  * Already exist in Chrome

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 60%;">
    <a href="https://github.com/tc39/proposal-optional-chaining" target="_blank">Optional chaining</a> (Stage 1)
    <pre class="large"><code class="lang-javascript">const address = user?.address

const street = user?.address?.street

user?.update()

update?.()</code></pre>
  </div>
</div>

NOTES:
- 7th and final feature
  * Likely a ways away
  * Probably my favorite

=====
<!-- .slide: data-background="url(../../img/esnext/anna-demianenko-12400-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 45%" class="content-overlay">
  
  <h1>Resources</h1>

  <ul style="margin-top: 2em">
    <li><a href="https://github.com/tc39/ecma262" target="_blank">ECMAScript Github Repo</a></li>
    <li><a href="http://kangax.github.io/compat-table/es2016plus/" target="_blank">ES2016+ Compatibility Table</a></li>
    <li><a href="http://kangax.github.io/compat-table/esnext/" target="_blank">ES.next Compatibility Table</a></li>
    <li><a href="https://tc39.github.io/ecma262/" target="_blank">ECMAScript Living Spec</a></li>
    <li><a href="https://tc39.github.io/process-document/" target="_blank">TC39 Proposal Process</a></li>
    <li><a href="https://github.com/rwaldron/tc39-notes" target="_blank">TC39 Meeting Notes</a></li>
    <li><a href="https://github.com/tc39/test262" target="_blank">ECMAScript Test Suite</a></li>
  </ul>
  
  
  </div>
</div>

NOTES:
- Lots of resources for ya

=====
<!-- .slide: data-background="url(../../img/webdev/matt-jones-42954-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 40%" class="content-overlay">
  
  <h1>Ben Ilegbodu</h1>

  <p><a href="/" target="_blank">benmvp.com</a> | <a href="https://twitter.com/benmvp" target="_blank">@benmvp</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  <br />

  <p>Ask me anything!<br /><a href="http://www.benmvp.com/ama/" target="_blank">benmvp.com/ama</a></p>
  
  </div>
</div>

NOTES:
- So that's it!
- Wanna thank **conference** and **YOU!**
- Ask questions on Twitter, via email or AMA!
- Thanks!
