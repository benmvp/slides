# React exposed! 😮

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ReactSF](https://twitter.com/hashtag/ReactSF)  

<br />

February 9, 2017  

NOTES:
- My name is Ben Ilegbodu
- Talk is called "React exposed!" w/ surprised emoji
- Realized there was no description for the talk so you have no idea what it's gonna be about
- Title is intentionally hyperbolic to grab attention

/////

# 10 Revelations about React...
# ...Wait until you see #6!!

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ReactSF](https://twitter.com/hashtag/ReactSF)  

<br />

February 9, 2017  

NOTES:
- Was thinking of calling it “10 Revelations about React… Wait until you see #6!!!”
- But we're no longer fooled by those anymore
- BTW - Posted link to slides on twitter if you want to follow along
- Still not gonna tell you what the talk is about, instead let's...

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
  "work": "@Eventbrite",
  "role": "Frontend Eng Mgr",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
	<div style="flex:0 0 50%;">
		<img src="../../img/family-avery-birth.jpg" style="width:100%;height:auto" alt="Ilegbodu family after baby Avery was born" />
	</div>
</div>

NOTES:
- Now that you've all met, more about me...

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Senior UI Engineer and Frontend Platform Manager at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences use it for registration
- We've built up a whole new React-based stack to replace Backbone/Marionette
- I've had the opportunity to teach React both formally (workshop) and informally (helping people)
- Found myself explaining core concepts of React even though I didn’t write any of the implementation (only barely looked at the code)
- Genesis of this talk

/////

<!-- .slide: data-background="url(../../img/giphy/shia-magic.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- A good library abstracts away underlying complexity.
- Don't need to know how implementation works
- React has a lot of “magic” (as Shia puts it) that makes it powerful
- In general don’t need to know how the magic works
- However, there are some seemingly counterintuitive parts the make more sense when you understand how React works behind the scenes

=====

## Adjacent JSX elements

```
const PageBody = () => (
  <aside> LEFT NAV </aside>
  <section> MAIN BODY </section>
)

const Page = () => (
  <main>
    <h1> HEADING </h1>
	<PageBody />
  </main>
)
```
<!-- .element: class="large" -->

NOTES:
- Maybe using some ES6 syntax you're unfamiliar with
- This is intentional
- Not to show off, but to expose you to new syntax
- Might learn something else not even related to the topic
- If you're coming from a templating background like Handlebars you may try to use JSX like this
- You know you want to stick the contents of `PageBody` in `Page`

/////

## Adjacent JSX elements

```
repl: Adjacent JSX elements must be wrapped in an enclosing
tag (3:2)

  1 | const PageBody = () => (
  2 |   <aside> LEFT NAV </aside>
> 3 |   <section> MAIN BODY </section>
    |   ^
  4 | )
  5 |
  6 | const Page = () => (
```
<!-- .element: class="large" -->

NOTES:
- However, this results in an error saying you have to wrap in an enclosing tag
- We'll talk about why that is in a sec, but lets look at another issue...

/////

## Conditional JSX

```
const Section = ({headingText, content}) => (
  <section>
    { if (headingText) { }
		<h1>{headingText}</h1>
	{ } }
    <p>{content}</p>
  </section>
)
```
<!-- .element: class="large" -->

NOTES:
- All the string-based templating languages provide some facility for conditionally including markup
- May be tempted to do something like this
- Or just wonder how to accomplish conditionally including code
- This obviously looks like broken syntax
- Trying to include the `<h1>` only if `headingText` is defined

/////

## Conditional JSX

```
repl: Unexpected token (3:6)
  1 | const Section = ({headingText, content}) => (
  2 |   <section>
> 3 |     { if (headingText) { }
    |       ^
  4 | 		<h1>{headingText}</h1>
  5 | 	{ } }
  6 |     <p>{content}</p>
```
<!-- .element: class="large" -->

NOTES:
- Naturally this syntax is broken
- We need a way of handling conditional markup in JSX

/////

## Commenting JSX

```
const Card = ({line1, line2}) => (
  <div
    <!-- className="card" -->
  >
    <p>{line1}</p>
    <!-- <p>{line2}</p> -->
  </div>
)
```
<!-- .element: class="large" -->

NOTES:
- JSX looks like HTML, so you might first think you can use HTML comments
- To comment out attributes or entire pieces of markup

/////

## Commenting JSX

```
repl: Unexpected token (3:4)
  1 | const Card = ({line1, line2}) => (
  2 |   <div
> 3 |     <!-- className="card" -->
    |     ^
  4 |   >
  5 |     <p>{line1}</p>
  6 |     <!-- <p>{line2}</p> -->
```
<!-- .element: class="large" -->

NOTES:
- But you'll quickly find out that this syntax is unsupported & results in an error

/////

## Unexpected prop names

```
const Label = ({children, inputId}) => (
    <label
        class="is-hidden"
        for={inputId}
    >
	  {children}
	</label>
)
```
<!-- .element: class="large" -->

NOTES:
- And lastly, if you don't know JSX, you would naturally use `class` & `for` for attributes
- Anybody who's done React knows that `class` & `for` are incorrect
- But interestingly enough they don't throw any errors!
- They just simply don't work like you'd intend
- About to explain...

/////

![JSX](../../img/react-exposed/jsx.png)   <!-- .element: style="width:75%" -->

NOTES:

- Makes React much more approachable IMO
- Looks like HTML, but not exactly
- You shouldn't _need_ to learn JSX since it looks like HTML
- But as we saw, in certain cases you’re pretty much forced to know

/////

```
<span className="old">Vintage</span>
```
<!-- .element: class="large" -->

```
React.createElement(
  'span',
  {className: 'old'},
  'Vintage'
)
```
<!-- .element: class="large" -->

<br />

```
<Selector values={items} />
```
<!-- .element: class="large" -->


```
React.createElement(
  Selector,
  {values: item}
)
```
<!-- .element: class="large" -->

NOTES:
- JSX is really just JavaScript like everything else
- And that's the key to explaining how to properly use JSX
- JSX gets transpiled into this JS code: both for DOM nodes as well as custom components

/////

## Adjacent JSX elements


```
const PageBody = () => (
  <aside> LEFT NAV </aside>
  <section> MAIN BODY </section>
)
```
<!-- .element: class="large" -->

<br />

```
const PageBody = () => (
  React.createElement('aside', null, ' LEFT NAV '),
  React.createElement('section', null, ' MAIN BODY ')
)
```
<!-- .element: class="large" -->

NOTES:
- So when trying to return back those two DOM nodes
- We're actually trying to return back to objects, which we know is not possible
- Only one thing can be returned: one array, object, string, boolean, etc.

/////

## Adjacent JSX elements

```
const PageBody = () => (
  <div>
    <aside> LEFT NAV </aside>
    <section> MAIN BODY </section>
  </div>
)
```
<!-- .element: class="large" -->


```
const PageBody = () => (
  React.createElement(
	'div',
	null,
	React.createElement('aside', null, ' LEFT NAV '),
    React.createElement('section', null, ' MAIN BODY ')
  )
)
```
<!-- .element: class="large" -->

NOTES:
- So that's why you end up having to wrap the contents in a `<div>`
- You'll find that a lot of React apps have lots of "unnecessary" `<div>`s cuz of this

/////

## Conditional JSX

```
const Section = ({headingText, content}) => {
  let heading

  if (headingText) {
    heading = (<h1>{headingText}</h1>)
  }

  return (
    <section className="section-correct">
      {heading}
	  <p>{content}</p>
    </section>
  )
}
```
<!-- .element: class="large" -->

NOTES:
- This how you can tackle conditional code
- Naturally JSX is just JS, we can use JS to do conditionals instead of muddying up our JSX
- Conditionally assign a variable, and put that in our JSX
- It seems like a lot more code, so...

/////

## Conditional JSX

```
const Section = ({headingText, content}) => (
  <section className="section-correct">
    {headingText ? (<h1>{headingText}</h1>) : null}
	<p>{content}</p>
  </section>
)

```
<!-- .element: class="large" -->

NOTES:
- I've seen people use a ternary for this to keep things short
- But at Eventbrite we strive to keep the JSX as "clean" as possible
- This might be "okay", but would get out of hand quickly
- I've seen ternaries spanning 10+ lines


/////

## Commenting JSX

```
const Card = ({line1, line2}) => (
  <div
    // className="card"
  >
    <p>{line1}</p>
    {/*} <p>{line2}</p> {*/}
  </div>
)
```
<!-- .element: class="large" -->

```
const Card = ({line1, line2}) => (
  React.createElement(
    'div',
    null,
    React.createElement('p', null, line1)
  )
)
```
<!-- .element: class="large" -->

NOTES:
- Correct way of commenting out JSX
- Babel transpiler will just omit comments from generated code
- Have to admit that the syntax is kinda gross to look at

/////

## Unexpected prop names

```
const Label = ({children, inputId}) => (
    <label
      className="is-hidden"
	  htmlFor={inputId}
    >
	  {children}
	</label>
)
```
<!-- .element: class="large" -->

<br />

```
labelNode.className = 'is-hidden'
labelNode.htmlFor = inputId
```
<!-- .element: class="large" -->

NOTES:
- It's the `className` & `htmlFor` prop which make it **really** clear that this isn't HTML
- React chose to mirror the JS DOM API for its props which are all camelCase
- And that's why its `className` & `htmlFor` instead of the HTML `class` & `for`
- It's also why it's `onClick`, etc.
- You need ESLint rules to guard you from using `class` & `for` accidentally

=====

<!-- .slide: data-background="url(../../img/giphy/clumsy-digging.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- Let's dig deeper by looking at another problem

/////

```
const Selector = ({values}) => {
  let options = values.map(({value, display}) => (
    <option value={value}>{display}</option>
  ))

  return (<select>{options}</select>)
}
```
<!-- .element: class="large" -->

Can you spot the error?

<br />

```text
Warning: Each child in an array or iterator should have a unique
"key" prop. Check the render method of `Selector`. See
https://fb.me/react-warning-keys for more information.
```
<!-- .element: class="large fragment" -->

NOTES:
- I really like that React actually provides helpful errors
- Any other library and there'd be some cryptic error pointing to lib code
- If it's your first time seeing this error then you'll visit the link
- If you already know what's up, you'll probably do something like...

/////

```
const Selector = ({values}) => {
  let options = values.map(({value, display}, index) => (
    <option key={index} value={value}>{display}</option>
  ))

  return (<select>{options}</select>)
}
```
<!-- .element: class="large" -->

![Dikembe Mutombo No No No](../../img/giphy/no-no-no-mutombo.gif) <!-- .element: style="width:50%" -->

NOTES:
- ...this
- Where you'll use the second argument in the `map` callback which is the `index` and pass as `key`
- This is super simple & easy, but it's an anti-pattern and you shouldn't do it
- So y'all are the people behind the desk, balled piece of paper is you using "index as key" and I'm Dikembe Mutombo

/////

```
const Selector = ({values}) => {
  let options = values.map(({value, display}) => (
    <option key={value} value={value}>{display}</option>
  ))

  return (<select>{options}</select>)
}
```
<!-- .element: class="large" -->

Use a **unique** value as `key`!

NOTES:
- Instead you should be using a unique value in the data as the key
- Something that's not order dependent and is tied to the data
- Here we're reusing the `value` property as the `key` since it's unique

/////

<!-- .slide: data-background="url(../../img/giphy/house-of-cards-but-why.gif) no-repeat center" data-background-size="contain" -->

NOTES:
- But you're probably sitting there asking "why???"
- "Why does it matter?"

/////

![Brace Yourselves - A live demo is coming](../../img/react-exposed/live-demo.jpg) <!-- .element: style="width:70%" -->

NOTES:
- And that's best explained by a demo

=====

<!-- .slide: data-background="url(../../img/giphy/mario-out-of-time.gif) no-repeat center" data-background-size="contain"-->

NOTES:
- I've got a couple of other "exposes" so to speak
- But unfortunately there isn't too much time left...

=====

## Additional resources

- [React Exposed Demo](http://www.benmvp.com/react-exposed/)
- [React Fiber Architecture](https://github.com/acdlite/react-fiber-architecture)
- [_Index as key is an anti-pattern_](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318#.1191by53f)
- [Eventbrite React & JSX Coding Style Guide](https://github.com/eventbrite/javascript/tree/master/react)

=====

![Usain Bolt Thumbs Up](../../img/giphy/julian-edelman-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

/////

# ReactJS SF Bay Area Meetup

(Devon Lindsey)

NOTES:
-

/////

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct
- Any feedback would be appreciated!

=====

![Zac Efron Thanks](../../img/giphy/thanks-zac-efron.gif)
<!-- .element: style="width: 60%" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)

<br />


Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- Slides are available on Twitter
- Github repo
- Ask questions on Twitter, via email or AMA!
