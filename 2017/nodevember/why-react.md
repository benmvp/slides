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
- I gave a talk call _React exposed! 😮_ at ForwardJS earlier this year
- I go through several JSX gotchas among other topics
- Feel free to watch the video (not now)

=====

# Component-driven

=====

# All JavaScript*

=====

# State-driven

=====

# Sophisticated reconciler

### (Virual DOM)

=====

# Server-side rendering

=====

# Testing

=====

# React Native

### (...and other renderers)

=====

# Unopionated

=====

# Other stuff...

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
