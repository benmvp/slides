# Isomorphic React sans Node??

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#fstoco](https://twitter.com/hashtag/fstoco)  

<br />

October 23, 2017  

NOTES:
- My name is Ben Ilegbodu
- Talking about Isomorphic React w/o Node back-end
- Posted link to slides on twitter if you want to follow along

/////

## What this talk is **not** about... 😞

<br />

- Why to use React
- How to build a React app
- Implementation details in code

NOTES:
- Focusing mainly on high-level implementation instead of all of the implementation details

/////

## What this talk is about! 😄

<br />

- "Isomorphic React" sans Node*
- Architecture design

NOTES:
- "Isomorphic JavaScript" or "Isomorphic React" is the idea of using the same templates rendered client-side on initial server render
- Eventbrite had to solve the problem of rendering React components server-side on non-Node web server
- Hoping our experiences, both good & bad, will help you if you find yourself in the same boat

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
		<img src="../../img/family/family-house-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family standing in front of their house" />
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

<!-- .slide: data-background="url(../../img/giphy/james-harden-pot-cook.gif) no-repeat center" data-background-size="contain"-->

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Principal Frontend Engineer at Eventbrite
- Eventbrite is an online events & ticketing platform
- Full Stack is using one of our competitors, but that's ok! ;-)
- We've spent the last year transitioning from Backbone to React
- I'm sure others in the room are doing the same
- Made the transition over a year ago now and have been building new features on the new platform
- One of the key must-haves in the transition was server-side rendering

=====

### Isomorphic React

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

![Node.js logo](../../img/react-sans-node/nodejs-black.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 50%" -->

NOTES:
- Node is needed to render React components server-side because we need a full-fledged JS interpreter
- Typically, with "Isomorphic React" you would have a Node/Express web server
- With help of routing lib like `react-router`, render App to a string included in HTML response
- BUT Because Eventbrite has existed for a decade, our backend isn’t Node

/////

![Python logo](../../img/react-sans-node/python.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

### (python)

NOTES:
- We use Python/Django for our back-end web server
- And it obviously can't interpret JS
- Question: how do we render React components?
- _Anybody else use Python/Django/Flask?_

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
- Currently solved the “dual rendering issue” using a lib called Pybars
- Our JS templates are written in Handlebars & Pybars converts the Handlebars into Python functions that return a string
- It's like what happens in the original JS
- Except it's super-duper slow because it was poorly written
- Tried to speed it up, but it was still like 10x slower than rendering in Django/Mako templates
- Same solution wouldn’t work for React; you’d essentially need to recreate V8 engine in Python
- Although we did consider it for a few seconds
- This problem isn't just for Python/Django, it exists for all non-Node back-ends

/////

![Ruby on Rails logo](../../img/react-sans-node/ruby-on-rails.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 35%" -->

/////

![PHP logo](../../img/react-sans-node/php.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 50%" -->

/////

![ASP.NET logo](../../img/react-sans-node/asp-net.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 75%" -->

/////

![Java logo](../../img/react-sans-node/java.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

NOTES:
- Java, Groovy, Scala or anything else on the JVM?

/////

![Coldfusion logo](../../img/react-sans-node/coldfusion.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

NOTES:
- I'm just trolling you now...

=====

![Baby no no no!](../../img/giphy/baby-no.gif)
<!-- .element: style="width: 33%" -->

NOTES:
- We've tried to switch to Node web server a couple of times now
- But our OPS team immediately shot down any notion of replacing Django w/ a Node/Express web server
- Not because Node/Express is bad
- Unfamiliar for Ops. Frontend developers are familiar, but they'd actually have to maintain these servers for critical pages
- Furthermore... We still have the typical legacy monolith app in our Django middle-tier
- Working on factoring out things to SOA, but it's a lot! Long process
- Would have to replicate a lot of legacy logic in our Node server that's in Django
- At the time, already making a huge “gamble” with React in general

/////

![Confused Urkel](../../img/giphy/confused-urkel.gif)
<!-- .element: style="width: 75%" -->

NOTES:
- Web server **cannot** change from being Django (for OPS)
- Server-side rendering of React **must** be Node (for JS)

/////

![Thinking Winnie the Pooh](../../img/giphy/thinking-pooh.gif)
<!-- .element: style="width: 75%" -->

NOTES:
- So we were thinking...

/////

![Thinking Batman](../../img/giphy/thinking-batman.gif)
<!-- .element: style="width: 70%" -->

NOTES:
- And thinking...

/////

![Thinking Batman](../../img/giphy/thinking-tom-hanks.gif)
<!-- .element: style="width: 75%" -->

NOTES:
- And thinking...

/////

![Yes!](../../img/giphy/success.gif)
<!-- .element: style="width: 35%" -->

NOTES:
- Until finally we figured it out

/////

<div style="display:flex;align-items:center;justify-content:space-between;margin-top:5%">
    <div style="flex:0 0 35%;">
        <img
            src="../../img/react-sans-node/python.png"
            style="background:none;box-shadow:none;border:none;"
        />
    </div>
    <div style="flex: 0 0 5%;text-align:center">
        <h1>+</h1>
    </div>
    <div style="flex:0 0 50%;">
        <img
            src="../../img/react-sans-node/nodejs-black.png"
            style="background:none;box-shadow:none;border:none"
        />
    </div>
</div>

NOTES:
- We use both servers!

/////

<div style="display:flex;align-items:center;justify-content:space-between;margin-top:5%">
    <div style="flex:0 0 50%;">
        <img
            src="../../img/react-sans-node/python.png"
            style="background:none;box-shadow:none;border:none;"
        />
    </div>
    <div style="flex: 0 0 5%;text-align:center">
        <h1>+</h1>
    </div>
    <div style="flex:0 0 25%;">
        <img
            src="../../img/react-sans-node/nodejs-black.png"
            style="background:none;box-shadow:none;border:none"
        />
    </div>
</div>

NOTES:
- Really this should be the diagram because the Node/Express server is tiny because it's really a rendering service
- Lemme walk through some pseudocode to explain the architecture at a high level

=====

## "Stateless" Render Server

```sh
REQUEST:
- URL endpoint
    ex. http://localhost:9009/render
- Path to React component
    ex. /www/js/react/HelloWorld.js
- Component props
    ex. {name: 'Ben'}

RESPONSE:
- Rendered markup
    ex. <div data-reactid="1">Hello Ben!</div>
```
<!-- .element: class="large" -->

NOTES:
- It's an internal service that given path to React component and its props, it'll return a string of rendered markup
- No AJAX, on DB calls, no environment lookup, etc.
- Everything must be passed in for _initial render_
- "Stateless" because the server has access to the file system of all React components which _is_ state

/////

## React Component

```js
// www/js/react/HelloWorld.js

const HelloWorld = ({name}) => (
  <div>Hello {name}!</div>
)
```
<!-- .element: class="large" -->

NOTES:
- Say for example we had this sample React `HelloWorld` component
- It takes a `name` prop and renders a `<div>` with some text

/////

## cURL Request

```sh
$> curl
  -H "Content-Type: application/json"
  -X POST
  -d '{"path":"/www/js/react/HelloWorld.js",props:{name:"Ben"}}'
  http://localhost:9009/render

<div data-reactid="1">Hello Ben!</div>
```
<!-- .element: class="large" -->

NOTES:
- If reading cURL requests are your thing...
- Here's what the request/response looks like

/////

## Express Server

```js
// services/react-render-server/server.js
app.post('/render', (req, res) => {
  let params = req.body

  // Dynamic require to retrieve React component
  let Component = require(params.path)

  // Create element from component & props
  let element = React.createElement(Component, params.props)

  // Render element to a markup string
  let markup = ReactDomServer.renderToString(element)

  res.send(markup)
})
```
<!-- .element: class="large" -->

NOTES:
- Digging deeper here's the super simple Express app
- Has a `/render` route
- Create the Component class from the specified component path by using `require()`
- Create an element applying the props to the Component class (i.e. JSX)
- Leveraging React's [`renderToString`](https://facebook.github.io/react/docs/top-level-api.html#reactdomserver.rendertostring) to get the markup
- Because React is a declarative tree, we can turn our JS into a string! Most previous libs couldn't do this
- Return it as the response
- Of course there are many more implementation details (some of which I'll mention). But that's the gist

/////

## Running Render Server

```sh
$> node server.js --verbose

[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
[2016-10-21T21:40:23] Request for /www/js/react/HelloWorld.js
```
<!-- .element: class="large" -->

NOTES:
- With the initial proof-of-concept running the render server was this simple
- Message would be written to console that said when the server started up
- We'd run that cURL script from before in another terminal and we'd get back the response

/////

## Django View

```python
component_props = {
    # Data coalesced from DB / SOA calls
    # Data coalesced from Django GET/POST params
    # Data coalesced from environment params
}

response = requests.post(
    render_server_url,
    headers={'Content-Type': 'application/json'},
    data=json_encoder({
        'props': component_props,
        'path': component_path,
    }))

context['react_page_markup'] = response.text
context['react_page_props'] = component_props
```
<!-- .element: class="large" -->

NOTES:
- The Python/Django code that renders the template makes the POST with the path & props
- Coalesce data directly from DB/SOA calls, Django request / environment params
- EVERYTHING must be passed because it's "stateless"
- Again this is a simplification of what's going on
- It gets the markup response and adds it to the context w/ props for the template to render

/////

## HTML template

```html
<html>
  <head>
    <title>Eventbrite</title>
  </head>
  <body>
    <div id="root">${ react_page_markup }</div>
    <script>
      window.__INITIAL_STATE = ${ json.dumps(react_page_props) }
    </script>
    <script src="dist/react_bundle.js" />
  </body>
</html>
```
<!-- .element: class="large" -->

NOTES:
- So the HTML template page scaffolding may look something like this
- Take the string of markup rendered and inject it into the page template
- We still have to rely on server template (Mako) to render the page scaffolding (unavoidable)
- EB is made up of multiple SPAs so the template is a bit more complicated, but this is idea
- Pass along props in `window.INITIAL_STATE` to hydrate the app on the client

/////

## Network overhead?

Yes. 😞

NOTES:
- Hopefully you're thinking: "Isn't there network overhead?"
- Instead of rendering all in Django/Mako, we're making a roundtrip to render

/////

### However...

- Django + render servers on same machine
- Single React render per Django page render
- Pass JS App bundle
- `renderToString` ≪ Pybars

NOTES:
- Latency is limited by having both servers on the same machine
- Single React render per Django render to limit requests
- Instead of rendering a bunch of tiny components sprinkled, we render the entire page
- We're using Webpack to create our client bundles, so we also create one for Node
- Means Node doesn't have to import a bunch of client code, just `node_modules`
- Found that the overhead + React rendering was faster than Pybars
- And we had actually already forked it to speed it up

=====

![Squidward Ta-Da!](../../img/giphy/squidward-tada.gif)
<!-- .element: style="width: 65%" -->

NOTES:
- That's it!
- So hopefully if you are in the same situation we were, what I've presented thus far is pretty compelling
- No doubt you've got your own legacy code, and there'll be lots of different implementation details for you

/////

![Slippery bowling lane](../../img/giphy/bowling-lane-fall.gif)
<!-- .element: style="width: 65%" -->

NOTES:
- But I did want to highlight a few gotchas/pitfalls that we ran into so hopefully you can learn from us
- Not all sunshine & roses
- The initial proof-of-concept was easy, it was handling all of the use-cases that was the “fun” part

=====

## Production Mode

```sh
$> node server.js --verbose
```
<!-- .element: class="large" -->

<br />

### (Whoops! 🙈)

NOTES:
- As we saw before this is how we run the server
- There's something wrong with this, but it's non-obvious
- The code runs fine, but it's sub-optimal

/////

## Production Mode

Running the server...

```sh
$> NODE_ENV=production node server.js --verbose
```
<!-- .element: class="large" -->


<br />

...so that in React code...

```js
if (process.env === 'development') {
  // Display helpful warnings only in DEV...
}
```
<!-- .element: class="large" -->

NOTES:
- If you've developed in React, you've noticed that it provides lots of helpful warnings
- Great for developer experience, but they do slow things down
- If you pass in `NODE_ENV=production`, `process.env` is `'production'` so those extra checks don't get run
- `PropTypes` are an example of warnings not run on production
- Instead we should've run the server this way, but we forgot!

/////

## Production Mode

![react-render-server render times after setting process.env](../../img/react-sans-node/rrs-node-env.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 85%" -->

🤣🤣🤣

NOTES:
- Can you guess when we turned on the env var?? 🤣
- 2x improvement just by adding that env variable
- We went through this so you don't have to!

/////

## Production Mode

![Chart outlining React 16 server-side rendering perf](../../img/react-fiber/ssr-perf-chart-updated.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; width: 65%" -->

[github/aickin/react-16-ssr-perf](https://github.com/aickin/react-16-ssr-perf)

NOTES:
- Basically proved this synthetic benchmark chart
- Comparing Raw React 15, compiled React 15, and compiled React 16 beta 3
- Latest Node 4, 6 & 8
- 17x improvement just by upgrading systems

/////

## [Layperson’s guide to React Fiber](http://www.benmvp.com/slides/2017/reactrally/fiber.html)

<iframe width="1333" height="750" src="https://www.youtube.com/embed/q6QTxq_pFn0" frameborder="0" allowfullscreen></iframe>

### [React Rally 2017](http://www.reactrally.com/)

NOTES:
- If you're intersted in learning more about React Fiber & React 16...
- I gave a talk call _Layperson’s guide to React Fiber_ at React Rally in August
- There are more improvements to SSR including streaming support

=====

## Handling translations

```js
// constants.js
import gettext from 'js-utils/gettext'

export const FREE = gettext('Free')
export const ENDED = gettext('This event is over')
```
<!-- .element: class="large" -->

NOTES:
- Eventbrite exists in a dozen countries and languages
- So we completely translate the site to the local language
- But this caused problems with SSR and translated `const` strings
- Let's say we have a `constants.js` module exported a bunch of strings
- The first time the module is evaluated the `const` values are stored
- So it's cached in whatever was the lang of initial request
- Would see incorrect lang server-side and flash to correct lang client-side

/////

## Handling translations

```js
// LazyString.js

import gettext from 'js-utils/gettext'

export default class LazyString {
  constructor(msg) {
    this._msg = msg
  }

  toString() {
    return gettext(msg)
  }
}
```
<!-- .element: class="large" -->

NOTES:
- What we needed was something that would do the translation at _render_ time
- That's when we knew the language of the request
- Unfortunately I don't have too much time to go into the details
- But here's the `LazyString` object we built
- It overrides the `toString` method so that it _acts_ like a string

/////

## Handling translations

```js
// js-utils/lazy-gettext
import LazyString from './LazyString'

const lazyGettext = (msg) => new LazyString(msg)
export default lazyGettext;
```
<!-- .element: class="large" -->

<br />

```js
// constants.js
import lazyGettext from 'js-utils/lazy-gettext'

export const FREE = lazyGettext('Free')
export const ENDED = lazyGettext('This event is over')
```
<!-- .element: class="large" -->

NOTES:
- Created a new `lazy-gettext` module
- So even though the `LazyString` object is const, the message will be translated
- We _just_ found this issue, a year into it
- We'll be blogging about it soon
- Had to introduce a new prop type that receive a normal string or `LazyString`

=====

## Path to Production

- Health check with `/ping` endpoint
- Log file writing with [`node-bunyan`](https://github.com/trentm/node-bunyan)
- [Sentry](https://sentry.io/) error logging with [`raven-node`](https://github.com/getsentry/raven-node) & [`bunyan-sentry-stream`](https://github.com/transcovo/bunyan-sentry-stream)
- Render performance monitoring with [Grafana + Graphite](http://docs.grafana.org/datasources/graphite/)
- Load testing with [Locust](http://locust.io/)
- Several apps in Production!

NOTES:
- In order for the render server to move from a proof of concept to a production-ready, needed logging & monitoring
- As a UI Engineer all of what I've described was already out of my comfort zone
- Logging & monitoring was even further outside my expertise
- Thankfully I had some AMAZING back-end engineers who volunteered to help me take it to completion
- Decided for the first consumers of new React platform to be new features
- Checkout widget, Organizer onboarding, new signin apps is in production!
- Destination team has new City Browse experience coming sooon!

=====

## Additional resources
- Airbnb [Hypernova](https://github.com/airbnb/hypernova) (Rails friendly)
- [`python-react`](https://github.com/markfinger/python-react) & [`react-render`](https://github.com/markfinger/react-render)
- [ReactJS.NET](https://reactjs.net/)
- [Nashorn](http://openjdk.java.net/projects/nashorn/) JS runtime in Java

NOTES:
- Looks like Airbnb & us were trying to solve the same problem at roughly the same time
- They open-sourced Hypernova which is basically all that I described in late May. We started in late January
- Creating the server isn't complicated at all, but it's a bit complex with little details here in there
- If you don't want to go through the hassle, I'd recommending checking out Hypernova
- They sped up `renderToString` by 3x!

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
- Wanted to thank Full Stack and James for invited me here to share with you
- Also thank YOU for attending!
- My goal is for you to learn at least one thing you can take away to be a better dev
- Slides are available on Twitter and Blog
- Ask questions on Twitter, via email or AMA!
- Thanks and enjoy the rest of the conference!
