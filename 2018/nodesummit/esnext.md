# ES.next features that'll make ya 💃🕺🏾

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#NodeSummit](https://twitter.com/hashtag/NodeSummit)  

<br />

July 24, 2018

NOTES:
- ES.next is just future JavaScript

=====

# Recap

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

- [`async` / `await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
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

# ES.next

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 10px; color: white; font-size: 5em" -->

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
  "role": "Principal UI Engineer",
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

# ES.next

=====

# ES2018

/////

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

[Spread Properties](http://2ality.com/2016/10/rest-spread-properties.html) (Stage 3)

**Node 8+ support! 😎**

NOTES:
- Now we copy objects while adding new properties in one object literal definition
- It's a Stage 3 ES feature
- The ES5 way was to use `_.assign()`
- ES6 did introduce Object.assign() to handle this as well, but I'll always prefer syntax

/////

Object destructuring + rest operator!

```js
export default class TextInput extends Component {
    render() {
        let {type, defaultValue, ...inputProps} = this.props
        // `inputProps` has everything in `this.props`
        // except `type` & `defaultValue`

        /* render stuff */
    }
}
```
<!-- .element: class="large" -->

[Rest Properties](http://2ality.com/2016/10/rest-spread-properties.html)

**Node 8+ support! 😎**

NOTES:
- Rest properties are coming in soon to ECMAScript. They're in Stage 3
- Not in ES2015, not ES2016, but future JavaScript (maybe ES2017)

/////

[`Promise.prototype.finally`](http://2ality.com/2017/07/promise-prototype-finally.html)

**No Node support yet 😔**

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

**Most Node 10+ support 😐**

NOTES:
- Remaining features in ES2018
- The spec was just finalized 2 weeks ago

=====

# 4-stage process

NOTES:
- May be wondering how features get bundled in yearly releases
- 4-stage process
- Features have to be in the final stage by February 1st of the release year
- Basically the January meeting of the year is when it is finalized
- Gets released in July
- ES2018 was just officially released

=====

# Stage 4 (Finished)
## (ES2019)

NOTES:
- Feature will be in the next release
- Specification is complete
- Has two compatible implementations which pass additional acceptance test suite
- Has significant in-the-field experience with **shipping** implementations, such as that provided by two independent VMs
- Spec is not expected to change except for wording edits to spec

/////

[Optional catch binding](http://2ality.com/2017/08/optional-catch-binding.html)

=====

# Stage 3 (Candidate)

NOTES:
- Specification is considered complete
- Spec will only change based upon implementations necessitating one
- Should be safe to use
- Needs real-world implementations which pass additional acceptance test suite
- May be in ES2019, may not
- Object rest/spread sat in Stage 3 for nearly 2 years

/////

- [Class fields](http://2ality.com/2017/07/class-fields.html)
- [Private methods](https://github.com/tc39/proposal-private-methods)
- [Static fields & private static methods](https://github.com/tc39/proposal-static-class-features/)

=====

# Stage 2 (Draft)

NOTES:
- Committee expects the feature to be developed and eventually included in the standard (not guaranteed)
- There's a _rough_ spec coming in
- Objective is to formalize the spec
- There should really only be incremental changes to the spec
- Still a gamble to use

/////

[Decorators](https://github.com/tc39/proposal-decorators)

NOTES:
- Not a fan, but folks seem to like them
- Been languishing for a while, not sure what the hold up is

=====

# Stage 1 (Proposal)

NOTES:
- Has a "champion"
- Text outlining the problem & potential solution
- Example usages & high-level API
- Discussion of implementation challenges
- Committee expects to devote time to examining the problem space, solutions and cross-cutting concerns
- Make the case for the addition
- Describe the shape of a solution
- Identify potential challenge
- Spec can change drastically as its being formalized
- **HUGE** gamble to use
- There are some fun ones here

/////

[Optional chaining](https://github.com/tc39/proposal-optional-chaining)

/////

[Temporal (DateTime) object](https://github.com/tc39/proposal-temporal/blob/master/README.md)

/////

[Pipeline operator](https://github.com/tc39/proposal-pipeline-operator)

=====

# [Stage 0 (Strawman)](https://github.com/tc39/proposals/blob/master/stage-0-proposals.md)

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

# Using it now

/////

[TypeScript Node Starter Kit](https://github.com/Microsoft/TypeScript-Node-Starter#typescript--node)

=====

## Resources

- [ES2016+ Compatibility Table](http://kangax.github.io/compat-table/es2016plus/)
- [ES.next Compatibility Table](http://kangax.github.io/compat-table/esnext/)
- [ECMAScript Living Spec](https://tc39.github.io/ecma262/)
- [ECMAScript Github Repo](https://github.com/tc39/ecma262)
- [TC39 Proposal Process](https://tc39.github.io/process-document/)
- [TC39 Meeting Notes](https://github.com/rwaldron/tc39-notes)
- [ECMAScript Test Suite](https://github.com/tc39/test262)

=====

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
