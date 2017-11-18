# Why choose React?

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#nodevember2017](https://twitter.com/hashtag/nodevember2017)  

<br />

November 28, 2017  

NOTES:
- My name is Ben Ilegbodu
- Here to pull back the covers on how Eventbrite decided to make the switch from Backbone to React
- Posted link to slides on twitter if you want to follow along

/////

[![Tweet about Nodevember being my first talk](../../img/why-react/nodevember-first-talk-tweet.png)](https://twitter.com/benmvp/status/626294349148483584)

NOTES:
- Beyond excited to be giving the CLOSING KEYNOTE here at Nodevember
- Truly an honor
- Because 2 years ago I was novice speaker hoping for a chance
- Had such a great time sharing about ES6 and learn so much
- And now I'm back

=====

## What this talk is **not** about... 😞

<br />

- Intro to React
- React is better than _X_
- React 💕 fest

NOTES:
- The goal of this talk is not to teach you React, so you can go off and build the next app that's gonna change the game
- Even if I wanted to, not possible in an hour
- Also not gonna be framework bashing; talking about how React is better than Angular or Vue
- Although I am basically saying it's better than Backbone since switched
- Lastly, not gonna be a React love-fest
- There's no perfect framework; there are trade-offs and I'll point them out
- So hopefully if you're still investigating, you'll get a somewhat balanced opinion

/////

## What this talk is about! 😄

<br />

- Rationales explained in code
- For everyone!
- Shameless plugs

NOTES:
- Wanna walk through the many reasons why we made the switch
- But not just talk about; I want to demonstrate it w/ code
- Also, given that this is a keynote for everyone I wanted to make it useful to everyone
- So if you've never used React, it should be a good primer
- But if you're hardcore React, hopefully I can hit you w/ some tips
- And if not this can be an example of how to explain besides "it's awesome"
- Heads up!
- I've had the opportunity now to speak about a variety of different React topics over the last year
- Throughout the talk I'll be giving shameless plugs to those talks
- Forewarning you now, so you can get all of your eye rolls out early

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 4px; color: white" -->

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

/////

## me.json

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<img src="../../img/family-house-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family standing in front of their house" />
	</div>
	<div style="flex:0 0 50%;">
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

/////

![NBA Go CLI](../../img/giphy/nba-go-cli.gif)
<!-- .element: style="width: 75%" -->


[xxhomey19/nba-go](https://github.com/xxhomey19/nba-go)

NOTES:
- I'm a huge basketball fan; love playing & watching
- Got so excited when I found this NBA Go CLI
- I use VS Code, which has the terminal pane right at the bottom
- So I could literally be following the game and coding at the same time!

=====

# Why choose React?

NOTES:
- Let's jump right in

/////

[![Tweet from Jordan Harband about how people are hard](../../img/why-react/jordan-harband-people-are-hard.png)](https://twitter.com/ljharb/status/927606717793296384)

NOTES:
- I've been in the industry for about a dozen years
- And I've come to realize that software development isn't just the code you commit
- There's an equal human element to it
- Whenever doing something buy-in is equally as important as the technical approach
- When difficulties arise, the difference between folks complaining or rallying to find a solution, is buy-in
- We had tried React a couple of times, ran into issues, and people threw out the baby w/ the bathwater
- So this time, in early 2016, I put together a loooong document to explain why our Frontend Platform team thought we should make the switch
- The rest of the talk is a talk-friendly distillation of that doc

=====

# Declarative JSX

/////

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
- Here's a rather simple component
- All it does is increment the value every time you click the button
- Want to zero on the `render()` method which is return this HTML-link syntax in our JavaScript
- Many people didn't like the syntax at first
- But I find it very approachable

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
- Here it is close up


/////

## Transpiled JSX

```js
React.createElement(
  "div",
  null,
  React.createElement("span", {className: "val"}, value),
  React.createElement("button", {onClick: this._handleClick}, "+")
);
```
<!-- .element: class="large" -->

NOTES:
- Here it is transpiled; it's just JavaScript
- Thanks to the power of build tooling (Babel)
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
- With React, a component contains...
  * Markup (`render()`)
  - Logic (`_handleClick`)
  - Data (`this.state`)
- You can also include styling too, but not trying to start a flamewar over css-in-js right now
- So everything is collocated, which is very different than traditional MVC like Backbone

/////

## Traditional MVC equivalent

Backbone Model & View
```
var IncrementerModel = Backbone.Model.extend({
  defaults: {value: 0}
})
var IncrementerView = Backbone.View.extend({
  template: Handlebars.compile($('#tempalte').html()),
  events: {
    'click .js-btn': 'increment'
  },
  initialize: function() {
    this.listenTo(this.model, 'change', this.render)
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
  },
  render: function() {
    this.$el.html(this.template(this.mode.attributes))
  }
})
```

NOTES:
- This is the traditional MVC equivalent in Backbone
- You have a separate file for template (markup), model & view (logic)
- Here's the logic
- THe idea is that we wanted to have a "separation of concerns"
- But it didn't happen in practice; especially as things got complex
- We used `js-*` prefix in our templates to safely reference them in views
- If the template changed, you needed to change the view
- If the model changed, you needed to change the tmeplate, and so on
- As things got complicated, hard to know the effects changing one would have on the other
- BTW - we're re-rendering everytime the model changes for simplicity, but bad perf

/////

## Traditional MVC equivalent

Handlebars template
```
<div>
  <span class="val">{{value}}</span>
  <button class="js-btn">+</button>
</div>
```
<!-- .element: class="large" -->

NOTES:
- Here's the template; it's simple enough
- But the templating languages were intended to be _just_ markup, so limited logic...

/////

## Logic in the template

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
- And doing any kind of fancy logic got really, really messy
- Plus we'd basically have to basically learn a new language
- We created "helpers" so we could call functions in templates
- Alternative is to do a whole lot of pre-computation in the view to enable the template to be dumb
- Handlebars didn't even have `else-if`
- So we'd have a nested `if` w/in an `else`

/////

## Logic in React Component

```js
class Selector extends React.Component {
  render() {
    let options = this.props.values.map((info) => {
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
- But with React, since our markup is in JavaScript
- We have the full use of JavaScript at our dispoable to build up the markup
- We also have linting, editor autocmoplete, and more around JavaScript the language
- There's no need, IMO, to invent a new language for logic

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
labelNode.htmlFor = inputId
```
<!-- .element: class="large" -->

NOTES:
- One con or gotcha, is that although JSX looks like HTML, it's not
- It's the `className` & `htmlFor` prop which make it **really** clear that this isn't HTML
- React chose to mirror the JS DOM API for its props which are all camelCase
- And that's why its `className` & `htmlFor` instead of the HTML `class` & `for`
- It's also why it's `onClick`, `onChange`, etc.
- React is pretty good at giving great warnings if you forget or mess up
- Especially with React 16

/////

## [React exposed! 😮](http://www.benmvp.com/slides/2017/forwardjs/react-exposed.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/cAYMqBU7Qko" frameborder="0" allowfullscreen></iframe>

### ForwardJS Spring 2017

NOTES:
- Shameless plug alert!
- I gave a talk called _React exposed! 😮_ at ForwardJS earlier this year
- I go through several JSX gotchas among other topics

=====

# Component-driven

/////

## Everything is a component!

```js
class FormField extends React.Component {
  render() {
    let name = this.props.name
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
- Here we have a FormField component made up of `Label` & `TextInput` components
- It defines 4 `props`, which are how the component is configured

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
- You include the component by importing it and then using it in `render()` like an HTML tag
- And you configure the props by passing them in via attributes, just like HTML
- Although we're in Javascript using JSX, the HTML-like syntax should feel familiar
- Then you can combine one or more `FormField` components to create a bigger form component
- And keep doing that until you have a full-fledged app

/////

## Eventbrite Design System

![Eventbrite Design System](../../img/why-react/eds-homepage.png)
<!-- .element: style="border: 0; background: none; margin: 0; width: 85%" -->

NOTES:
- At Eventbrite we created our own component library
- It's filled with dozens of React components big and small
- But it's more than a component library; it's a design system
- Talks about _why_ components should be used, etc

/////

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
		<img src="../../img/react/backbone-logo.png" style="width:100%;height:auto;border:0;background:none;box-shadow:none;" alt="Backbone.js logo" />
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/react/marionette-logo.svg" style="width:100%;height:auto;border:0;background:none;box-shadow:none;" alt="Marionette logo" />
	</div>
</div>

NOTES:
- Component-driven development seems pretty obvious right?
- All the popular libraries/frameworks are component-driven in their own way
- But not Backbone; you simply could not nest Backbone views
- Now we were also using Marionette; an architecture layer on top of Backbone
- The version we were using had Layouts, which could contain Views, which could _be_ layouts so nesting was possible
- But it was not nearly as effortless as what I just showed w/ React
- Configuring the nested views wasn't simple either
- It's the difference between components being the core vs. being an add-on
- We were stuck on the latest v1 version that came out mid-2014; think about how JS has changed since then

/////

## Explicitly passing data DOWN the tree

`App.js`
```
<NameForm fields={ ... } />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`NameForm.js`
```
<FormField name="first" value={props.fields.first} />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`FormField.js`
```
<TextInput value={props.value} />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`TextInput.js`
```
<input type="text" value={props.value} />
```
<!-- .element: class="large" -->

NOTES:
- It's not all sunshine & roses; at least not for everyone
- If in my `App` I want to set the value of the HTML input for the first name...
- I pass it from `App` -> `NameForm` -> `FormField` -> `TextInput` that reners `<input>`
- This is _very_ explicit; you can clearly see how data flows down the component hierarchy
- I personally don't have a problem with it because I prefer the clarity; especially in code reviews
- But some find it verbose. If they could, they'd rather jump levels of the hierarchy to get it where it should
- But I've seen that introduce other gnarliness

/////

## Explicitly passing data UP the tree 

`App.js`
```
<NameForm onFieldChange={this._handleFieldChange} />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`NameForm.js`
```
<FormField onChange={props.onFieldChange.bind(null, 'first')} />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`FormField.js`
```
<TextInput onChange={props.onChange} />
```
<!-- .element: class="large" style="margin-bottom: 1.5em" -->

`TextInput.js`
```
<input type="text" onChange={props.onChange} />
```
<!-- .element: class="large" -->

NOTES:
- Similarly getting data back **up** the tree is also explicit
- Let's say the top-level App wants to react to changes in the `<input>` field
- Well we have to pass callback handlers down the tree as props
- So when `onChange` happens on `TextInput` -> `FormField` -> `NameForm` -> `App`
- In Backbone/Marionette we had global "radios" & components could register channels
- But no enforcement on who was sending/receiving

/////

## `<App />`

## ↓ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↑

## `<NameForm />`

## ↓ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↑

## `<FormField />`

## ↓ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↑

## `<TextInput />`

## ↓ &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; ↑

## `<input />`



NOTES:
- This one-way circular data flow is a completely different way of thinking than traditional MVC
- It's probably the hardest thing to grasp in React, but one you do everything else falls into place

=====

# All JavaScript*

NOTES:
- Have the asterisk there because obviously we're building web apps so CSS is definitely involved

/////

[![Dan Abramov's tweet about no special JSX API for loops/conditionals](../../img/why-react/dan-abramov-jsx-tweet.png)](https://twitter.com/dan_abramov/status/929136989085093890)

(...but [StackOverflow](https://stackoverflow.com/questions/22876978/loop-inside-react-jsx))

NOTES:
- Dan tweeted this in response to an RFC to add conditionals and loops into JSX
- I ❤️ JavaScript so the more I can do in JS the better
- I'm glad that I don't have to learn a new API to do conditionals/loops in JS
- Because it's JS, I can do whatever JS can do
- For some though, this is a drawback because you _have_ to know JS pretty well
- Before if you were solid at HTML/CSS, you could throw some jQuery around and do well
- I would say it's not intuitive: there's a StackOveflow question about loops that has > 300k views!
- Now it's JS or bust, which takes some getting used to

/////

## Conditional JSX

```
class Section extends React.Component {
  render() {
    let headingText = this.props.headingText

    return (
      <section className="section-correct">
        if (headingText) {
          <h1>{headingText}</h1>
        }
        <p>{this.props.children}</p>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- All the string-based templating languages provide some facility for conditionally including markup
- In those cases, you're trying to replicate logic in the template
- May be tempted to do something like this
- Or... more likely just wonder how to accomplish conditionally including code
- Cuz this obviously looks like broken syntax
- Trying to include the `<h1>` only if `headingText` is defined
- This is a syntax error

/////

## Conditional JSX

```
class Section extends React.Component {
  render() {
    let headingText = this.props.headingText
    let headingElem

    if (headingText) {
      headingElem = (<h1>{headingText}</h1>)
    }
    return (
      <section className="section-correct">
        {headingElem}
        <p>{this.props.children}</p>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- React doesn't have any special API to do loops or conditionals
- It just piggybacks on JavaScript
- Here's how I would do the conditional
- We can use normal JS to do conditionals instead of muddying up our JSX
- Conditionally assign a variable, and put that in our JSX

/////

## Conditional JSX

```
class Section extends React.Component {
  render() {
    let headingText = this.props.headingText
    let headingElem

    if (headingText) {
      headingElem = React.createElement('h1', null, headingText)
    }
    return React.createElement(
      'section',
      {className: 'section-correct'},
      headingElem,
      React.createElement('p', null, children)
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- This is what the JSX would be transformed into
- So it really **is** all JavaScript
- It seems like a lot more code, so...

/////

## Conditional JSX

```
class Section extends React.Component {
  render() {
    let headingText = this.props.headingText

    return (
      <section className="section-correct">
        {headingText ? (<h1>{headingText}</h1>) : null}
	      <p>{this.props.children}</p>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Many people use a ternary for this to keep things short
- But at Eventbrite we strive to keep the JSX as "clean" as possible
- This might be "okay", but would get out of hand quickly
- I've seen ternaries spanning 10+ lines

/////

## React + ES.next = ❤️

```
class Section extends React.Component {
  render() {
    let headingText = this.props.headingText
    let headingElem

    if (headingText) {
      headingElem = (<h1>{headingText}</h1>)
    }
    return (
      <section className="section-correct">
        {headingElem}
        <p>{this.props.children}</p>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- The nice thing about React, the JS UI lib, tying itself to JS instead of its own API is that as JS evolves it auto-evolves
- You probably already noticed that we were using `class`es to creat our React components
- That's ES6 that's become standard with React
- But we can take the previous `Section` component...

/////

## React + ES.next = ❤️

```
const Section = ({headingText, children}) => {
  let headingElem

  if (headingText) {
    headingElem = (<h1>{headingText}</h1>)
  }

  return (
    <section className="section-correct">
      {headingElem}
      <p>{children}</p>
    </section>
  )
}
```
<!-- .element: class="large" -->

NOTES:
- ...rewrite it using the latest JavaScript
- React components can be written as functions of their props
- Here we're using an arrow function instead of a standard function
- And we're immediately destructuring the props into `headerText` & `children`
- There's plenty more we can do too

/////

## Gotta have a build system

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

Fun features like [tree-shaking](https://webpack.js.org/guides/tree-shaking/) & [code splitting](https://webpack.js.org/guides/code-splitting/)!

NOTES:
- But all this goodness comes at a cost
- We basically are forced to have a build system
- And that's where some combo of Babel, Webpack, TypeScript, Rollup, etc. come in
- Chances are for production apps you already had _some_ sort of build system
- Compile SASS -> CSS, minify & bundle JS, etc
- Paying the upfront cost of the build system enables cool features: tree-shaking & code splitting

/////

## Create React App

Create React apps with no build configuration

```
$> yarn add global create-react-app

$> create-react-app awesome-app

$> cd awesome-app

$> yarn start
```
<!-- .element: class="large" style="margin:5% 0" -->

Babel, Webpack 3, ESLint, and more!

NOTES:
- And you don't have to roll your own build system; at least not initially
- Create React App let's you bootstrap an app to start React-ing quickly

/////

## [React + ES.next = ♥](http://www.benmvp.com/slides/2017/reactconf/react-esnext.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/jh_Qzi-yHU0" frameborder="0" allowfullscreen></iframe>

### ReactConf 2017

NOTES:
- Shameless plug alert!
- I gave a talk called _React + ES.next = ♥_ at React Conf back in March
- I go through a handful of ES.next features that go great with React

=====

# State-driven

NOTES:
- So far we've basically been creating static user-interfaces; not user interaction
- To do that the state of the UI has to change over time
- React components are state-driven instead of the more familiar event-driven
- This is the hardest thing to wrap your head around if you're new to React
- It's just a different way of building UIs
- But I've found it to be very compelling

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
      currentValue = parseInt($val.html(), 10);

  $val.html(currentValue + 1);
});
```
<!-- .element: class="large" -->

<div>
	<span class="val" style="font-size: 2em;text-align: center;margin: 0 1em">0</span>
	<button class="btnUp" style="font-size: 2em" onclick="$('.val').html(+$('.val').html() + 1)">&nbsp;&nbsp;+&nbsp;&nbsp;</button>
</div>

NOTES:
- Here's some event-driven jQuery code that should be pretty familiar
- It's the jQuery equivalent of the `Incrementer` component we saw earlier when talking about JSX
- Click a button and update `<span>`
- The driver is the event
- The only way to get the app so that it displays 10 is to click the button 10 times
- If you were using Backbone you may have a model that you update as well, but it's basically same flow
- This is _really_ easy to follow (imperative), but as app grows in complexity, code turns into spaghetti

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

NOTES:
- Contrast this with the React code
- Used ES.next to keep my example as concise as possible
- Explanation of code...
- It's the handler that does the logic of incrementing the value; separation of concerns!
- And since `value` is already in `state` we don't have to get it from the DOM
- Then calling `setState` causes `render` to be called again
- Click again and the loop continues
- In the old world `_handleClick` would've directly manipulated the DOM
- But instead we update the state and that will indirectly update the DOM
- Layer of indirection is hard to wrap head around

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
        <Text size="large">{this.state.value}</span>
        <Button onClick={this._handleClick}>+</button>
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Let's say instead of DOM elements, `Incrementer` used other React components
- We see here that the `state` of `Incrementer` becomes the `props` of `Text`
- So `Text` can be "dumb" in that it does worry about any state
- Just renders based on its `size` & special `children` props
- I find that React dev is actually similar to server-side dev
- Server-side: one-pass, render out the marker
- React: initial render, but subsequent renders

/////

## State-driven React

Work in React can be boiled down to 2 main areas...
<!-- .element: style="margin: 2em 0" -->

1. `render()` based on `props` & `state`
1. `onEvent` → transform data to generate new `state`
1. Profit 🎉

NOTES:
- So basically we do work in two main areas:
- 1) Define what we're going to `render()` based on `prop` & `state`
- Can have conditional logic, loops, other sophisticated logic to determin what to render
- 2) When events happen transform data to generate new `state` (to `render` again)
- Where algorithms become really useful to transform data efficiently
- Can also do async transformation by making API calls

/////

[![Dan Abramov's tweet about how React code remains understandable as app gets more complex](../../img/why-react/dan-abramov-reactive-tweet.png)](https://twitter.com/dan_abramov/status/930380316463726593)

NOTES:
- When folks look at simple examples of "reactivity" in React, they find it to be too verbose
- But with React trades conciseness for predictability
- So you end up spending more time explicitly wiring things up together
- Structure of your code can more or less stay the same as complexity grows
- Certainly not the case with Backbone; things got crazy
- But prepare yourself for the fact that it'll feel like you're writing "more code"

=====

# Sophisticated reconciler

### (aka Virual DOM)

NOTES:
- Here's where we talk about the killer feature of React
- Whenever anyone talks about React it's the cool feature they talk about
- Up until this point, it's looked like `render()` was rendering to the DOM
- But it's not...

/////

## React reconciler makes efficient updates easy

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
- Let's take our example from before...
- When we call `setState` React calls `render()` w/ updated state
- So it looks like are re-rendering the `<div>` + children each time
- When we know all we _really_ are updating is _just_ the `<span>` content
- This is where you should know that `render()` is updating DOM, but building up element hierarchy
- Basically a virtual representation of the DOM
- The reconciler (aka "Virtual DOM") keeps a copy of DOM, compares w/ newly rendered DOM and only updates changes
- We don't have to do the hard work of figuring out how to make the "micro updates"
- We can just write our code the easy way: like it re-renders everything
- And React does the hard work of figuring out micro updates

/////

## No reconciler in Backbone 😩

```
var IncrementerModel = Backbone.Model.extend({
  defaults: {value: 0}
})
var IncrementerView = Backbone.View.extend({
  template: Handlebars.compile($('#tempalte').html()),
  events: {
    'click .js-btn': 'increment'
  },
  initialize: function() {
    this.listenTo(this.model, 'change', this.render)
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
  },
  render: function() {
    this.$el.html(this.template(this.mode.attributes))
  }
})
```

NOTES:
- Here again is the equivalent Backbone code written to be "reactive"
- Probably not how it would normally be written; hard not to after knowing React
- It's really simple; `increment` updates model & `model` calls `render()`
- But this will actually re-render the whole template blowing away prev DOM
- This is super inefficient

/////

## Manual update in Backbone 😭

```
var IncrementerView = Backbone.View.extend({
  template: Handlebars.compile($('#tempalte').html()),
  events: {
    'click .js-btn': 'increment'
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
    $('.val').html(this.model.get('value'))
  },
  render: function() {
    this.$el.html(this.template(this.mode.attributes))
  }
})
```
<!-- .element: class="large" -->

NOTES:
- Instead of listening to model changes and re-rendering
- We should just update the `<span>` ourselves after updating the odel
- Full `render` would only be for the initial render
- This is fine for this simple case; nightmare when there are lots of events
- Confession: when I have to go back to Backbone I just do it the easy way!

/////

![Brace Yourselves - A live demo is coming](../../img/react-exposed/live-demo.jpg)
<!-- .element: style="width:70%" -->

NOTES:
- I've kinda talked about it, but lemme **show** you the benefits w/ a demo

/////

## Fiber Reconciler
<!-- .element: style="margin-bottom: 1em" -->

- Rewrite of reconciler
- Prioritizes UI updates
- Enables async rendering
- Improves perceived performance
- In recent major React version (v16)

NOTES:
- React recently released React 16, which included a complete rewrite of the reconciler now codenamed Fiber
- The Fiber reconciler can prioritize UI updates, which means that the UI can render asynchronously
- As a result we get greater perceived performance because the higher priority updates happen first
- And this is all happening in React 16 - the next major version

/////

![Stack reconciler](../../img/react-fiber/stack-reconciler.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## Stack reconciler

NOTES:
- The previous reconciler has been posthumously given the name Stack reconciler
- Basically when an update needs to happen, the Stack reconciler traverses the entire component tree and does all the rendering for as long as it takes
- Then it reliquishes control back to the JS engine
- For deep or expensive updates this can have a noticeable impact on performance even w/ intelligent reconciliation

/////

![Fiber reconciler](../../img/react-fiber/fiber-reconciler.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## Fiber reconciler

NOTES:
- Instead the forthcoming Fiber reconciler will do some work and then relinquish control back to the engine
- So rendering becomes asynchronous because it can render a higher priority update before returning to the original update
- Imagine you have a text input field and then long list of results being populated by API response
- You want typing to have immediate feedback where as the list of results can be lower priority because it's coming from API
- These sorts of optimizations give a higher perceived performance

/////

## Update Priorities

<br />

- Synchronous
- Task
- Animation
- High
- Low
- Offscreen

NOTES:
- Synchronous (just like stack reconciler)
- Task        (next tick)
- Animation   (before next frame)
- High        (pretty soon)
- Low         (delays are ok)
- Offscreen   (prep for display/scroll, not being rendered)

/////

## "Secret" code to enable (partial) async scheduling 🤐

<br />

- Open `node_modules/react-dom/cjs/react-dom.development.js`
- Replace "`fiberAsyncScheduling: false`" ➜ "`fiberAsyncScheduling: true`"

<br />

```
// make low-priority update
ReactDOM.unstable_deferredUpdates(() => {
  this.setState((state, props) => {
    // return updated state
  })
});
```
<!-- .element: class="large" -->

Source: [`react-fiber-resources`](https://github.com/koba04/react-fiber-resources#try-react-fiber-with-asynchronous-scheduling)

NOTES:
- Async scheduling is turned off in React 16
- Will be a opt-in feature flag to turn it on in future release
- But you can still try it out!
- First need to manually turn on async scheduling by turning on flag in `react-dom`
- Then you can use the unstable API `unstable_deferredUpdates` in `ReactDOM`
- This makes the `setState` a "low priority"
- Great for the results of API calls that can wait a bit
- Using `setState` updater function is even more important now
- `react-fiber-resources` has a sample app

/////

## React Fiber Synchronous Scheduling 😞 

<a href="https://twitter.com/koba04/status/854924460352192520">
  <img src="../../img/react-fiber/sync-browser-perf.jpg" alt="Screenshot of browser performance with sync Fiber scheduling" style="width: 50%" />
</a>

NOTES:
- `fiberAsyncScheduling: false`
- With a very heavy update
- You can go from a performance profile that looks like this
- Where the browser is spending so much time updating your UI that it can't do anything else
- To...

/////

## React Fiber Asynchronous Scheduling! 🤗

<a href="https://twitter.com/koba04/status/854924460352192520">
  <img src="../../img/react-fiber/async-browser-perf.jpg" alt="Screenshot of browser performance with async Fiber scheduling" style="width: 50%" />
</a>

NOTES:
- `fiberAsyncScheduling: true`
- This where the browser has time to come up for air
- This it really happening in a browser
- The super awesome feature of React is posed to get even better!

/////

## [Layperson's guide to React Fiber](http://www.benmvp.com/slides/2017/reactrally/fiber.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/q6QTxq_pFn0" frameborder="0" allowfullscreen></iframe>

### React Rally 2017

NOTES:
- Shameless plug alert!
- I gave a talk called _Layperson's guide to React Fiber_ at React Rally in August
- I talk a little bit about React Fiber and other goodies in React 16

=====

# Server-side rendering

### (aka "Isomorphic React")

NOTES:
- Let's talk about server-side rendering or "Isomorphic React"
- "Isomorphic JavaScript" or "Isomorphic React" is the idea of using the same templates rendered client-side on initial server render

/////

## "Isomorphic" vs. "Universal"

![Definition of isomorphic](../../img/react-sans-node/isomorphic-definition.png)
<!-- .element: style="width: 65%;" -->

![Definition of universal](../../img/react-sans-node/universal-definition.png)
<!-- .element: style="width: 65%;" -->

NOTES:
- _Isomorphic_ basically means two things that _look the same_, but actually _aren't the same_
- _Universal_ basically means that it works everywhere
- So when we talk about our components rendering client-side as well as server-side and React Native, _universal_ makes more sense
- But I actually still prefer "Isomorphic React" because it sounds cooler
- I feel like I sound smarter saying it

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
- Again, we're talking about the _initial_ render

/////

## React components only define WHAT to render!

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
- Let's return to our old friend the Incrementer component
- Up until this point I've kind of made it seem like `render()` was rendering to the DOM
- But that's not true!
- `render()` just informs what elements & child components should be rendered
- It doesn't dictate _how_ they should be rendered

/////

## DOM rendering happens at the root

```js
import React from 'react'
import ReactDOM from 'react-dom'
import App from './App'


ReactDOM.render(<App />, document.getElementById('root'))
```
<!-- .element: class="large" -->

NOTES:
- That typically happens in the entry point of your app
- You'll import from `react-dom` and use it's `render()` function
- Insert your app into the DOM location
- And then when your app updates a produces a new component hierarchy
- `react-dom` is what takes that difference and applies it to the DOM

/////

## Render to string server-side!

```js
import React from 'react'
import ReactDOMServer from 'react-dom/server'
import App from './App'


let markup = ReactDOMServer.renderToString(<App />)

// return `markup` in HTML response
```
<!-- .element: class="large" -->

NOTES:
- I bring up that distinction because that separation between building your UI and rendering to DOM...
- Allows for us to render the _exact same_ UI server-side to a string!
- This is such a huge feature!
- Before this, all UI libraries just assumed the DOM and you were manipulating DOM elements
- So getting your templates to run server-side was at best a pain; at worst in possible

/////

## Run your Node server in production mode!

![Chart outlining React 16 server-side rendering perf](../../img/react-fiber/ssr-perf-chart-updated.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 65%" -->

[github/aickin/react-16-ssr-perf](https://github.com/aickin/react-16-ssr-perf)

NOTES:
- Comparing Raw React 15, compiled React 15, and compiled React 16 beta 2
- Latest Node 4, 6 & 8
- 17x improvement just by upgrading systems
- At Eventbrite we didn't set `process.env=PRODUCTION` for like 6 months

/////

## Run your Node server in production mode! 🤦🏾‍♂️

![react-render-server render times after setting process.env](../../img/react-sans-node/rrs-node-env.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 85%" -->

🤣🤣🤣

NOTES:
- Can you guess when we turned on the env var?? 🤣
- 2x improvement just by adding that env variable
- We went through this so you don't have to!


/////

## First-class server-side streaming support! 🎉

```js
import {renderToNodeStream} from 'react-dom/server'

app.get('/', (req, res) => {
  res.write('<html><head><title>EB</title><body><div id="root">')

  renderToNodeStream(<App />)
    .pipe(res, {end: false})
    .on('end', () => {
      res.write('</div></body></html>')
      res.end()
    })
})
```
<!-- .element: class="large" -->

Prior art: [`react-dom-stream`](https://github.com/aickin/react-dom-stream)

NOTES:
- Even with speed-ups, rendering to string is still sub-optimal:
  0. Server can't send out response until entire HTML is created, so browsers can't paint until `renderToString` is finished
  0. Server has to allocate memory for entire HTML string
  0. Single call to `renderToString` can dominate CPU
- Speaking of React 16, React now supports server-side streaming!
- With streaming, the browser can render pages before entire response is finished
- Even further performance gains

/////

<div style="display:flex;align-items:center;justify-content:space-between;margin-top:5%">
    <div style="flex:0 0 40%;">
        <img
            src="../../img/react-sans-node/python.png"
            style="background:none;box-shadow:none;border:none;"
        />
    </div>
    <div style="flex: 0 0 5%;text-align:center">
        <h1>+</h1>
    </div>
    <div style="flex:0 0 45%;">
        <img
            src="../../img/react-sans-node/handlebars.png"
            style="background:none;box-shadow:none;border:none;width:100%"
        />
    </div>
</div>

([pybars](https://github.com/wbond/pybars3))

NOTES:
- At Eventbrite our backend is in Python/Django
- Currently solved the “dual rendering issue” using a lib called Pybars
- Our JS templates are written in Handlebars & Pybars converts the Handlebars into Python functions that return a string
- It's like what happens in the original JS
- Except it's super-duper slow because it was poorly written
- Tried to speed it up, but it was still like 10x slower than rendering in Django/Mako templates

/////

## [Isomorphic React sans Node??](http://www.benmvp.com/slides/2017/forwardjs/react-exposed.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/cAYMqBU7Qko" frameborder="0" allowfullscreen></iframe>

### Render Conf 2017

NOTES:
- Shameless plug alert!
- I gave a talk called _Isomorphic React sans Node??_ at Render Conf earlier this year
- Because backend is Django, makes server-side rendering w/ React a bit tricky
- But we created a small Node service just for rendering components
- Passed it the path to the component and its props and it would give back the HTML
- This talk goes into all of the nitty gritty details plus various gotchas

=====

# Testing

NOTES:
- The same component-based architecture that makes server-side rendering easy, also makes testing React easy
- Like any good UI lib/framework you wanna separate data logic from the UI
- The logic that help update state: utility functions, API, etc
- Vanilla Backbone was good at this; the Model architecture created a separation that was easily testable
- But when it came to testing UI logic: this markup should display based on a condition or a user action should call a handler
- Backbone like all the DOM-based UI libraries was bad
- And we made things worse by having global data stores and passing data between components with radios

/////

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

```
<Incrementer onIncrement={this._handleIncrement} />
```
<!-- .element: class="large" -->

NOTES:
- Again we have ol' faithful the `Incrementer` component
- Except this time after we click and update state, we also call `onIncrement` event handler prop
- At the bottom is an example of how you would call it
- We want to test the component's **public** API:
- The markup that it renders and the callback handlers it calls
- That's it! Don't want to test implementation details like `state` changes

/////

## Testing Render

```js
import {shallow} from 'enzyme'

it('renders a `.val`', () => {
  let wrapper = shallow(<Incrementer />)

  expect(wraper.find('.val')).toBePresent()
})
```
<!-- .element: class="large" -->

[Jest](https://facebook.github.io/jest/) + [Enzyme](http://airbnb.io/enzyme/) + [`jest-enzyme`]() = 😍

NOTES:
- We can test incrementer using Jest & Enzyme
- Here we're asserting that `Incremener` renders an element with `.val` class
- Enzyme has a jQuery-like interface for manipulating React components
- All w/o a browser
- "Rendering" is creating an enzyme wrapper
- Using Jest as the test framework; also created by Facebook
- `jest-enzyme` provides additional enzyme-specific assertions to Jest

/////

## Testing callbacks

```js
import {shallow} from 'enzyme';

it('renders a `.val`', () => {
  let onIncrement = jest.fn()
  let wrapper = shallow(<Incrementer onIncrement={onIncrement} />)
  let button = wrapper.find('button')

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
- Well with enzyme we can simulate clicking the button w/o running in a browser!
- And with Jest we can provide a mock function using `jest.fn()`
- Then we can assert things on that mock:
- How many times it was called (twice for 2 clicks)
- What arguments it was last called with (2)
- So we shouldn't inspect the `state` of the component (which would be 2)
- Instead we assert on the value in the handler (the public API)
- Being able to unit test like this is a game-changer

=====

# React Native

### (...and other renderers)

=====

# Unopionated

=====

# Miscellaneous

=====

## Recap

- Declarative JSX
- Component-driven
- All JavaScript*
- State-driven
- Sophisticated reconciler
- Server-side rendering
- Testing
- React Native
- Unopionated
- ...and more!

NOTES:
- Again these are the reasons **we** made the switch to React
- I'm sure there are plenty other great reasons as well

=====

## Additional resources

- [Babel REPL](https://babeljs.io/repl/)
- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite ES6+ coding styleguide](https://github.com/eventbrite/javascript/tree/master/es6)
- [Eventbrite React Testing Best Practices](https://github.com/eventbrite/javascript/blob/master/react/testing.md)


NOTES:

=====

![Aladdin Thanks](../../img/giphy/thanks-aladdin.gif)
<!-- .element: style="width: 35%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So that's it!
- Wanted to thank Nodevember for inviting me to share with you
- Let's celebrate them for putting on another great conference
- Thanks to Eventbrite too for sponsoring and flying me out
- We're hiring!
- Also thank YOU for attending and sticking around!
- My goal is for you to learn at least one thing you can take away to be a better dev
- Slides are available on Twitter and Blog
- Ask questions on Twitter, via email or AMA!
- Thanks and enjoy the rest of the conference!
