# Why React?

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#reactathon](https://twitter.com/hashtag/reactathon)  

<br />

March 20, 2018  

NOTES:
- My name is Ben Ilegbodu
- Excited to be kicking of Reactathon and the Fundamentals conference
- Wanna introduce you to React and intro many of the concepts you will hear today

- It was nearly 2 years ago that we (Eventbrite) embarked on the journey of transitioning our frontend from Backbone to React
- So I wanna talk about the first part of that transition: convincing everyone that it was a good idea 😀
- Gonna pull back the covers on the rationales we used to make that switch
- And in doing so introduce you to how React works

- Posted link to slides on twitter if you want to follow along

=====

## What this talk is **not** about... 😞

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<img src="../../img/giphy/dawson-creek-crying.gif" style="width:100%;height:auto" alt="Dawson's Creek crying" />
	</div>
	<div style="flex:0 0 50%;">
		<ul>
      <li>React tutorial</li>
      <li>React is better than <span>X</span></li>
      <li>React 💕 fest</li>
    </li>
	</div>
</div>

NOTES:
- Quick heads up
- The goal of this talk is not to teach you React, so you can go off and build the next app that's gonna change the game
- Even if I wanted to, not possible in an hour
- Had a full day workshop yesterday
- Also not gonna be framework bashing; talking about how React is better than Angular or Vue or Ember
- Although I am basically saying it's better than Backbone since we switched
- Lastly, gonna try to not make this a React love-fest

/////

## What this talk is about! 😄

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<ul>
      <li>Rationales explained in code</li>
      <li>Tradeoffs</li>
    </li>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/giphy/brad-pitt-dancing.gif" style="width:100%;height:auto" alt="Brad Pitt dancing" />
	</div>
</div>

NOTES:
- There's no perfect framework; there are trade-offs and I'll try to point them out
- So hopefully if you're still investigating, you'll get a somewhat balanced opinion
- Wanna walk through the many reasons why we made the switch
- But not just talk about; I want to demonstrate it w/ a lil' code

=====

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

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I'm a Principal Frontend Engineer on our Frontend Platform team
- We don't work on end-user features, but building the frontend platform that other devs build on
  top of
- Two main objectives: frontend infrastructure & component library

/////

<!-- .slide: data-background="url(../../img/giphy/james-harden-wesley-johnson-ankles.gif) no-repeat center" data-background-size="contain"-->

=====

# CORE STUFF
<!-- .element: class="title" -->

NOTES:
- Split this up into 2 main sections:
- Core Stuff & More STuff
- Core ones will apply to everyone using React
- Part of the core React lib

=====
<!-- .slide: data-background="#ddd" -->

# 1. Declarative JSX

![Denzel Washington shouting](../../img/giphy/shouting-denzel-washington.gif)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 60%" -->

NOTES:
- The first reason why we wanted to migrate from Backbone to React was its Declarative JSX

/////

## JSX

```js
<div>
  <span className="val">{this.state.value}</span>
  <button onClick={this._handleClick}>+</button>
</div>
```
<!-- .element: class="large" -->

NOTES:
- Here is some JSX
- Got a `<div>` wrapping a `<span>` display and a `<button>`
- Looks much like HTML and lives right w/in our JavaScript
- Many people didn't like the syntax at first
- But I find it very approachable
- What you may not realize is that this JSX gets converted into JavaScript

/////

## Transpiled JSX

```js
React.createElement(
  'div',
  null,
  React.createElement('span', {className: 'val'}, value),
  React.createElement('button', {onClick: this._handleClick}, '+'),
)
```
<!-- .element: class="large" -->

([Babel REPL](https://babeljs.io/repl/))

NOTES:
- Here it is transpiled; it's just JavaScript ultimately
- Thanks to the power of build tooling (aka Babel)
- We can write our code in friendly JSX
- But out comes normal JS
- I couldn't imagine building my React components like this

/////

## Collocated markup, logic & data

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Here's the JSX in the context of a full component
- We'll go into the details of what the component does in following sections
- With React, a component contains...
  - Markup (`render()`)
  - Data (`this.props` & `this.state`)
  - Logic (`_handleClick`)
- You can also include styling too, but not trying to start a flamewar over css-in-js right now
- So everything is collocated, which was very different than traditional MVC like Backbone

/////

## Logic in the template (markup-driven)

```html
<select>
  {{#each values}}
    {{option_value}}
  {{/each}}
</select>
```
<!-- .element: class="large" -->

```js
Handlebars.registerHelper('option_value', function() {
  if (shouldShow(this)) {
    return new Handlebars.SafeString(
      '<option value="' + this.value + '">'
        + this.display + '</option>'
    )
  }
})
```
<!-- .element: class="large" -->

NOTES:
- Traditional UI frameworks, like Backbone, are markup-driven
- Doing any kind of fancy logic in these templates can get really, really messy
- Plus we'd basically have to basically learn a new language
- At Eventbrite we registered Handlebars "helpers" so we could call functions in templates
- _explain what is happening_
- Alternative is to do a whole lot of pre-computation in the view to enable the template to be dumb
- Ya know, Handlebars doesn't support compound conditionals
- So you can't do `if` this `or` that` w/o writing a custom helper

/////

## Logic in React Component (logic-driven)

```js
class Selector extends React.Component {
  render() {
    const options = this.props.values.map((info) => {
      if (this._shouldShow(info)) {
        return (
          <option key={info.value} value={info.value}>
            {info.display}
          </option>
        )
      }
    })

    return (<select>{options}</select>)
  }
}
```
<!-- .element: class="large" -->

NOTES:
- But with React, since our markup is in JavaScript, the logic is in JS
- It's a little... different; not initially intuitive at first glance
- You see... _explain how it works_
- Backbone UI is template-driven, markup was primary and sprinkled in a little logic
- But React is reverse: logic is primary w/ JS and sprinkle in some markup
- We have the full use of JavaScript at our dispoable to build up the JSX to return
- Comes in handy

/////

[![Dan Abramov's tweet about no special JSX API for loops/conditionals](../../img/why-react/dan-abramov-jsx-tweet.png)](https://twitter.com/dan_abramov/status/929136989085093890)

(...but [StackOverflow](https://stackoverflow.com/questions/22876978/loop-inside-react-jsx) 😞)

NOTES:
- Dan tweeted this in response to a request to add conditionals and loops into JSX
- I ❤️ JavaScript so the more I can do in JS the better
- I'm glad that I don't have to learn a new API to do conditionals/loops in React
- Because it's JS, I can do whatever JS can do
- But for some though, this is a drawback because you _have_ to know JS pretty well to be effective
- Before if you were solid at HTML/CSS, you could throw in some jQuery & do really well
- Looping and conditionals in JSX is not intuitive
- That's a StackOveflow question about loops that has > 300k views and 520 upvotes!
- Now it's JS or bust, which takes some getting used to

/////

## JSX is not HTML!

```
class Label extends React.Component {
  render() {
    return (
      <label className="is-hidden" htmlFor={this.props.inputId}>
        {this.props.children}
      </label>
    )
  }
}
```

<!-- .element: class="large" style="margin-bottom: 1em" -->

React JSX props mirror HTML DOM properties!

```
let labelNode = document.getElementById('label')
labelNode.className = 'is-hidden'
labelNode.htmlFor = this.props.inputId
```
<!-- .element: class="large" -->

NOTES:
- One other thing, is that although JSX looks like HTML, it's not
- We're creating a custom `<Label>` component
- The `className` & `htmlFor` props should make it clear that this isn't HTML
- React chose to mirror the JS DOM API for its props which are all camelCase
- And that's why its `className` & `htmlFor` instead of the HTML `class` & `for`
- It's also why it's `onClick`, `onChange`, etc.
- React is pretty good at giving great warnings if you forget or mess up
- Especially with React 16

/////

![Jay Phelps](../../img/reactathon/jay-phelps.png)  <!-- .element: style="width: 500px" -->  
Jay Phelps

<br />

## Why I love JSX!

(Coming up next!)

NOTES:
- So that's a brief overview of JSX
- There's so much more I'd like to cover
- But luckily Jay is going to go more into JSX in his talk "Why I love JSX"
- He's pretty pumped about it. It's got an exclamation point!

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/russian-nesting-doll-trick.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Trick with Russian nesting dolls" />
    </div>
    <div>
      <h1>2. Component-driven</h1>
    </div>
</div>

NOTES:
- The next motivation for the transition was React's component-based architecture

/////

## Everything is a component!

```js
class FormField extends React.Component {
  render() {
    const name = this.props.name
    return (
      <div>
        <Label inputId={name}>{this.props.label}</Label>
        <TextInput
          id={name}
          value={this.props.value}
          onChange={this.props.onChange}
        />
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- The sole way you build your UI in React is with "custom" components
- Everything is a component!
- And you build bigger components by combining smaller components w/ markup
- One way we create components is by creating a `class` and extending from `React.Component`
- The component has a `render()` method which is where you define the UI & return JSX
- Here we have a `FormField` component made up of existing `Label` & `TextInput` components
- It defines 4 `props` (`name`, `label`, `value` & `onChange`), which are how the component is configured
- It lays out the `Label` & `TextInput` w/in `<div>` and then passes along those props as configuration

/////

## Everything is a component!

```js
import FormField from './FormField'
class NameForm extends React.Component {
  render() {
    return (
      <form onSubmit={this._handleSubmit}>
        <FormField
          name="fName"
          label="First"
          value={this.props.fields.first}
          onChange={this._handleFieldChange.bind(null, 'fName')}
        />
        <FormField name="lName" ... />
      </form>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- We include the component by importing it and then using it in `render()` like an HTML tag
- And we configure the props by passing them in via attributes, just like HTML
- Although we're in Javascript using JSX, the HTML-like syntax should feel familiar
- Then you can combine one or more `FormField` components to create a bigger `Form` component
- And keep doing that until you have a full-fledged app

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div>
      <h1>3. All JavaScript*</h1>
    </div>
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/throwing-packages.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Employee throwing packages" />
    </div>
</div>

NOTES:
- The 3rd reason was React being exclusively JavaScript based
- I have the asterisk there because obviously we're building web apps so CSS is obviously involved
- But I'm conveniently ignoring that for now 😀

/////

```
class Section extends React.Component {
  render() {
    const headingText = this.props.headingText
    let headingElem

    if (headingText) {
      headingElem = (<h1>{headingText}</h1>)
    }

    return (
      <section className="section">
        {headingElem}
        <p>{this.props.children}</p>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 80px; top: 43px"></div>

NOTES:
- The nice thing about React, the JavaScript UI lib, tying itself to JavaScript instead of its own API is that as JavaScript evolves, it auto-evolves
- You probably already noticed that we were using `class` keyword to create our React components
- That's ES6 and it's become standard way of creating React components
- I showed `import` w/ `FormField` which is the way of including other components & dependencies (also ES6)
- This `Section` component _[describe what it does]_
- But we can take this class-based component and...

/////

## React + ES.next = ❤️

```
const Section = ({headingText, children}) => {
  let headingElem

  if (headingText) {
    headingElem = (<h1>{headingText}</h1>)
  }

  return (
    <section className="section">
      {headingElem}
      <p>{children}</p>
    </section>
  )
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 80px; top: 133px"></div>

NOTES:
- ...rewrite it using the latest JavaScript
- React components can also be written as functions of their props
- Here we're using an arrow function instead of a standard function
- And we're immediately destructuring the props into `headerText` & `children`
- There's plenty more we can do too with new JS features in React

/////

## Gotta have a (modern) build system

<div style="display:flex;align-items:flex-end;justify-content:space-around;margin: 2em 0">
	<div style="flex:0 0 22%;">
        <a href="https://babeljs.io/"><img
            src="../../img/es6/babel-logo.png"
            style="background:none;box-shadow:none;border:none;"
        /></a>
		<a href="https://babeljs.io/">Babel</a>
  </div>
	<div style="flex:0 0 22%;">
        <a href="https://webpack.github.io/"><img
            src="../../img/nav-react/webpack-logo.png"
            style="background:none;box-shadow:none;border:none;"
        /></a>
		<a href="https://webpack.github.io/">Webpack</a>
  </div>
	<div style="flex:0 0 22%;">
        <a href="https://www.typescriptlang.org/"><img
            src="../../img/nav-react/typescript-logo.png"
            style="background:none;box-shadow:none;border:none;"
        /></a>
		<a href="https://www.typescriptlang.org/">TypeScript</a>
  </div>
	<div style="flex:0 0 22%;">
        <a href="http://rollupjs.org/"><img
            src="../../img/nav-react/rollup-logo.svg"
            style="background:none;box-shadow:none;border:none;"
        /></a>
		<a href="http://rollupjs.org/">Rollup</a>
  </div>
</div>

Enable fun features like [tree-shaking](https://webpack.js.org/guides/tree-shaking/) &
[code splitting](https://webpack.js.org/guides/code-splitting/)!

NOTES:
- But all this goodness comes at a cost
- We basically are **forced** to have a modern build system that we must configure
- And that's where some combo of Babel, Webpack, TypeScript, Rollup, etc. come in
- I'm actually working on a project that uses all 4 of these
- Frontend Platform team just wrapped up a transition from requirejs to Webpack 3
- And now Webpack 4 is out!
- Chances are for any modern production apps you already had _some_ sort of build system
- Compile SASS -> CSS, minify & bundle JS, CoffeeScript, etc so not end of the world
- And by paying the upfront cost of the build system, it enables cool features: tree-shaking & code splitting

/////

## Create React App

Create React apps with no build configuration

```
$> npx create-react-app my-app

$> cd my-app

$> yarn start
```

<!-- .element: class="large" style="margin:5% 0" -->

Configures Babel, Webpack 3, ESLint, and more!

([`npx`](https://github.com/zkat/npx))

NOTES:
- Thankfully though, you don't have to roll your own build system w/ React; at least not initially
- Create React App is a tool that let's you bootstrap an app to start React-ing quickly
- Run these commands and you'll have an app that does all of the Frontend DevOps for you!
- `npx` is a new tool from NPM that allows you to easily/quickly run a global CLI tool...

/////

## [React + ES.next = ♥](http://www.benmvp.com/slides/2017/reactconf/react-esnext.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/jh_Qzi-yHU0" frameborder="0" allowfullscreen></iframe>

### ReactConf 2017

NOTES:
- Shameless plug alert!
- I gave a talk called _React + ES.next = ♥_ at React Conf back in March
- I go through a handful of ES.next features that go great with React
- So if some of the features I was talking about didn't quite make sense, check it out!

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/success.gif" style="width:75%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="" />
    </div>
    <div>
      <h1>4. State-driven</h1>
    </div>
</div>

NOTES:
- So far we've talked about (1) JSX, (2) Component-driven & (3) JavaScript
- And so far we've basically been creating static user-interfaces; not user interaction
- To do that the state of the UI has to change over time
- So React components are state-driven instead event-driven, which is more familiar
- This is the hardest thing to wrap your head around if you're new to React
- It's just a different way of building UIs
- But I've found it to be very compelling
- And this is the 4th motivator for the transition away from Backbone to React

/////

## Event-driven jQuery

```html
<div>
  <span class="val">0</span>
  <button class="btnUp">+</button>
</div>
```
<!-- .element: class="large" -->

```js
$('.btnUp').click(function() {
  var $val = $('.val'),
      currentValue = parseInt($val.html(), 10)

  $val.html(currentValue + 1)
})
```
<!-- .element: class="large" -->

<div>
	<span class="val" style="font-size: 2em;text-align: center;margin: 0 1em">0</span>
	<button class="btnUp" style="font-size: 2em" onclick="$('.val').html(+$('.val').html() + 1)">&nbsp;&nbsp;+&nbsp;&nbsp;</button>
</div>

NOTES:
- Here's some event-driven jQuery code that should be pretty familiar
- Click a button and update `<span>`
- The driver is the event
- This is _really_ easy to follow (imperative), but as app grows in complexity, code turns into crazy spaghetti

/////

## State-driven React

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 80px; top: 197px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 650px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 704px"></div>
<div class="code-highlight fragment current-visible" style="height: 190px; top: 313px"></div>

NOTES:
_click through code highlights_

- Contrast this with the React code equivalent
- Simplest example of reactivity in React
- Explanation of code...
- It's the handler that does the logic of incrementing the value; separation of concerns!
- And since `value` is already in `state` we don't have to get it from the DOM
- Then calling `setState` causes `render` to be called again
- Click again and the cycle continues
- In the old world `_handleClick` would've directly manipulated the DOM
- But instead we update the state and that will indirectly update the DOM
- Layer of indirection is hard to wrap head around

/////

## React dev work can be boiled down to...

1. `render()` based on `props` & `state`
1. `onEvent` transform data → `setState()`
1. Profit 🎉

<!-- .element: style="font-size: 1.5em; margin-top: 1.5em" -->

NOTES:
- So basically we do work in two main areas:
- 1/ Define what we're going to `render()` based on `props` & `state`
- Can have conditional logic, loops, other sophisticated logic to determine what to render
- Skill: Ability to build layouts with HTML & CSS
- 2/ When events happen, do stuff to transform data to generate new `state` (and `render` again)
- Can also do async transformation by making API calls
- Skill: Ability to transform data efficiently; algorithms are really handy
- And the loop continues

/////

[![Dan Abramov's tweet about how React code remains understandable as app gets more complex](../../img/why-react/dan-abramov-reactive-tweet.png)](https://twitter.com/dan_abramov/status/930380316463726593)

NOTES:
- When folks look at simple examples of "reactivity" in React, they find it to be too verbose; and it is
- But with React trades conciseness for predictability
- So you end up spending more time explicitly wiring things up together
- Buuuut... structure of your code can more or less stay the same as complexity grows
- Certainly not the case with jQuery or Backbone; things got cray
- So if an app grew organically, it never was rearchitected
- But prepare yourself for the fact that it'll feel like you're writing "more code" in the beginning

/////

![Feather Knee](../../img/reactathon/feather-knee.png)  <!-- .element: style="width: 500px" -->  
Feather Knee

<br />

## From Imperative to Declarative

(Right after Jay!)

NOTES:
- That was suuuper quick overview of how reactivity in React works in a declarative way
- It's really the crux of how React works
- It's also probably the biggest mental shift when developing in React
- Luckily Feather's gonna go into way more detail about how it all works
- And she's speaking right after Jay! You'd think this was planned or something!

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div>
      <h1>5. Sophisticated reconciler</h1>
      <h2>(aka Virtual DOM)</h2>
    </div>
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/shia-magic.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Shia displays magic" />
    </div>
</div>

NOTES:
- Let's talk about our 5th reason for the transition:
- The killer feature of React: the Reconciler aka Virtual DOM
- Whenever anyone talks about React it's the cool feature they talk about
- Technically "Virtual DOM" is a misnomer


- So up until this point, it's looked like `render()` was rendering to the DOM
- But it's not...

/////

## React reconciler makes efficient updates easy 💯

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 240px; top: 595px"></div>

NOTES:
- Let's take our example from before...
- When we call `setState` React calls `render()` w/ updated state
- So it looks like are re-rendering the `<div>` + children each time
- When we know all we _really_ are updating is _just_ the `innerHTML` of `<span>`
- `render()` is **not** updating DOM, but building up element hierarchy
- Basically a _new_ virtual representation of the DOM
- The reconciler (aka "Virtual DOM") keeps a copy of DOM, compares w/ newly rendered DOM and only
  updates changes
- So we don't have to do the hard work of figuring out how to make the "micro updates"
- We can just write our code the easy way: like it re-renders everything
- And React does the hard work of figuring out micro updates
- This is _really_ _really_ nice

/////

## Lin Clark - A Cartoon Intro to Fiber

<iframe width="1333" height="750" src="https://www.youtube.com/embed/ZCuYPiUIONs" frameborder="0" allowfullscreen></iframe>

### React Conf 2017

NOTES:
- React has a brand new reconciler called the "Fiber reconciler" which is opening up the door to even more sophistication
- Lin did an amazing job at last year's React Conference explaining what it is and how it all works
- Highly suggest you check that out later!

=====

# MORE STUFF
<!-- .element: class="title" -->

NOTES:
- So those were the Core Motivations
- The ones that will apply to everyone because they are part of the core lib
- Before we jump into Additional motivations, let's pause
- Everyone yell out the most recent JS lib/framework they used (jQuery, React, Vue, etc)


- Now let's jump into some additional motivations
- They applied to us at Eventbrite, but _may_ not apply to your situation

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/homer-pours-water-on-servers.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Homer pours water all over servers" />
    </div>
    <div>
      <h1>6. Server-side rendering</h1>
      <h2>(aka "Isomorphic React")</h2>
    </div>
</div>

NOTES:
- Let's talk about the 6th reason: server-side rendering or "Isomorphic React"
- "Isomorphic JavaScript" or "Isomorphic React" is the idea of using the same templates rendered client-side on initial server render

/////

## Isomorphic React

<div style="display:flex;align-items:center;justify-content:space-around;">
    <img src="../../img/react/react-logo.png" style="background:none;box-shadow:none;border:none"/>
    <div>
		  <h2>Performance</h2>
      <h2>SEO</h2>
      <h2>Open Graph</h2>
    </div>
</div>

NOTES:
- Three reasons:
- Performance: initial page render
- SEO: google includes page render speed in ranking algorithm
- Open Graph: media previews
- React, unlike other JS frameworks/libraries, is setup to render server-side, as we'll see
- Want to emphasize that I'm talking about the _initial_ render

/////

## React components only define **WHAT** to render!

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Let's return to our old friend the `Incrementer` component
- Up until this point I've kind of made it seem like `render()` after reconciliation was rendering to the DOM
- But event that's not true!
- `render()` just informs _what_ elements & child components should be rendered
- It doesn't dictate _how_ they should be rendered

/////

## DOM rendering happens at the root

```js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'

const props = window.__SERVER_DATA__ || {}

ReactDOM.hyrdate(
  <App {..props} />,
  document.getElementById('root')
)
```
<!-- .element: class="large" -->

([`ReactDOM.hydrate`](https://reactjs.org/docs/react-dom.html#hydrate) is new in React 16)

<div class="code-highlight fragment current-visible" style="height: 70px; top: 201px"></div>
<div class="code-highlight fragment current-visible" style="height: 240px; top: 487px"></div>

NOTES:
_click through code highlights_

- Rendering to the DOM typically happens in the entry point of your app
- You'll import from `react-dom` and use it's `hydrate()` function (new to React 16)
- Inserts your app into the DOM location
- And then when your app updates, it produces a new component hierarchy
- `react-dom` is what takes that difference from reconciler and applies it to the DOM
- I bring up that distinction because that separation between building your UI and rendering to DOM...


/////

## Render to string server-side!

```js
import React from 'react'
import ReactDOMServer from 'react-dom/server'
import App from './App'

const props = {
  // Data coalesced from DB / API calls
  // Data coalesced from Express GET/POST params
  // Data coalesced from other environment params
}

const markup = ReactDOMServer.renderToString(<App {...props} />)

// return `markup` in HTML response
// assign `props` to `window.__SERVER_DATA__` in HTML response
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 711px"></div>

NOTES:
- Allows for us to render the _exact same_ UI server-side to a string!
- Take that string and include it in HTML response
- This is such a huge feature!
- Before this, all UI libraries just assumed the DOM and browser
- So getting your templates to run server-side was at best a pain; at worst in possible
- But now React allows us to do isomorphic javascript

/////

![Tanmai Gopal](../../img/reactathon/tanmai-gopal.png)  <!-- .element: style="width: 500px" -->  
Tanmai Gopal

<br />

## Lightning Talk: awesome-react-fullstack

(Stay for Day 3!)

NOTES:
- 

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div>
      <h1>7. Testing</h1>
    </div>
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/homer-simpson-walk-away.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Homer simpson slowly walks away" />
    </div>
</div>

NOTES:
- Who hear likes testing?!?!
- The same component-based architecture that makes server-side rendering easy, also makes testing React components easy
- Many other frameworks directly manipulate the DOM, making UI hard to test
- Pretty much have to run tests in a browser or headless browser which brought a host of issues

/////

## Test public API only!

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}), () => {
      this.props.onIncrement(this.state.value)
    })
  }

  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```

<div class="code-highlight" style="height: 60px; top: 353px"></div>

```
<Incrementer onIncrement={this._handleIncrement} />
```
<!-- .element: class="large" -->



NOTES:
- Again we have ol' faithful the `Incrementer` component
- Except this time after we click and update state, we also call `onIncrement` event handler prop
- We pass it `this.state.value` as a parameter
- At the bottom is an example of how you would call it
- We want to test the component's **public** API:
- The markup that it renders and the callback handlers it calls
- That's it! Don't want to test implementation details like `state` changes

/////

## Testing Render

```js
import {shallow} from 'enzyme'

it('renders a `.val`', () => {
  const wrapper = shallow(<Incrementer />)

  expect(wraper.find('.val')).toBePresent()
  expect(wrapper.find('.val')).toHaveText('0')
})
```
<!-- .element: class="large" -->

[Jest](https://facebook.github.io/jest/) + [Enzyme](http://airbnb.io/enzyme/) +
[`jest-enzyme`](https://yarnpkg.com/en/package/jest-enzyme) = 😍

NOTES:
- We can test `Incrementer` using Jest & Enzyme to test the public API
- Enzyme has a jQuery-like interface for manipulating React components
- All w/o a browser
- "Rendering" is creating an enzyme wrapper
- We use Jest as the test framework & assertion lib; also created by Facebook
- `jest-enzyme` provides additional enzyme-specific assertions to Jest
- Here we're asserting that `Incremener` renders an element with `.val` class
- And that that `.val` element has the text "0" inside of it

/////

## Testing callbacks

```js
import {shallow} from 'enzyme'

it('calls `onIncrement` prop with current value', () => {
  const onIncrement = jest.fn()
  const wrapper = shallow(<Incrementer onIncrement={onIncrement} />)
  const button = wrapper.find('button')

  // simulate clicking twice
  button.simulate('click')
  button.simulate('click')

  expect(onIncrement).toHaveBeenCalledTimes(2)
  expect(onIncrement).toHaveBeenLastCalledWith(2)
})
```
<!-- .element: class="large" -->

NOTES:
- If you recall, when we click the button we call our `onIncrement` handler
- We want to verify that when we click the button that `onIncrement` gets called w/ the right parameter
- Well with enzyme we can simulate clicking the button w/o running in a browser!
- And with Jest we can provide a mock function using `jest.fn()`
- Then we can assert things on that mock:
- How many times it was called (twice for 2 clicks)
- What arguments it was last called with (2)
- Again: we shouldn't inspect the `state` of the component (which would be 2)
- Instead we assert on the value in the handler (the public API)
- Being able to unit test like this is a game-changer

/////

![Rachel Ralston](../../img/reactathon/rachel-ralston.png)  <!-- .element: style="width: 500px" -->  
Rachel Ralston

<br />

## Testing your React Components with Jest

(This afternoon @ 1:15p!)

NOTES:
- Hopefully I haven't stolen too much of Rachel's thunder cuz she's going to show us how to properly test our React components

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/mind-blown.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Mind blown!" />
    </div>
    <div>
      <h1>8. React Native</h1>
      <h2>(...and other renderers)</h2>
    </div>
</div>

NOTES:
- Let's jump to the 8th reason for transitioning
- Eventbrite has 4 native apps: 2 on iOS & 2 on Android
- One set for people running events (organizer) / other set for people attending (attendee)
- We don't have any plans to replace our apps with React Native
- But should we need other native apps, being able to use React Native is appealing

/////

![Learn Once, Write Anywhere screenshot from react homepage](../../img/why-react/react-learn-once-write-anywhere.png)
<!-- .element: style="width: 50%" -->

NOTES:
- One of the benefits React mentions on its home page is that you can "Learn Once, Write Anywhere"
- Basically saying that once you learn React and its paradigms, you can build apps for _any_ environment
- Not just the web

/////

## React for the Web

```js
class Incrementer extends React.Component {
  state = {value: 0}

  _handleClick = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <div>
        <span className="val">{this.state.value}</span>
        <button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 240px; top: 603px"></div>


NOTES:
- Let's bring back our good friend the `Incrementer` component one more time
- Here's what it looks like if we were writing for React in the web
- We're using HTML elements: `<div>`, `<span>` & `<button>`
- But...

/////

## React Native 😄

```js
import {View, Text, TouchableOpacity} from 'react-native'
class Incrementer extends React.Component {
  state = {value: 0}
  _handlePress = () => {
    this.setState((prevState) => ({value: prevState.value + 1}))
  }
  render() {
    return (
      <View>
        <Text style={...}>{this.state.value}</span>
        <TouchableOpacity onPress={this._handlePress}>+</TouchableOpacity>
      </View>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 143px"></div>
<div class="code-highlight" style="height: 240px; top: 603px"></div>


NOTES:
- If replaced `<div>`, `<span>` & `<button>` w/ `View`, `Text` & `TouchableOpacity` components from
  `react-native`
- You've got the makings a native app!
- I remember when I went to a React Native workshop and was blown away
- Everything I learned building React web apps, I could leverage in React Native
- Just like w/ the web there are special considerations for native of course
- Layout engine is different
- But there are a bunch more pre-built components
- And React is not just for mobile devices...

/////

## React exists in many environments

<div style="columns:3;-webkit-columns:3;-moz-columns:3;margin: 2em 0">
  [`ink`](https://github.com/vadimdemedes/ink)  
  [`noop-renderer`](https://github.com/facebook/react/blob/master/src/renderers/noop/ReactNoop.js)  
  [`rax`](https://github.com/alibaba/rax)  
  [`react-art`](https://github.com/reactjs/react-art)  
  [`react-blessed`](https://github.com/Yomguithereal/react-blessed)  
  [`react-canvas`](https://github.com/Flipboard/react-canvas)  
  [_**`react-dom`**_](https://github.com/facebook/react/tree/master/packages/react-dom)  
  [`react-fs-renderer`](https://github.com/ericvicenti/react-fs-renderer)  
  [`React-Gibbon`](http://techblog.netflix.com/2017/01/crafting-high-performance-tv-user.html)  
  [`React-GL`](https://github.com/PixelsCommander/React-GL)  
  [`react-hardware`](https://github.com/iamdustan/react-hardware)  
  [`react-html-email`](https://github.com/chromakode/react-html-email)  
  [`react-konsul`](https://github.com/mohebifar/konsul)  
  [_**`react-native`**_](https://github.com/facebook/react-native)  
  [`react-pdf`](https://github.com/diegomura/react-pdf)  
  [_**`react-sketchapp`**_](https://github.com/airbnb/react-sketchapp)  
  [_**`react-test-renderer`**_](https://www.npmjs.com/package/react-test-renderer)  
  [`react-three`](https://github.com/Izzimach/react-three)  
  [`react-titanium`](https://github.com/yuchi/react-titanium)  
  [`react-tvml`](https://github.com/ramitos/react-tvml)  
  [_**`react-vr`**_](https://github.com/facebookincubator/react-vr)  
  [`react-worker-dom`](https://github.com/web-perf/react-worker-dom)  
  [`react-x11`](https://github.com/sidorares/react-x11)  
  [`ReactLiberty`](https://github.com/LibertyGlobal/ReactLiberty)  
</div>

Source: [`awesome-react-renderer`](https://github.com/chentsulin/awesome-react-renderer)

NOTES:
- React is everywhere! Got 24 renderers listed here!
- And the new Fiber architecture should make building new renderers easier
- Remember the Reconciler determines what in the UI should change on re-render
- The renderer actually applies the changes in the environment
- We're pretty excited about `react-sketchapp` from Airbnb
- Just discovered `react-html-email`; need to look into that one!
- These are all links so feel free to check them out!

/////

![Harry Tormey](../../img/reactathon/harry-tormey.png)  <!-- .element: style="width: 500px" -->  
Harry Tormey

<br />

## An iOS Developer's Opinion of React Native

(This afternoon @ 2:55p!)

NOTES:
- So Harry, a recovering iOS Devleoper, will really clue us in on how React Native works
- Being an iOS developer, he'll really be able to give us a solid comparison

=====
<!-- .slide: data-background="#ddd" -->

# 9. Unopinionated

![Lady falls down slipping on bowling lane](../../img/giphy/bowling-lane-fall.gif)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 60%" -->

NOTES:
- Honestly this 9th reason can be seen as a pro or con depending on how you look at it
- React is pretty unopinionated on how your apps should be built

/////

## Decisions decisions...

<div style="display:flex;align-items:flex-start;justify-content:space-between;margin:2em 0">
    <div>
        <h3>Tooling</h3>

        <ul>
          <li>bundlers</li>
          <li>task runners</li>
          <li>static analyzers</li>
        </ul>
    </div>
    <div>
        <h3>Styling</h3>

        <ul>
          <li>global css</li>
          <li><a href="https://github.com/gajus/react-css-modules" target="_blank">css modules</a></li>
          <li>inline styles</li>
          <li>css-in-js 🔥</li>
        </ul>
    </div>
    <div>
        <h3>Testing</h3>

        <ul>
          <li><a href="https://facebook.github.io/jest/" target="_blank">jest</a></li>
          <li><a href="https://mochajs.org" target="_blank">mocha</a> + <a href="http://chaijs.com" target="_blank">chai</a></li>
        </ul>
    </div>
    <div>
        <h3>State</h3>

        <ul>
          <li><a href="https://reactjs.org/docs/react-component.html#setstate" target="_blank"><code>setState</code></a></li>
          <li><a href="http://redux.js.org/" target="_blank">redux</a></li>
          <li><a href="http://mobxjs.github.io/mobx/" target="_blank">mobx</a></li>
        </ul>
    </div>
    <div>
        <h3>API</h3>

        <ul>
          <li>REST + <a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank"><code>fetch</code></a></li>
          <li><a href="https://facebook.github.io/relay/" target="_blank">relay</a></li>
          <li><a href="http://dev.apollodata.com/" target="_blank">apollo</a></li>
          <li><a href="http://netflix.github.io/falcor/" target="_blank">falcor</a></li>
        </ul>
    </div>
</div>

Decision fatigue?

NOTES:
- React is just a UI library; it's a great one IMO, but just a UI library
- So to create apps you need to build up your own stack
- **Tooling:** probably Webpack, but need to configure it; gulp/grunt; eslint/flow/Typescript;
- Create React App helps w/ getting started; eject later
- **Styling:** glamorous, styled-components, radium, aphrodite
- You really get to tailor your own stack
- But if you're just getting started it's "decision fatigute"

/////

## Moar decisions decisions...

<div style="display:flex;align-items:flex-start;justify-content:space-between;margin:2em 0">
    <div>
        <a href="https://medium.com/javascript-scene/setstate-gate-abc10a9b2d82" target="_blank"><img src="../../img/why-react/setState-gate.png" alt="setState Gate by Eric Elliott" /></a>
    </div>
    <div>
        <a href="https://cdb.reacttraining.com/react-inline-functions-and-performance-bdff784f5578" target="_blank"><img src="../../img/why-react/inline-functions.png" alt="Inline functions debate by Ryan Florence" /></a>
    </div>
    <div>
        <a href="https://medium.com/react-native-training/redux-4-ways-95a130da0cdc" target="_blank"><img src="../../img/why-react/redux-4-ways.png" alt="Redux 4 Ways by Nader Dabat" /></a>
    </div>
    <div>
        <a href="https://cdb.reacttraining.com/use-a-render-prop-50de598f11ce" target="_blank"><img src="../../img/why-react/use-a-render-prop.png" alt="Use a Render Prop by Michael Jackson" /></a>
    </div>
</div>

There's no **React way™** 🤷🏾‍♂️

NOTES:
- But even when you have the stack down, there are all these debates abou the "right way" to do things
- Do you always use component classes or use stateless functions until you need state?
- `setState` gate
- Inline functions debate
- 4 different ways to do Redux side-effects: thunk, sagas, observables & promise middleware
- HOCs vs render props
- How can you decide if you're new to React and don't even know what I just said?
- But can be a "pro" because you can look at the team and make decisions based on the skillset
- This is how you can from one team to another doing React and it'll be done completely differently

/////

![Joe Seifi](../../img/reactathon/joe-seifi.png)  <!-- .element: style="width: 500px" -->  
Joe Seifi

<br />

## CSS in React

(Right after luch, no napping!)

NOTES:
- Luckily for us we've got a number of speakers today with a lot of opinions!
- I work with Joe at Eventbrite, he's gonna share **FIVE** different ways to style our React components

/////

![Mark Erikson](../../img/reactathon/mark-erikson.png)  <!-- .element: style="width: 500px" -->  
Mark Erikson

<br />

## The Fundamentals of Redux

(Today @ 2:15p!)

NOTES:
- I mentioned there are different ways to maintain state, `setState()`, Redux & Mobx
- Well Mark is a maintainer of Redux, so you know he's got opinions about Redux
- He's gonna teach us the fundamentals of Redux!

/////

![Jon Wong](../../img/reactathon/jon-wong.png)  <!-- .element: style="width: 500px" -->  
Jon Wong

<br />

## An Introduction to GraphQL

(Today @ 3:30p!)

NOTES:
- Most of us are probably familiar with interacting with REST APIs
- But GraphQL is alternative (and easier) way to retrieve data
- My buddy Jon is going to give us a gentle introduction 

=====
<!-- .slide: data-background="#ddd" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/omg-taco.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Taco goes from one woman's mouth to the next" />
    </div>
    <div>
      <h1>10. Miscellaneous</h1>
    </div>
</div>

NOTES:
- Ok, the final reason that Eventbrite wanted to migrate to React is a sort of catch-all
- There are many other reason for going for React
- Don't really deserve their own section (and I don't have hours), but still important...

/////

## Other considerations

<div style="columns:2;-webkit-columns:2;-moz-columns:2;margin: 2em 0">
  <h3>Deep commitment by Facebook</h3>
  <h3>Dedicated Facebook dev staff</h3>
  <h3>Rapid feedback loop</h3>
  <h3>Huge ecosystem</h3>
  <h3>Simple API</h3>
  <h3>Popular</h3>
  <h3>Stable</h3>
  <h3>Evolving</h3>
  <h3>Codemods</h3>
  <h3>Developer Tools</h3>
  <h3>Browser compatibility</h3>
  <h3>Composable with existing apps</h3>
</div>

Thanks [Cory House 🏠](https://twitter.com/housecor/status/909145686498775040)!

NOTES:
- **Commitment**: Facebook uses it in their own products so less likely to go away
- **Staff**: is a big reason; it's not just some folks doing it in their spare time
- **Popular**: not a good enough reason by itself but doesn't hurt for recruiting/perception
- **Simple API**: I rarely have to go to the docs (except for prop types)
- **Ecosystem**: Similarly the eco-system is huge so if you need to do something probably already
  exists
- **Feedback**: React + webpack makes developing a sync with webpack dev server
- **Evolving + Stable**: React continues to grow greatly (Fiber) but few breaking changes & there
  are long deprecations
- **Codemods**: enable switching code when features are deprecated
- **Existing apps**: React _can_ be used with other libs like Backbone for a gradual transition
  (what we're doing)
- This list was lifted from a tweet from Cory, so thanks!

=====

## Recap

<ol style="margin-right: 1em">
  <li>Declarative JSX</li>
  <li>Component-driven</li>
  <li>All JavaScript*</li>
  <li>State-driven</li>
  <li class="fragment highlight-red">Sophisticated reconciler</li>
</ol>

<ol start="6">
  <li>Server-side rendering</li>
  <li>Testing</li>
  <li>React Native</li>
  <li>Unopionated</li>
  <li>...and more!</li>
</ol>

NOTES:
- Again these are the reasons **we** made the switch to React
- I really wish I could've gone into more details on each one
- Each one literally could be its own talk
- Talked about how JSX provides great developer ergonomics
- The fact that it's component-driven not only makes it easy to build UIs
- But also enables the reconciler, server-side rendering, testing & dozens of other renders
- It's state-driven instead of event-driven and we can use at lot of the latest JavaScript in our apps
- And many other goodies!
- My favorite one is the sophisticated reconciler!

=====

![React logo](../../img/react/react-logo.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 15%" -->


# +


![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 75%" -->

NOTES:
- Before I let you go, I wanna quickly showcase a handful of new experiences on Eventbrite that are built in React

/////

## Eventbrite Design System

<video data-autoplay loop style="width: 80%">
  <source data-src="../../img/why-react/eventbrite-design-system.m4v" />
</video>

NOTES:
- It's filled with dozens of React components big and small
- But it's more than a component library; it's a design system
- Talks about _why_ components should be used, etc
- David Wells will be talking about how to build a React design system for your company first thing tomorrow morning

/////

## [Sign-in / Sign-up](http://www.eventbrite.com/signin)

<a href="http://www.eventbrite.com/signin">
  <video data-autoplay loop style="width: 80%">
    <source data-src="../../img/why-react/eventbrite-sign-up-flow.m4v" />
  </video>
</a>

NOTES:
- We rebuilt our sign-in & sign-up experiences in React
- It's actually a modal that sits on top of the page
- And it's launchable from every page, React or not
- So it's an example of React co-existing w/ non React
- It's dynamically loaded using dynamic `import()`

/////

## [Checkout Widget](https://www.speednashvilledating.com/event-schedule/)

<a href="https://www.speednashvilledating.com/event-schedule/">
  <video data-autoplay loop style="width: 80%">
    <source data-src="../../img/why-react/eventbrite-checkout-widget.m4v" />
  </video>
</a>


NOTES:
- We want to give organizers the ability to control the experience of displaying tickets
- Checkout widget takes you to speednashvilledating.com FYI
- Taking place tonight at 8PM

/////

## [Organizer Onboarding](https://www.eventbrite.com/organizer/onboarding/)

<a href="https://www.eventbrite.com/organizer/onboarding/" target="_blank">
  <video data-autoplay loop style="width: 80%">
    <source data-src="../../img/why-react/eventbrite-organizer-onboarding-flow.m4v" />
  </video>
</a>

/////

## [City Browse](https://www.eventbrite.com/d/tn--nashville/events/?janus_fv=exp_eb_60058_city_browse%3DB)

<a href="https://www.eventbrite.com/d/tn--nashville/events/?janus_fv=exp_eb_60058_city_browse%3DB" target="_blank">
  <video data-autoplay loop style="width: 80%">
    <source data-src="../../img/why-react/eventbrite-city-browse-flow.m4v" />
  </video>
</a>

/////

## Eventbrite + React in the wild

- [Trending Searches](https://www.eventbrite.com/trending/searches/tn--nashville/daily/)
- Event Creation (Beta)
- Event Management Navigation
- Event Management Dashboard
- Admin Tools
- Secret stuff coming soon! 🤫

NOTES:
- Event Management Navigation was an example where we mixed React & Backbone
- Dozens of management pages that share the same nav, so redid the nav in React
- So that when pages got rewritten or added, the IA would seem consistent

=====

## Additional resources

- [The Beginner's Guide to ReactJS](https://egghead.io/courses/the-beginner-s-guide-to-reactjs)
- [Advanced React Component Patterns](https://egghead.io/courses/advanced-react-component-patterns)
- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite ES6+ coding styleguide](https://github.com/eventbrite/javascript/tree/master/es6)
- [Eventbrite React Testing Best Practices](https://github.com/eventbrite/javascript/blob/master/react/testing.md)
- [React/Redux Links](https://github.com/markerikson/react-redux-links)


NOTES:
- Mark (w/ help) has collection a bazillion links to resources covering React, Redux, ES6 and more!

=====

![Jack Sparrow Thanks](../../img/giphy/animated-take-a-bow.gif)
<!-- .element: style="width: 50%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So before I close...
- Wanted to thank Nodevember for inviting me to share with you
- Let's celebrate them for putting on another great conference
- Thanks to Eventbrite too for sponsoring and flying me out
- Also thank YOU for attending and sticking around!
- My goal is for you to learn at least one thing you can take away to be a better dev
- Hopefully if you are in the same boat of wanting to transition, you've got some good material
- Slides are available on Twitter and Blog
- Would love to hear from you about things that were unclear, wanna know more about or general questions
- Ask on Twitter, via AMA or email
- I hope you enjoyed the conference
- Thanks and let's enjoy the afterparty
