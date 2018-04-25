# Why we choose React at Eventbrite

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@evbeng](https://twitter.com/evbeng)

<br />

April 25, 2018

NOTES:
- My name is Ben Ilegbodu
- It was over 2 years ago that we mbarked on the journey of transitioning our frontend from Backbone to React
- So this talk is about the first part of that transition: convincing everyone that it was a good idea 😀
- Wanna pull back the covers on the rationales we used to make that switch
- Most ofo you are familiar with Backbone so hopefully this will explain the advantages of React
- This is a "polished" presentation, but I'm hoping we'll stop many times with questions
- Posted link to slides on twitter if you want to follow along

=====

[![Tweet from Jordan Harband about how people are hard](../../img/why-react/jordan-harband-people-are-hard.png)](https://twitter.com/ljharb/status/927606717793296384)

NOTES:
- I've been in the industry for about a dozen years now
- And I've come to realize that software development isn't just the code you commit
- There's an equally important human element to it
- Whenever doing something buy-in is just as important as the technical approach
- When difficulties arise, it can be the difference between folks complaining or rallying to find a
  solution, is buy-in

/////

<a href="https://docs.google.com/document/d/1fOvODYnaEngqFhVf1nbmN9hejj5a4L4J64_zk5qGu9k/edit?usp=sharing">
  <video data-autoplay loop style="width: 55%">
    <source data-src="../../img/why-react/eventbrite-why-react-doc.m4v" />
  </video>
</a>

NOTES:
- We had actually tried React a couple of times, ran into issues, and people concluded "React is no good"
- So this time, in early 2016, I put together a loooong 19-page document to explain why our Frontend Platform team thought we should make the switch
- And as I said "cuz everybody is using it!" wasn't a good enough reason 😉
- The rest of the talk is a talk-friendly distillation of that doc

=====

# CORE STUFF
<!-- .element: class="title" -->

NOTES:
- Split this up into 2 main sections
- Start off with the Core Stuff
- Core ones will apply to everyone using React
- Part of the core React lib

=====
<!-- .slide: data-background="#222" -->

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

## Markup, logic & data are together

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
- But we're returning the JSX w/in `render()` as if it's a regular object
- So markup is in the JavaScript right there with the logic
- So everything is together, which was very different than traditional MVC like Backbone

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

<div class="code-highlight" style="height: 80px; top: 333px"></div>

NOTES:
- This is the traditional MVC equivalent in Backbone
- You have a separate file for the template (markup) as well as model & view (logic)
- Nice things: a non-JS expert could come in and make changes in a familiar env
- We used `js-*` prefix in our templates to safely reference them in JavaScript

/////

## Traditional MVC equivalent

Backbone Model & Marionette View

```
var template = require('hb!./incrementer.handlebars');
var IncrementerModel = Backbone.Model.extend({
  defaults: {value: 0}
})
var IncrementerView = Marionette.ItemView.extend({
  template: template,
  ui: {
    incrementButton: '.js-btn'
  },
  events: {
    'click @ui.incrementButton': 'increment'
  },
  modelEvents: {
    'change': 'render'
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
  }
})
```

<div class="code-highlight" style="height: 316px; top: 439px"></div>

NOTES:
- Here's the logic
- Focusing on how the view connected with the template
- The idea is that we wanted to have a "separation of concerns"
- But it didn't happen in practice
- But it was really "separation of technologies"
- But when the template changed, you needed to change the view
- When the model changed, you needed to change the template, and so on
- What we found was, as things got complex, hard to know the effects changing one would have on the other

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

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

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
export default class FormField extends React.Component {
  render() {
    const id = this.props.id
    return (
      <div>
        <Label inputId={id}>{this.props.label}</Label>
        <TextInput
          id={id}
          value={this.props.value}
          onChange={this.props.onChange}
        />
      </div>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 80px; top: 253px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 423px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 594px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 654px"></div>


NOTES:
_click through code highlights_

- The sole way you build your UI in React is with "custom" components
- Everything is a component!
- And you build bigger components by combining smaller components w/ markup
- One way we create components is by creating a `class` and extending from `React.Component`
- The component has a `render()` method which is where you define the UI & return JSX
- Here we have a `FormField` component made up of already defined `Label` & `TextInput` components
- Props are how a component is configured; it's an object
- **Click through props:** `FormField` defines 4 `props` (`id`, `label`, `value` & `onChange`)
- It lays out the `Label` & `TextInput` w/in `<div>` and then passes along those props as configuration

/////

## Everything is a component!

```js
import FormField from './FormField'
export default class NameForm extends React.Component {
  render() {
    return (
      <form onSubmit={this._handleSubmit}>
        <FormField
          id="fName"
          label="First"
          value={this.props.fields.fName}
          onChange={this.props.onFieldChange.bind(null, 'fName')}
        />
        <FormField id="lName" ... />
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

/////

## Everything is a component!

```js
import NameForm from './NameForm'

export default class App extends React.Component {
  _handleFieldChange = (fieldName) => {
    // Do something
  }

  render() {
    return (
      <NameForm
        fields={ {fName: 'Ben', lName: 'Ilegbodu'} }
        onFieldChange={this._handleFieldChange}
      />
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- And keep doing that until you have a full-fledged app
- `App` contains `NameForm` component
- And probably would contain other big components as well: header, footer, navigation, etc.

/////

<div style="display:flex;align-items:center">
	<div style="flex:0 0 50%;">
    <a href="http://backbonejs.org/" target="_blank">
		  <img src="../../img/react/backbone-logo.png" style="width:100%;height:auto;border:0;background:none;box-shadow:none;" alt="Backbone.js logo" />
    </a>
	</div>
	<div style="flex:0 0 50%;">
    <a href="https://marionettejs.com" target="_blank">
		  <img src="../../img/react/marionette-logo.svg" style="width:100%;height:auto;border:0;background:none;box-shadow:none;" alt="Marionette logo" />
    </a>
	</div>
</div>

NOTES:
- Component-driven development seems pretty obvious right?
- All the modern libraries/frameworks are component-driven in their own way
- But not Backbone; you simply could not nest Backbone views
- At Eventbrite, we began to use Marionette; an architecture layer on top of Backbone to help w/ more complex UIs
- The version we were using had Layouts, which could contain Views, which could _be_ layouts so nesting was possible
- But it was not nearly as effortless as what I just showed w/ React
- Configuring the nested views wasn't simple either
- Way too much code to try to put on a slide
- The problem was that the idea of "components" was an add-on in Backbone/Marionette
- As opposed to being a core feature w/ React

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

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
- Traditional UI frameworks, like Backbone, are driven by markup
- You create your markup templates separately and then layer interactivity in JS with the framework
- And doing any kind of fancy logic in the template got really, really messy
- Plus we'd basically have to basically learn a new language
- At Eventbrite we registered Handlebars "helpers" so we could call functions in templates
- _explain what is happening_
- Alternative is to do a whole lot of pre-computation in the view to enable the template to be dumb
- Ya know, handlebars didn't even have `else-if`
- So we'd have a nested `if` w/in an `else`'
- Handlebars was so simplistic in its language that it made Backbone a pain to use


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

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

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
<div class="code-highlight fragment current-visible" style="height: 80px; top: 704px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 764px"></div>
<div class="code-highlight fragment current-visible" style="height: 190px; top: 313px"></div>
<div class="code-highlight fragment current-visible" style="height: 80px; top: 704px"></div>

NOTES:
_click through code highlights_

- Contrast this with the React code equivalent
- Simplest example of reactivity in React
- **First:** Start off with initial state
- **Second:** Then we render UI based on state (and props)
- **Third:** Handle user click of `+` button
- **Fourth:** Take the previous value of the state (`0`), increment by 1 and then update the state (`setState`)
- It's the handler that does the logic of incrementing the value; separation of concerns!
- And since `value` is already in `state` we don't have to get it from the DOM
- **Fifth:** Then calling `setState` causes `render` to be called again
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
- **Skill:** Ability to build layouts with HTML & CSS
- 2/ When events happen, do stuff to transform data to generate new `state` (and `render` again)
- Can also do async transformation by making API calls
- **Skill:** Ability to transform data efficiently; algorithms are really handy
- And the loop continues

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

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

<div class="code-highlight fragment current-visible" style="height: 70px; top: 370px"></div>
<div class="code-highlight fragment current-visible" style="height: 240px; top: 655px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 715px; left: 875px; width: 530px"></div>

NOTES:
_click through code highlights_

- Let's take our example from before...
- **First:** When we call `setState`...
- **Second:** React calls `render()` w/ updated state
- So it looks like are re-rendering the `<div>` + children each time
- **Third:** When we know all we _really_ are updating is _just_ the `innerHTML` of `<span>`
- `render()` is **not** updating DOM, but building up element hierarchy
- Basically a _new_ virtual representation of the DOM
- The reconciler (aka "Virtual DOM") keeps a copy of DOM, compares w/ newly rendered DOM and only updates changes
- So we don't have to do the hard work of figuring out how to make the "micro updates"
- We can just write our code the easy way: like it re-renders everything
- And React does the hard work of figuring out micro updates
- This is _really_ _really_ nice

/////

## No reconciler in Backbone 😩

```
var IncrementerView = Marionette.ItemView.extend({
  template: template,
  ui: {
    incrementButton: '.js-btn'
  },
  events: {
    'click @ui.incrementButton': 'increment'
  },
  modelEvents: {
    'change': 'render'
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
  }
})
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 483px"></div>
<div class="code-highlight fragment current-visible" style="height: 180px; top: 773px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 654px"></div>

NOTES:
_click through code highlights_

- Here again is the equivalent Marionette code written to be "reactive"
- Probably not how it would normally be written; hard not to after knowing React
- It's pretty straightforward
- **First:** Clicking button calls `increment()`
- **Second:** `increment()` updates model
- **Third:** All `model` changes calls `render()`
- But this will actually re-render the whole template blowing away prev DOM
- This is super inefficient especially for bigger chunks of DOM; will get flashes

/////

## Manual update in Backbone 😭

```
var IncrementerView = Marionette.ItemView.extend({
  template: template,
  ui: {
    incrementButton: '.js-btn',
    value: '.val'
  },
  events: {
    'click @ui.incrementButton': 'increment'
  },
  increment: function() {
    this.model.set({value: this.model.get('value') + 1})
    this.ui.value.html(this.model.get('value'))
  }
})
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 772px"></div>

NOTES:
- Instead of listening to model changes and re-rendering
- We _should_ just update the `innerHTML` of the `<span>` ourselves after updating the model
- Full `render` would only be for the initial render
- This is fine for this simple case; very easy to follow
- Nightmare when there are lots of events & states
- Confession: when I _have_ to go back to Marionette I just do it the easy way!
- If you see some UI flashing on Eventbrite, I may be to blame 😂

**[ASK ABOUT QUESTIONS]**

=====

# MORE STUFF
<!-- .element: class="title" -->

NOTES:
- So those were the Core Motivations
- The ones that will apply to everyone because they are part of the core lib

- Now let's jump into some additional motivations
- They applied to us at Eventbrite, but _may_ not apply to your situation

=====
<!-- .slide: data-background="#222" -->

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
- SEO: Google doesn't have to execute your JS to get meaningful data + they includes page render speed in ranking algorithm
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
- **First:** You'll import from `react-dom`
- **Second:** Then use it's `hydrate()` function (new to React 16)
- Inserts your app into the DOM location
- When your app updates, it produces a new component hierarchy
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
- Our JS templates are written in Handlebars & Pybars converts the Handlebars into Python functions
  that return a string
- It's like what happens in the original JS
- Except it's super-duper slow because it was poorly written
- Tried to speed it up, but it was still like 10x slower than rendering in Django/Mako templates

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div>
      <h1>7. Testing</h1>
    </div>
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/homer-simpson-walk-away.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Homer simpson slowly walks away" />
    </div>
</div>

NOTES:
- The same component-based architecture that makes server-side rendering easy, also makes testing React components easy
- Since Backbone views were directly manipulating the DOM, they were hard to test
- Pretty much had to run tests in a browser or headless browser which brought a host of issues
- So the 7th reason for transition is about making testing life far simpler

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
- We want to test the component's **public** API only:
- The markup that it renders and the callback handlers it calls
- That's it! Want to avoid testing implementation details like `state` changes

/////

## Testing Render

```js
import {mount} from 'enzyme'

it('renders a `.val`', () => {
  const wrapper = mount(<Incrementer />)

  expect(wraper.find('.val')).toBePresent()
  expect(wrapper.find('.val')).toHaveText('0')
})
```
<!-- .element: class="large" -->

[Jest](https://facebook.github.io/jest/) + [Enzyme](http://airbnb.io/enzyme/) +
[`jest-enzyme`](https://yarnpkg.com/en/package/jest-enzyme) = 😍

<div class="code-highlight fragment current-visible" style="height: 70px; top: 430px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 485px"></div>

NOTES:
_click through code highlights_

- We can test `Incrementer` using Enzyme to test the public API
- Enzyme has a jQuery-like interface for manipulating React components _all without a browser_
- "Rendering" is creating an enzyme wrapper
- We use Jest as the test framework & assertion lib; also created by Facebook
- `jest-enzyme` provides additional enzyme-specific assertions to Jest
- **First:** Here we're asserting that `Incremener` renders an element with `.val` class
- **Second:** And that that `.val` element has the text "0" inside of it

/////

## Testing callbacks

```js
import {mount} from 'enzyme'

it('calls `onIncrement` prop with current value', () => {
  const onIncrement = jest.fn()
  const wrapper = mount(<Incrementer onIncrement={onIncrement} />)
  const button = wrapper.find('button')

  // simulate clicking twice
  button.simulate('click')
  button.simulate('click')

  expect(onIncrement).toHaveBeenCalledTimes(2)
  expect(onIncrement).toHaveBeenLastCalledWith(2)
  expect(wrapper.find('.val')).toHaveText('2')
})
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 317px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 373px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 593px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 771px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 829px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 886px"></div>

NOTES:
- If you recall, when we click the button we call our `onIncrement` handler
- We want to verify that when we click the button that `onIncrement` gets called w/ the right parameter
- Well with enzyme we can simulate clicking the button w/o running in a browser!
- **First:** First with Jest we can create a mock function using `jest.fn()`
- **Second:** Then we pass that mock function as `onIncrement` when we shallow render the component
- **Third:** Then we simulate clicking button inside `Incrementer`
- Then we can assert things on that mock:
- **Fourth:** How many times it was called (twice for 2 clicks)
- **Fifth:** What arguments it was last called with (2)
- Again: we shouldn't inspect the `state` of the component (which would be 2)
- Instead we assert on the value in the handler (the public API)
- **Sixth:** Lastly we can assert that the display value has been updated
- Being able to unit test like this is a game-changer
- We don't even really bother in Backbone/Marionette

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

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
- Ticketea uses React Native for their mobile apps!

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

<div class="code-highlight" style="height: 240px; top: 655px"></div>


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
        <Text style={...}>{this.state.value}</Text>
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
- You've got the makings of a native app!
- I remember when I went to a React Native workshop and was blown away
- Everything I learned building React web apps, I could leverage in React Native
- Just like w/ the web there are special considerations for native of course
- For instance, layout engine is different
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

**[ASK ABOUT QUESTIONS]**

=====
<!-- .slide: data-background="#222" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
    <div style="flex: 0 0 50%">
      <img src="../../img/giphy/omg-taco.gif" style="width:100%;height:auto;border: 0; background: none; margin: 0; box-shadow: none;" alt="Taco goes from one woman's mouth to the next" />
    </div>
    <div>
      <h1>9. Miscellaneous</h1>
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

**[ASK ABOUT QUESTIONS]**

=====

## Recap

<ol style="margin-right: 1em">
  <li>Declarative JSX</li>
  <li>Component-driven</li>
  <li>All JavaScript*</li>
  <li>State-driven</li>
  <li>Sophisticated reconciler</li>
</ol>

<ol start="6">
  <li>Server-side rendering</li>
  <li>Testing</li>
  <li>React Native</li>
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

## Eventbrite Design System

<a href="https://admin.evbqa.com/admin/eds/">
  <video data-autoplay loop style="width: 80%">
    <source data-src="../../img/why-react/eventbrite-design-system.m4v" />
  </video>
</a>

NOTES:
- It's filled with dozens of React components big and small
- But it's more than a component library; it's a design system
- Talks about _why_ components should be used, etc

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

![Jack Sparrow Thanks](../../img/giphy/thanks-jack-sparrow.gif)
<!-- .element: style="width: 50%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)

[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So before I close...
- My goal is for you to learn at least one thing you can take away to be a better dev
- Hopefully if you are in the same boat of wanting to transition, you've got some good material
- Slides are available on Twitter and Blog
- Would love to hear from you about things that were unclear, wanna know more about or general questions
- Ask on Twitter, via AMA or email
