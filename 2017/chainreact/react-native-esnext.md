# React Native + ES.next = ♥

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ChainReact2017](https://twitter.com/hashtag/ChainReact2017)    

<br />

July 10, 2017  

NOTES:
- My name is Ben Ilegbodu
- Here to talk about React Native + ES.next
- ES.next = ES2015 and beyond

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

# Stand Up!
<!-- .element: style="-webkit-text-stroke: black 4px; color: white" -->

NOTES:
- But first, would like everyone to stand up!
- Let's do 10 squats
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
		<img src="../../img/family-tahoe-beach-mountain.jpg" style="width:100%;height:auto" alt="Ilegbodu family on the beach at Lake Tahoe" />
	</div>
</div>

NOTES:
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently an Engineering Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Probably used Eventbrite before, but because an organizer told you to buy your tickets on Eventbrite
- This conference is using Eventbrite, so thank you very much :)
- But I'm leading the team tasked with making Eventbrite a Destination

/////

## Backstory

<br />

- [Jul 2015] [_Learning ES6 series_](http://www.benmvp.com/learning-es6-series)
- [Jan 2016] [React official tutorial (original)](https://github.com/facebook/react/blob/8cac523beaaacfeae179ca14a1d8a46d82892016/docs/docs/tutorial.md)
- [Nov 2016] [React Native Express](http://www.reactnativeexpress.com/) training course by [Devin Abbott](https://twitter.com/devinaabbott)

NOTES:
- Two years ago (Jul 2015) I began learning ES6 by writing a blog series called _Learning ES6_
- 6 months later (Jan 2016) I began learning React starting w/ the official tutorial
- It was the comments app still written in ES5 back then, but rewrote in ES6 to apply knowledge
- End of last year (Nov 2016) took a React Native workshop from Devin Abbott
- Blew my mind how React Native was just like React, just in a different environment
- Outside of JSX, React is just JavaScript, so naturally ES.next (future JavaScript) will apply well
- Given ES.next & React go well together, and React & React Native are very similar
- I’m going to spend time talking about how ES.Next & React Native go so well together


=====

## Agenda

<br />

0. Destructuring
0. Arrow functions
0. Spread operator
0. Classes

NOTES:
- Here's the agenda
- Focusing on the features you're most likely to use while building UI in React Native
- As opposed to features for APIs/Redux/etc
- Wish I could talk about everything but that's 40+ features
- Reason picking these 5 features is because they'll help write clear & concise code
- They target a wide range of audiences
- We'll see other features along the way that I will explain quickly

/////

![Chain React Conference App Ad](../../img/react-esnext/chain-react-app-ad.jpg)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 75%" -->

[github/infinitered/ChainReactApp](https://github.com/infinitered/ChainReactApp)

NOTES:
- All of the examples I'll show come from the Chain React Conference app
- Some of the examples are code "improvements"; what I thought should've been done
- Others are just explaining how you get to the ES.next from ES5
- I considered submitting a "code improvements" PR
- But didn't wanna be _that_ guy nor get uninvited to speak 😉

/////

![Lebron gets hit in head with basketball](../../img/giphy/lebron-head-basketball.gif)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 50%" -->

NOTES:
- I gave my first ES6 talk in October 2015 right after the ES2015 spec was released, and 2 years later speaking on it
- Some people know everything & others know absolutely nothing
- For some of you, a lot of what I'll talk about will be new, and that's ok
- Others will know the core concepts, but I hope to remind of details
- There'll be some of you who have been doing it longer than me that will know most of this stuff
- Hoping there's at least one thing that maybe you forgot or hadn't used it in a way
- But even if you do know **EVERYTHING** you can teach others!








=====

![Chain React Conf App Schedule Screen](../../img/react-esnext/chain-react-schedule-screen.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 30%" -->

NOTES:
- First feature relates to the Schedule Screen
- It has a list of the talks happening today and tomorrow

/////

```js
// Containers/ScheduleScreen.js
render() {
  return (
    <PurpleGradient style={styles.linearGradient}>
      <DayToggle activeDay={activeDay} />
      <FlatList
        data={data}
        extraData={this.props}
        renderItem={this.renderItem}
        keyExtractor={(item, idx) => item.eventStart}
        contentContainerStyle={styles.listContent}
        showsVerticalScrollIndicator={false}
      />
    </PurpleGradient>
  )
}
```
<!-- .element: class="large" -->

NOTES:
- Rendering a `FlatList` component to display talks and breaks
- We'll talk more about this `render()` method later when we discuss classes
- Connects to the `data` that's in state
- Each talk itself is rendered via `renderItem`

/////

```js
// Containers/ScheduleScreen.js

renderItem(info) {
  // create vars from properties in `state`
  let currentTime = this.state.currentTime
  let isCurrentDay = this.state.isCurrentDay

  // create vars from properties in `info.item`
  let eventType = info.item.type
  let eventStart = info.item.eventStart
  let eventEnd = info.item.eventStart

  // render <Talk /> or <Break /> component
}
```
<!-- .element: class="large" -->

NOTES:
- And that's where the fun happens
- A non ES.next implementation may look something like this
- We're pulling lots of properties out of `state` and `info.item` param to create variables
- Helps code below be more redable with out constantly dereferencing those objects
- BTW - using `let` keyword instead of `var` that came with ES6

/////

# Destructuring

Replace multiple assignments with a single one

<br />
<br />

[_Learning ES6: Destructuring_](http://www.benmvp.com/learning-es6-destructuring/)

NOTES:
- It's called Destructuring
- With destructuring we can reduce multiple assignments down to one
- Be advised, destructuring is probably the most "out there" syntax addition
- It's ok if you don't understand it at first

/////

<!-- .slide: data-background="url(../../img/giphy/i-hate-you-brad-pitt.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I'm afraid that after we cover destructuring, you'll feel like this...
- Really just shooting the messenger
- But stick with me...

/////

<!-- .slide: data-background="url(../../img/giphy/brad-pitt-dancing.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- Eventually I think you'll be super excited about them

/////

"DRY-er" assignment!

```js
renderItem(info) {
  let {currentTime, isCurrentDay} = this.state
  let {type: eventType, eventStart, eventEnd} = info.item
}
```
<!-- .element: class="large" -->

-----

##### Before

```js
renderItem(info) {
  let currentTime = this.state.currentTime
  let isCurrentDay = this.state.isCurrentDay

  let eventType = info.item.type
  let eventStart = info.item.eventStart
  let eventEnd = info.item.eventStart
}
```
<!-- .element: class="large" -->

NOTES:
- Uses object literal pattern
- Removes the duplication of `this.state` & `info.item`
- We can also create a differently named variable
- This is more or less how the actual code looks like

/////

Nested destructuring!

```js
renderItem(info) {
  let {currentTime, isCurrentDay} = this.state
  let {item: {type: eventType, eventStart, eventEnd}} = info
}
```
<!-- .element: class="large" -->

-----

##### Previous

```js
renderItem(info) {
  let {currentTime, isCurrentDay} = this.state
  let {type: eventType, eventStart, eventEnd} = info.item
}
```
<!-- .element: class="large" -->

NOTES:
- Previously we were still doing `info.item`
- So we can changed that to be a nested destructuring pattern!
- Just taking the pattern from before, but nesting it w/in `item`

/////

Destructured parameters!

```js
renderItem({item: {type: eventType, eventStart, eventEnd}}) {
  let {currentTime, isCurrentDay} = this.state
}
```
<!-- .element: class="large" -->

-----

##### Previous

```js
renderItem(info) {
  let {currentTime, isCurrentDay} = this.state
  let {item: {type: eventType, eventStart, eventEnd}} = info
}
```
<!-- .element: class="large" -->

NOTES:
- Now it's clear precisely what properties of the `info` param are needed
- `info` isn't even available
- Even with the inline destructuring, someone could still dereference `info` or `info.item` later

/////

### After

```js
renderItem({item: {type: eventType, eventStart, eventEnd}}) {
  let {currentTime, isCurrentDay} = this.state
}
```
<!-- .element: class="large" -->

-----

### Before

```js
renderItem(info) {
  let currentTime = this.state.currentTime
  let isCurrentDay = this.state.isCurrentDay

  let eventType = info.item.type
  let eventStart = info.item.eventStart
  let eventEnd = info.item.eventStart
}
```
<!-- .element: class="large" -->

NOTES:
- Look how much more concise are code is with using destructuring!
- To be honest, the new syntax takes a lot of time to get used
- Way more curly braces in places you wouldn't expect to see them
- But I think the conciseness & clarity is worth it







=====

![Chain React Conf App Location Screen](../../img/react-esnext/chain-react-location-screen.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 30%" -->

NOTES:
- Next feature is on the location screen of the app
- There's a map that you can pan around on

/////

```js
// Containers/LocationScreen.js

componentWillMount() {
  this._panResponder = PanResponder.create({
    onStartShouldSetPanResponder: function() { return true },
    onPanResponderGrant: function(e) { 
	  this.setState({mapTouchStart: e.nativeEvent.timestamp})
	}.bind(this),  // pass in proper `this` context
    onPanResponderRelease: this.checkMapTap.bind(this)
  })
}
```
<!-- .element: class="large" -->

Anonymous function + ES5 `bind` is so clunky for getting proper [`this`](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Operators/this)!

NOTES:
- So naturally we'll be using `PanResponder`
- A non ES.next implementation might look like this
- The `PanResponder` exposes lots of events which we handle with function callbacks
- It's pretty verbose!
- I especially dislike having to `.bind` the `onPanResponderGrant` handler to pass proper this
- This isn't how the original code was written

/////

# Arrow functions

Replace anonymous functions with arrow functions

<br />
<br />

[_Learning ES6: Arrow functions_](http://www.benmvp.com/learning-es6-arrow-functions/)

NOTES:
- With arrow functions we can stop using anonymous functions

/////

Arrow functions works how you would expect!

```js
this._panResponder = PanResponder.create({
  onStartShouldSetPanResponder: () => true,
  onPanResponderGrant: (e) => { 
	this.setState({mapTouchStart: e.nativeEvent.timestamp})
  },
  onPanResponderRelease: this.checkMapTap.bind(this)
})
```
<!-- .element: class="large" -->

-----

#### ES5 way

```js
this._panResponder = PanResponder.create({
  onStartShouldSetPanResponder: function() { return true },
  onPanResponderGrant: function(e) { 
	this.setState({mapTouchStart: e.nativeEvent.timestamp})
  }.bind(this),  // pass in proper `this` context
  onPanResponderRelease: this.checkMapTap.bind(this)
})
```
<!-- .element: class="large" -->


NOTES:
- Arrow functions in ES6 solve this problem
- Arrow functions use what’s called “lexical scoping” for `this`
- It's implicitly “inherited” from the enclosing scope, which in our case would be the class method
- Essentially arrow functions work how you would expect it to
- An arrow function is literally an arrow (fat arrow) between parameters and body
- You'll see a lot of React Native docs using arrow functions
- I left the last `this.checkMapTap.bind(this)` as-is and I'll explain why later

/////

```js
let squares = [1, 2, 3].map(value => value * value)
  // [1, 4, 9]
```
<!-- .element: class="large" -->

```js
let sum = [9, 8, 7, 6].reduce((prev, value) => prev + value, 0)
  // 30
```
<!-- .element: class="large" -->

```js
const log = (message) => {
  console.log(message)
})
```
<!-- .element: class="large" -->

```js
setTimeout(() => {
  log('delayed for 1 second')
  log('using arrow function')
}, 1000)
```
<!-- .element: class="large" -->

```js
const MyComponent = ({style, content}) => (
  <View style={style}>{content}</View>
)
```
<!-- .element: class="large" -->

NOTES:
- You’ll find that arrow functions come in handy most when used as a callback function.
- The various higher-order functional programming array methods that were introduced with ECMAScript 5 (like `map`, `forEach`, `reduce`, etc.) work well with arrow functions.
- Arrow functions can also be used as callback functions for event handlers (like `click`, `keydown`, etc)
- This also shows the different formats of arrow functions
- Parentheses can be omitted if there is one parameter
- Curly braces can be omitted if there's just a single `return` line
- The last example is a stateless function using arrow functions with parameter destructuring








=====

![Chain React Conf App About Screen](../../img/react-esnext/chain-react-about-screen.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 30%" -->

NOTES:
- Third feature relates to the About Screen
- It really doesn't, but I needed some screen to associate with it
- It applies to all the screens and none of the screens at the same time
- But to explain it, I need to take us on a journey

/////

```js
let maxValueNormal = Math.max(33, 2, 9)
let arrayOfValues = [33, 2, 9]
let maxValueFromArray = Math.max.apply(null, arrayOfValues)

// output: 33  33
console.log(maxValueNormal, maxValueFromArray)
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

[_Learning ES6:_ Parameter handling](http://www.benmvp.com/learning-es6-parameter-handling/#spread-operator)

/////

No more `apply`!

```js
let arrayOfValues = [33, 2, 9]
let maxValueFromArray = Math.max(...arrayOfValues)

// output: 33
console.log(maxValueFromArray)
```
<!-- .element: class="large" -->

<br />

-----

#### ES5 way

```js
let arrayOfValues = [33, 2, 9]
let maxValueFromArray = Math.max.apply(null, arrayOfValues)

// output: 33
console.log(maxValueFromArray);
```
<!-- .element: class="large" -->

NOTES:
- Instead of calling `apply` we can use the spread operator
- It's 3 dots preceding a parameter in a function call
- The spread operator _spreads_ out the array into individual parameters

/////

Maintain immutability!

```js
let start = ['do', 're']
let middle = ['mi', 'fa', 'so']
let end = ['la', 'ti']
let scaleFromLiteral = [...start, ...middle, ...end]

// output: ['do', 're', 'mi', 'fa', 'so', 'la', 'ti']
console.log(scaleFromLiteral)
```
<!-- .element: class="large" -->


NOTES:
- When we spread multiple arrays into an array literal we're constructing a new array with all of those values

/////

Creating an array

```js
// verbose
let values = new Array(2, 3, 4)

// shorthand
let values = [2, 3, 4]
```
<!-- .element: class="large" -->

------

Spreading into an array

```js
// [1, 2, 3, 4, 5]
let verbose = new Array(1, ...values, 5)

// [1, 2, 3, 4, 5]
let shorthand = [1, ...values, 5]
```
<!-- .element: class="large" -->

NOTES:
- So what does this have to do w/ maintaining immutability?

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

[Spread Properties](https://github.com/sebmarkbage/ecmascript-rest-spread) (Stage 3)

NOTES:
- Now we copy objects while adding new properties in one object literal definition
- It's a Stage 3 ES feature
- The ES5 way was to use `_.assign()`
- ES6 did introduce Object.assign() to handle this as well, but I'll always prefer syntax

/////

Sharing styles

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="width:48%">
		<pre><code class="lang-js">// Styles/AboutScreenStyle.js
export default StyleSheet.create({
  ...ApplicationStyles.screen,
  container: {
    flex: 1
  }
})</code></pre>
		<pre><code class="lang-js">// Themes/ApplicationStyles.js
const ApplicationStyles = {
  screen: {
    titleText: {
      ...Fonts.style.h2,
      fontSize: 14,
      color: Colors.text
    }
  }
}
export default ApplicationStyles</code></pre>
	</div>
	<div style="width:48%">
		<pre><code class="lang-js">// Themes/Fonts.js
const size = {
  h1: 38,
  h2: 34
}
const style = {
  h1: {
    fontFamily: type.base,
    fontSize: size.h1
  },
  h2: {
    fontWeight: 'bold',
    fontSize: size.h2
  }
}
export default {size, style}</code></pre>
		<pre><code class="lang-js">&lt;Text style={styles.titleText}>
  Our Sponsors
&lt;/Text></code></pre>
	</div>
</div>

NOTES:
- So that was a long digression to talk about the actual feature in the app
- React Native components don't use CSS but "inline styles"
- `StyleSheet.create` takes an object literal allowing to define several styles in one place
- Spreading in `ApplicationStyles.screen` so all the default styles for screens are available in component
- `titleText` is a style w/in `ApplicationStyles.screen`
- It spreads in the styling for `h2` defined in `Fonts`
- We can see that the `fontSize` for `titleText` is overriding the `fontSize` coming from `Fonts`
- There are other ways to share multiple styles (passing an array), but I like the simplicity of single style used

/////

![Mario Mushroom](../../img/giphy/mario-mushroom.gif)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 20%" -->

NOTES:
- While we're here, I have one bonus feature I want to throw at you
- Couldn't find it anywhere in the code, but here seems like a good place

/////

Object destructuring + rest operator!

```js
export default class Box extends PureComponent {
  render() {
    let {type, style, ...restProps} = this.props
    // `restProps` has everything in `this.props`
    // except `type` & `style`
	  let calcStyle = calculateStyle(type, style)

    return (
      <View style={calcStyle} {...restProps} />
    )
  }
}
```
<!-- .element: class="large" -->

[Rest Properties](https://github.com/sebmarkbage/ecmascript-rest-spread) (Stage 3)

NOTES:
- Rest operator is used for other things as well
- Rest properties are coming in soon to ECMAScript. They're in Stage 3
- Not in ES2015, not ES2016, not ES2017, but future JavaScript (maybe ES2018?)

/////

### Spread operator
object ➡️ multiple properties (right-hand side)

```js
let warriors = {Steph: 95, Klay: 82, Draymond: 79}
let newWarriors = {
  ...warriors, 
  Kevin: 97
}
```
<!-- .element: class="large" -->

-----

### Rest operator
Multiple properties ➡️ object (left-hand side)

```js
let {type, style, ...restProps} = this.props
  // `restProps` has everything in `this.props`
  // except `type` & `style`
```
<!-- .element: class="large" -->

NOTES:
- Spread operator & rest operator look the exact same
- Spread operator takes an object and spreds each of its properties to create a new object
- So it's on the RHS of assignment
- Rest operator takes multiple properties and combines them together into an object
- So it's on the LHS of assignment
- They are opposites of each other






=====

![Chain React Conf App Location Screen](../../img/react-esnext/chain-react-location-screen.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 30%" -->

NOTES:
- Fourth and last feature relates to the Location Screen again
- Has this toggle area where it shows Lyft/Uber options if you expand it

/////

```js
// Containers/LocationScreen.js
class LocationScreen extends React.PureComponent {
  static propTypes = { } // static property

  state = { }  // instance property

  _toggleRides = () => { }  // bound function ("private")

  render() {  // instance method
    return (
      <TouchableOpacity onPress={this._toggleRides}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
```
<!-- .element: class="large" -->

NOTES:
- This is a snapshot of what the LocationScreen component looks like
- It's making use of several ES.next features
- Pay special attention to the `_toggleRides` "method"
- Let's talk about 'em

/////

# Classes

Replace class factories with `class` syntax

<br />
<br />

[_Learning ES6: Classes_](http://www.benmvp.com/learning-es6-classes/)

NOTES:
- Now we can replace assigning to the prototype or using custom class factories with native class syntax

/////

ES6 class structure

```js
class MyClass extends BaseClass {
  static staticMethodA() { }
  static staticMethodB() { }
  constructor() { }
  methodOne() { }
  methodTwo() { }
}
```
<!-- .element: class="large" -->

NOTES:
- `class` keyword
- `extends` base class
- supports `constructor`, instance & `static` methods
- JavaScript doesn't officially support properties (yet)
- So our component in just ES6 would look like...

/////

```js
class LocationScreen extends React.PureComponent {
  constructor(props) {
	super(props)
    this.state = { }  // instance property
  }
  
  _toggleRides() { }  // instance method ("private")

  render() {  // instance method
    return (
      <TouchableOpacity onPress={this._toggleRides.bind(this)}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
LocationScreen.propTypes = { } // static property
```
<!-- .element: class="large" -->

NOTES:
- `propTypes` is now defined after the class definition as a static property
- `state` is assigned in `constructor` which now needs to call `super(props)`
- `_toggleRides` needs to be defined like a true method
- Naming convention prefix private helpers with `_`
- As a result we need `this._toggleRides.bind(this)`

/////

```js
class LocationScreen extends React.PureComponent {
  static propTypes = { } // static property

  state = { }  // instance property

  _toggleRides() { }  // instance method ("private")

  render() {  // instance method
    return (
      <TouchableOpacity onPress={this._toggleRides.bind(this)}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
```
<!-- .element: class="large" -->

[Public Class fields](https://github.com/tc39/proposal-class-fields) (Stage 2)

NOTES:
- Public class fields proposal moves back `propTypes` & `state`
- Supports both static and instance properties
- More declrative as to what's going on w/ the class
- Still have the `.bind`
- Having the `.bind` there potentially is bad because it's creating a new function for each `render`

/////

```js
class LocationScreen extends React.PureComponent {
  static propTypes = { } // static property

  state = { }  // instance property

  _toggleRides = () => { }  // bound function ("private")

  render() {  // instance method
    return (
      <TouchableOpacity onPress={this._toggleRides}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
```
<!-- .element: class="large" -->

Bound instance property functions solve `.bind` issue!

NOTES:
- Can convert `_toggleRides()` method to `_toggleRides` instance property bound arrow function
- Don't need to `.bind` anymore because of "lexical scoping"
- Can have implicit returns
- Still not 100% sold
- Looks like a method, but it's actually an instance property

/////

```js
class LocationScreen extends React.PureComponent {
  constructor(props) {
	super(props)
    this.state = { }  // instance property
	this._toggleRides = () => { }  // bound function ("private")
  }
  
  render() {  // instance method
    return (
      <TouchableOpacity onPress={this._toggleRides}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
LocationScreen.propTypes = { } // static property
```
<!-- .element: class="large" -->

Bound instance property functions aren't extendable!

NOTES:
- As a result, each instance creates its own copy
- Means that `_toggleRides` isn't subclassable
- In React world we don't use OOP, so not a huge deal

/////

```js
class LocationScreen extends React.PureComponent {
  static propTypes = { } // static property

  state = { }  // instance property

  #toggleRides = () => { }  // bound function (private) 

  render() {  // instance method
    return (
      <TouchableOpacity onPress={#toggleRides}>
        <Text style={styles.rideLabel}>Taking Lyft/Uber?</Text>
	  </TouchableOpacity>
	)
  }
}
```
<!-- .element: class="large" -->

[Private class fields](https://github.com/tc39/proposal-class-fields) (Stage 2)  

NOTES:
- Advantage of instance property func:
- Can use private fields syntax (`#`)
- It really is a private method
- Helps distinguish helper methods from lifecycle methods
- Also get to omit `this.`
- Part of the same proposal
- Not yet implemented in Babel!

=====

## Recap

<br />

0. Destructuring
0. Arrow functions
0. Spread operator (+ Rest operator!)
0. Classes

NOTES:
- Destructuring to be concise and clear
- Arrow functions to get lexical scoping + concise
- Spread operator to maintain immutability
- Classes to be more declarative

/////

## Additional resources

<br />

- [React Native Official Tutorial](https://facebook.github.io/react-native/docs/tutorial.html)
- [_Learning ES6_ series](/learning-es6-series/)
- [Chain React Conference App repo](https://github.com/infinitered/ChainReactApp)
- [Eventbrite ES6+ coding style guide](https://github.com/eventbrite/javascript/tree/master/es6)
- [Eventbrite React coding style guide](https://github.com/eventbrite/javascript/tree/master/react)
- [Eventbrite React ESLint configuration](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)

=====

![Julian Edelman Thumbs Up](../../img/giphy/julian-edelman-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

NOTES:
- So some quick shoutouts before I wrap

/////

![Chain React Conference logo](../../img/conf-logos/chain-react-logo.svg)
<!-- .element: style="width: 50%; border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Truly an honor & privilege to be here
- A year ago I didn't even know React Native
- And now I'm here sharing with you at the first React Native conf in the US
- Simply amazing
- Thanks to Tom, Ben, Beth & the rest of the team for the opportunity

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- I'm here in part because Eventbrite allowed my Frontend Platform team to make the transition from Backbone to React
- So thanks to the leadership for that trust
- Also thanks for continued support in speaking at conference to share what I know and what we've been doing

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:
- It's my hope that, the main reason I do this, is so you learn something new to make you a better developer
- Any feedback would be appreciated!

=====

![Take a bow](../../img/giphy/animated-take-a-bow.gif)
<!-- .element: style="width: 70%" -->

NOTES:

/////

# Ben Ilegbodu

<br />

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

<br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- Slides are available on Twitter and Blog
- Ask questions on Twitter, via email or AMA!
- Find me at lunch if you've got questions!
