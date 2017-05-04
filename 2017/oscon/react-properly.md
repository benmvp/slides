# React Properly

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#OSCON](https://twitter.com/hashtag/OSCON)    

<br />

May 10, 2017  

NOTES:
- My name is Ben Ilegbodu

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
  "work": "Eventbrite",
  "role": "Engineering Manager",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/family-tahoe-beach-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family on the beach at Lake Tahoe" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

<!-- .slide: data-background="url(../../img/giphy/james-harden-pot-cook.gif) no-repeat center" data-background-size="contain" -->

NOTES:
- I also absolutely love basketball - both playing & watching
- But you didn't come to hear about me. At least I hope not

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently an Engineering Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- Historically we've just been a ticketing platform, but moving to being an events destination
- I am the engineering manager of that team
- Previously I was on the Frontend Platform team and where we transitioning Eventbrite from Backbone to React
- Didn’t want to introduce immediate tech debt from people ramping up
- Reviewed dozens of coding exercises written in React which showed how poorly code can be written in a hurry :)
- Instituted from the beginning React best practices (which we modified over time)
- Best practices helped level up our team in React
- Target audience: those who have done a little bit of React dev

=====

## What this talk is **not** about... 😐

<br />

- Why to use React
- How to develop in React
- How to transition from Backbone to React

NOTES:
- Just so we're clear...

/////

## What this talk is about! 😄

<br />

- Overview of Eventbrite React coding styleguide
- Lots of code examples
- Fast-paced!

NOTES:
- However!

/////

## Just to be clear...

[![Tweet from Dan Abramov about no React rules](../../img/react-properly/no-react-rules-tweet-dan-abramov.png)](https://twitter.com/dan_abramov/status/760871101526310912)

NOTES:
- These are guidelines and rules that **we** at Eventbrite have adopted
- They are not hard fast rules
- But if you're looking coding best practices this may be a great place to start


=====

## Agenda

0. Developer Tools
0. ESLint

NOTES:

=====

## React Developer Tools

![React Developer Tools Chrome screenshot](../../img/react-properly/react-developer-tools.jpg)
<!-- .element: style="width: 55%" -->

Available for [Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en) and [Firefox](https://addons.mozilla.org/en-US/firefox/addon/react-devtools/)

NOTES:
- Before we start looking at code, gotta suggest React DevTools
- It's a debugging lifesaver

=====

## ESLint

<div style="display:flex;align-items:center;justify-content:space-around;">
    <img src="../../img/nav-react/eslint-logo.svg" style="background:none;box-shadow:none;border:none;width:30%"/>
    <div>
		<h2>Prevent errors</h2>
		<h2>Enforce style</h2>
        <h2>Promote a11y</h2>
    </div>
</div>

Extend Eventbrite’s [React ESLint Config](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)!

NOTES:
- Definitely definitely use ESLint rules
- Keeps code syntax consistent so folks new to code can focus on code logic instead of code style
- Great async teaching tool for best practices because violating them causes failures
- Enforcing style (like no empty tags)
- Preventing errors (using `class` instead of `className`)
- Promoting a11y (ensuring ARIA roles are correct)
- Try our best to have all style rules enforced by ESLint

/////

## ESLint: Errors

```js
const HelloWord = () => (
	<div class="hello">Hello World</div>
)
```
<!-- .element: class="large" -->

<br /><br />

```
Unknown property 'class' found, use 'className' instead (react/no-unknown-property)
```

[`react/no-unknown-property`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/no-unknown-property.md)

NOTES:
- So helpful in catching little bugs, especially when the linter is incorporated in IDE

/////

## ESLint: Style

```js
class MyComponent extends PureComponent {
	static propTypes = {
		style: PropTypes.string
	}

	state = {value: ''}

	componentDidMount() { }
	componentWillReceiveProps() { }
	componentWillUnmount() { }

	_helperMethod() { }

	render() {
		return (<div />);
	}
}
```

[`react/sort-comp`](https://github.com/yannickcr/eslint-plugin-react/blob/master/docs/rules/sort-comp.md)

NOTES:
- For example, We use the `react/sort-comp` eslint rule to ensure that our components are organized in a consistent way
- `static` propTypes are always first
- Then `state`
- The lifecycle methods in a specific order
- Any other helper methods
- And finally `render()` is always last

/////

## ESLint: Style

```js
class MyComponent extends PureComponent {
	render() {
		return (<div />);
	}

	static propTypes = {
		style: PropTypes.string
	}

	...

	_helperMethod() { }
}
```
<!-- .element: class="large" -->

```
render should be placed after _helperMethod (react/sort-comp)
```

NOTES:
- So if I decided to put `render()` first like I've seen some folks doing, it'll complain
- Keeps code syntax consistent so folks new to code can focus on code logic instead of code style

/////

## ESLint - A11y

```js
const ClickableThang = ({onAction}) => (
	<div onClick={onAction}>
		Do the thang
	</div>
)
```
<!-- .element: class="large" -->

<br /><br />

```
Visible, non-interactive elements with click handlers
must have role attribute. (jsx-a11y/no-static-element-interactions)
```

<br />

[`jsx/a11y/no-static-element-interactions`](https://github.com/evcohen/eslint-plugin-jsx-a11y/blob/master/docs/rules/no-static-element-interactions.md)

NOTES:
- I'll take a wild guess and say that most developers don't know the ends and outs of making an app accessible
- Well ESLint rules can help with some of the baseline things
- For instance clickable elements _should_ only be interactive elements like `<button>` but we're notorious for sticking `onclick` on `<div>`
- If we do, for a11y among other things it needs to have the proper ARIA role to indicate that it is playing the role of a button

/////

[![Tweet from Cory House on ESLint benefits](../../img/react-properly/eslint-benefits-cory-house.png)](https://twitter.com/housecor/status/857591914727694336)

NOTES:
- Speaking of new JavaScript features...

=====

## Recap

0. Developer Tools
0. ESLint

NOTES:
- So here's what we discussed
- Feel free to grab the slides

=====

## Additional resources

- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite React ESLint configuration](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)

=====

![Usain Bolt Thumbs Up](../../img/giphy/usain-bolt-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

NOTES:
- So some quick shoutouts before I wrap

/////

![DeveloperWeek 2016 logo](../../img/mobile-web-devcon-logo.png)
<!-- .element: style="width: 60%; border: 0; background: none; margin: 0; box-shadow: none;" -->

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
