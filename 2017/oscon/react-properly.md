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
0. ES.next
0. Props
0. Rendering

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

## ES.next: Modules

```js
import React, {PropTypes, PureComponent} from 'react'
import Comment from './Comment'

// create CommentList component

export default CommentList
```
<!-- .element: class="large" -->

<br />

[_ECMAScript 6 Modules: the final syntax_](http://www.2ality.com/2014/09/es6-modules-final.html)

NOTES:
- Make full use of "ES.next" features
- ES6 modules being one of them
- Instead of using globals, AMD or CommonJS, use ES6 modules

/////

## ES.next: Classes

```js
// good
export default class MainComponent extends PureComponent {

}


// bad (uses React.createClass)
const MainComponent = React.createClass({

});
export default MainComponent
```
<!-- .element: class="large" -->

[_Learning ES6: Classes_](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Use ES6 classes instead of `React.createClass`
- This can be enforced by ESLint

/////

## ES.next: Spread Operator

[Spread operator with array literals](http://www.benmvp.com/learning-es6-parameter-handling/#spread-operator)

```js
let values = new Array(2, 3, 4)

let allValues = [1, ...values, 5] // [1, 2, 3, 4, 5]
```
<!-- .element: class="large" -->

<br />

[Spread operator with object literals](https://github.com/sebmarkbage/ecmascript-rest-spread) (Stage 3)

```js
let warriors = {Steph: 95, Klay: 82, Draymond: 79}
let newWarriors = {
    ...warriors,
    Kevin: 97
}
```
<!-- .element: class="large" -->

NOTES:
- In react maintaining immutability is important
- Meaning that you never modify an array or object directly
- Clone it and then modify
- Spread operator makes that super easy

/////

## [React + ES.next = ♥](http://www.benmvp.com/slides/2017/reactconf/react-esnext.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/jh_Qzi-yHU0" frameborder="0" allowfullscreen></iframe>

### ReactConf 2017

NOTES:
- I gave a talk call _React + ES.next = ♥_ at ReactConf 2017
- What I just talked about was just a small snippet of all the different features
- Feel free to watch the video (not now)

=====

## Props: API

```js
// good
class TextInput extends PureComponent {
    static propTypes = {
        type: PropTypes.string,
        defaultValue: PropTypes.string
    }
}

// bad (adds `propTypes` after class definition)
const TextInput = class extends PureComponent {

};

TextInput.propTypes = {
    type: PropTypes.string,
    defaultValue: PropTypes.string
};
```

[Public class fields](https://tc39.github.io/proposal-class-public-fields/) (Stage 2)

NOTES:
- Props help clearly define the component's API
- React doesn't require you to define `propTypes` for your props, but require that they are defined
- Use `static` class property syntax to define `propTypes`
- Also don't use ambiguous like `PropTypes.object` or `PropTypes.array`

/////

## Props: Boolean

```js
// good
export default class Banner extends PureComponent {
    static propTypes = {
        hideIcon: React.PropTypes.bool,
    }
    static defaultProps = {
        hideIcon: false,
    }
}

// bad (icon-related prop is mis-named such that default is true)
export default class Banner extends PureComponent {
    static propTypes = {
        showIcon: React.PropTypes.bool,
    }
    static defaultProps = {
        showIcon: true,
    }
}
```

NOTES:
- Name boolean `propTypes` for a component so that their default value is `false`
- This means that you may need to name a prop negatively so that its default value will be `false`

/////

## Props: Boolean

```js
// great
const Header = () => (
	<header>
		<Banner />
	</header>
)

// not-so-great
const Header = () => (
	<header>
		<Banner showIcon={false} />
	</header>
)
```
<!-- .element: class="large" -->

NOTES:
- This way, omitting a boolean value in the JSX using the component is the same as specifying the boolean value as `false`

/////

## Props: Initializing State

```js
// good
export default class Togglr extends React.Component {
    constructor(props, context) {
        super(prop, context);
        this.state = {visible: props.defaultVisible};
    }

    // rest of the component
}

// bad (confusingly-named prop)
export default class Togglr extends React.Component {
    constructor(props, context) {
        super(prop, context);
        this.state = {visible: props.visible};
    }

    // rest of the component
}
```

NOTES:
- In general, using props to generate state is an anti-pattern because it results in duplicate "sources of truth"
- But if your props is properly named to indicate that it's only used as seed data for the component's internally-controlled state, it's no longer an anti-pattern.
- We tend to prefix these types of props with `default*` to match the `defaultValue` prop React uses for input elements. `initial*` is also a good prefix.
- In the "bad" example, both `props` and `state` have a property called `visible`, which is very confusing.
- Should you use `this.props.visible` or `this.state.visible`. The one in `props` cannot change, while the one in `state` can.
- Naming the prop `defaultVisible` (as shown in the "good" example) makes things clearer.

=====

## Rendering: Logic & JSX

```js
// bad (expressions in JSX)
render() {
  let {includeHeader} = this.props;

  return (
    <div>
      {includeHeader ? (<h2>Pagination</h2>) : null}
      {[1, 2, 3, 4, 5].map((page) => (
        <Button
          key={page}
          onClick={this._handlePageClick.bind(this, page)}
		/>
      ))}
    </div>
  );
}
```

NOTES:
- React and JSX supporting logic and markup in the same file allows for substantial complexity in markup generation over other traditional templating languages
- But with that increased complexity can come a decrease in readability.
- I see a lot of code like this that has ternary operators, `map`s and other code mixed right in the JSX
- The above "bad" example doesn't seem so bad right?
- But as we know, code tends to grow over time.
- If we add more expressions, add more markup to the header, or the map gets more more logic, the code will become unwieldy.

/////

## Rendering: Logic & JSX

```js
// good
render() {
    let {includeHeader} = this.props;
    let buttons = [1, 2, 3, 4, 5].map((page) => (
        <Button key={page} onClick={this._handlePageClick.bind(this, page)} />
    ));
    let header;

    if (includeHeader) {
        header = (<h2>Pagination</h2>);
    }

    return (
        <div>
            {header}
            {buttons}
        </div>
    );
}
```

NOTES:
- In order to maximize both complexity and readability, we suggest keeping all logic out of JSX, except variable references and method calls.
- Expressions, particularly ternary expressions, should be stored in variables outside of JSX.
- Also using a bound reference to `_handlePageClick` instead of using an anonymous function in the JSX

/////

## Rendering: Helper Components

```js
// bad (longer, less maintainable render)
render() {
    let {allTlds, currentTld, seoLinks} = this.props;
    let seoItems = seoLinks.map( ... );
    let domainItems = allTlds.filter( ... ).map( ... );

    return (
        <div className="global-footer">
            <ul className="global-footer__site-links">
                <li><a href="/about">About</a></li>
                <li><a href="/blog">Blog</a></li>
                <li><a href="/help">Help</a></li>
                <li><a href="/careers">Careers</a></li>
            </ul>
            <ul className="global-footer__seo-links">
                {seoItems}
            </ul>
            <ul className="global-footer__domain-links">
                {domainItems}
            </ul>
        );
        </div>
    );
}
```
<!-- .element: class="small" -->

NOTES:
- Here we have a global footer containing:
- A section with links to important top-level pages
- Another section with links for SEO (😐)
- A section of links to all of your top-level domains (e.g., .com, .co.uk, etc.).
- There's actually a lot of logic driving the markup

/////

## Rendering: Helper Components

```js
// using arrow functions for stateless functions
const SiteLinks = () => (
    <ul className="global-footer__site-links">
        <li><a href="/about">About</a></li>
        <li><a href="/blog">Blog</a></li>
        <li><a href="/help">Help</a></li>
        <li><a href="/careers">Careers</a></li>
    </ul>
);
```
<!-- .element: class="small" -->

```js
// good (clean render w/ help of helper components)
render() {
    let {allTlds, currentTld, seoLinks} = this.props;

    return (
        <div className="global-footer">
            <SiteLinks />
            <SeoLinks links={seoLinks} />
            <DomainLinks allTlds={allTlds} currentTld={currentTld} />
        </div>
    );
}
```
<!-- .element: class="small" -->

NOTES:
- As you can see, with this best practice, the `render()` of `GlobalFooter` is really clean.
- It's immediately obvious that the global footer consists of site, SEO and domain links.
- The `GlobalFooter` is composed of these helper components in true React style.
- Furthermore, if more content is needed for a given section, it's easy for the developer to know where to add code, and `render()` of `GlobalFooter` doesn't need to grow.
- Use stateless functions instead of class declarations for these helper components.
- Because they are only useful to the main component and only exist to keep `render()` lean, don’t place these helper components in their own files, nor `export` them within the main component.

/////

## Rendering: Hiding Markup

```js
// bad (uses CSS to hide element instead of not rendering)
render() {
    let {visible} = this.state;
    let messageClassName;

    if (!visible) {
        messageClassName = 'hidden';
    }

    return (
        <div>
            <Button click={this._handleToggle.bind(this)}>Toggle!</Button>
            <p className={messageClassName}>
                This message is toggled on/off with CSS 🙁!
            </p>
        </div>
    );
}
```

NOTES:
- Typically when you want to conditionally hide markup you would update its style or add a class that'd hide it
- It's tempting to do the same thing in React, but it's not necessary!

/////

## Rendering: Hiding Markup

```js
// good
render() {
    let {visible} = this.state;
    let message;

    if (visible) {
        message = (
            <p>This message is toggled on/off with React not CSS!</p>
        );
    }

    return (
        <div>
            <Button click={this._handleToggle.bind(this)}>Toggle!</Button>
            {message}
        </div>
    );
}
```

NOTES:
- With React's optimized re-rendering via its Virtual DOM abstraction, you should never need to hide elements with CSS
- (except maybe with some sophisticated CSS animations).
- Instead, don't render the element when it shouldn't be visible, and render it when it should

=====

## Recap

0. Developer Tools
0. ESLint
0. ES.next
0. Props
0. Rendering

NOTES:
- So here's what we discussed
- Feel free to grab the slides

=====

## Additional resources

- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite React ESLint configuration](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)
- [Eventbrite ES6+ coding style guide](https://github.com/eventbrite/javascript/tree/master/es6)
- [_Learning ES6_ series](/learning-es6-series/)

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
