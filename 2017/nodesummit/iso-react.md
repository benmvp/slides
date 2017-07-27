# Isomorphic React sans Node??

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#NodeSummit17](https://twitter.com/hashtag/NodeSummit17)  

<br />

July 27, 2017  

NOTES:
- My name is Ben Ilegbodu
- Posted link to slides on twitter if you want to follow along
- Talking about Isomorphic React w/o Node back-end

=====

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
- "Isomorphic JavaScript" or "Isomorphic React" is the idea of using the same templates rendered client-side on the server
- Eventbrite had to solve the problem of rendering React components server-side on non-Node web server
- Hoping our experiences, both good & bad, will help you if you find yourself in the same boat

/////

## "Isomorphic" vs. "Universal"

![Definition of isomorphic](../../img/react-sans-node/isomorphic-definition.png)
<!-- .element: style="width: 65%;" -->

![Definition of universal](../../img/react-sans-node/universal-definition.png)
<!-- .element: style="width: 65%;" -->

NOTES:
- Michael Jackson had a post of Medium...
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
- Prior to being a manager, I was lead Engineer on our Frontend Platform team that transitioned us from Backbone to React
- Made the transition over a year ago now and have been building new features on the new platform

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
- Isomorphic React is rendering our React app components server-side
- Server-side rendering was important & critical for the transition to be viable
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
- With help of routing lib like `react-router`, render components to a string included in HTML response
- BUT Because Eventbrite has existed for a decade, our backend isn’t Node

/////

![Python logo](../../img/react-sans-node/python.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

### (python)

NOTES:
- We use Python/Django for our back-end web server
- And it obviously can't interpret JS
- Question: how do we render React components?
- _Anybody else use Python/Django?_

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
- Same solution wouldn’t work for React; you’d essentially need to recreate Node in Python
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

/////

![Coldfusion logo](../../img/react-sans-node/coldfusion.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

=====

![Baby no no no!](../../img/giphy/baby-no.gif)
<!-- .element: style="width: 33%" -->

NOTES:
- We've tried to switch to Node web server a couple of times now
- But our OPS team immediately shot down any notion of replacing Django w/ a Node/Express web server
- Not because Node/Express is bad
- Unfamiliar for Ops. Frontend developers are familiar, but they'd actually have to maintain these servers for critical pages
- We still have the typical legacy monolith app in our Django middle-tier
- Working on factoring out things to SOA, but it's a lot! Long process
- Would have to replicate a lot of legacy logic in our Node server that's in Django
- Already making a huge “gamble” with React in general

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
    ex. /www/js/react/HelloWorld.jsx
- Component props
    ex. {name: 'Ben'}

RESPONSE:
- Rendered markup
    ex. <div data-reactid="1">Hello Ben!</div>
```
<!-- .element: class="large" -->

NOTES:
- It's an internal service that given a React component and its props it'll return a string of rendered markup
- No AJAX, on DB calls, no environment lookup, etc.
- Everything must be passed in for _initial render_
- "Stateless" because the server has access to the file system of all React components which _is_ state

/////

## React Component

```js
// www/js/react/HelloWorld.jsx

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
  -d '{"path":"/www/js/react/HelloWorld.jsx",props:{name:"Ben"}}'
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
- Create an element applying the props to the Component class
- Leveraging React's [`renderToString`](https://facebook.github.io/react/docs/top-level-api.html#reactdomserver.rendertostring) to get the markup
- Because React is a declarative tree, we can turn our JS into a string! Most previous libs couldn't do this
- Return it as the response
- Of course there are many more implementation details (some of which I'll mention). But that's the gist

/////

## Running Render Server

```sh
$> node server.js --verbose

[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
[2016-10-21T21:40:23] Request for /www/js/react/HelloWorld.jsx
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
- It gets the markup response and adds it to the context for the template to render

/////

## HTML template

```html
<html>
  <head>
    <title>Eventbrite</title>
  </head>
  <body>
    <div id="app">${ react_page_markup }</div>
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
- `renderToString` ≪ Pybars

NOTES:
- Latency is limited by having both servers on the same machine
- Single React render per Django render to limit requests
- Instead of rendering a bunch of tiny components sprinkled, we render the entire page
- Found that the overhead + React rendering was faster than Pybars
- And we had actually already forked it to speed it up

- That's it!

=====

![Slippery bowling lane](../../img/giphy/bowling-lane-fall.gif)
<!-- .element: style="width: 65%" -->

NOTES:
- That's it!
- So hopefully if you are in the same situation we were, what I've presented thus far is pretty compelling
- No doubt you've got your own legacy code, and there'll be lots of different implementation details for you
- But I did want to highlight a few gotchas/pitfalls that we ran into so hopefully you can learn from us
- Not all sunshine & roses
- The initial proof-of-concept was easy, it was handling all of the use-cases that was the “fun” part

=====

## On-Demand Transpilation (DEV)

```sh
$> node server.js --verbose
```
<!-- .element: class="large" -->

```sh
[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
SyntaxError: Unexpected reserved word import
```
<!-- .element: class="large" -->

NOTES:
- As we saw before this is how we run the server
- But in DEV we don't want to have to compile JS each time we make a change so server can pick it up
- We need the React component and all its dependencies, all written in ES6, transpiled
- Otherwise we get this sort of error when trying to request a component's markup
- (we're still running Node v4)
- We need "live" transpilation

/////

## On-Demand Transpilation (DEV)

```sh
$> babel-node server.js --verbose
```
<!-- .element: class="large" -->

```sh
[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
[2016-10-21T21:40:23] Request for /www/js/react/HelloWorld.jsx
```
<!-- .element: class="large" -->

([`babel-node`](https://babeljs.io/docs/usage/cli#babel-node))

NOTES:
- `babel-node` was the obvious choice
- Alternate node CLI which will compile ES6 code before script runs
- Only run in DEV!!!
- `babel-node` was fine until I tackled the next issue

=====

## Server restart (DEV)

```js
// Dynamic require to retrieve React component
var Component = require(params.path);
```
<!-- .element: class="large" -->

<br />

```sh
$> supervisor --watch js/react --extensions jsx --exec babel-node
    -- server.js --verbose
```
<!-- .element: class="large" -->

```sh
Starting child process with 'babel-node server.js --verbose'
Watching directory '/www/js/react' for changes.
[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
crashing child
Starting child process with 'babel-node server.js --verbose'
Error: listen EADDRINUSE 127.0.0.1:9009
```

([`node-supervisor`](https://github.com/petruisfan/node-supervisor))

NOTES:
- Once a node module is `require`d it’s “cached” for the lifetime of program execution (w/o hackery)
- In order to see file updates, we needed to watch for changes and restart the server
- Used the library `node-supervisor` for this
- But when I modified a file the server would crash with an address-in-use error
- As it turns out the problem was with `babel-node`. It didn't coexist well with `node-supervisor`

/////

## Server restart (DEV)

```sh
$> supervisor --watch /www/js/react --extensions jsx
    -- --require babel-register -- server.js --verbose
```
<!-- .element: class="large" -->

```sh
Starting child process with 'node --require babel-register -- server.js --verbose'
Watching directory '/www/js/react' for changes.
[2016-10-21T21:39:55] Started server at http://127.0.0.1:9009
crashing child
Starting child process with 'node --require babel-register -- server.js --verbose'
[2016-10-21T21:41:55] Started server at http://127.0.0.1:9009
```

([`babel-register`](https://babeljs.io/docs/usage/require/) require hook)

NOTES:
- After much googling & StackOverflow-ing, found the `--require` flag on node CLI
- Preloads a specified module at startup
- Could use it to require `babel-register` which is a require hook for transpiling everything that gets `require`d
- It worked beautifully
- But then there was _another_ problem...

/////

## Server restart (DEV)

```sh
$> supervisor
    --watch /www/js/react
    --extensions jsx
    --poll-interval 5000
    -- --require babel-register -- server.js --verbose
```
<!-- .element: class="large" -->

Long-polling needed for NFS in Docker Machine

NOTES:
- Everything worked great when I was developing the server locally on my Mac
- But once I ran it in our Docker Machine environment the server wasn't restarting on file changes
- This is because the file system was NFS and doesn't support file modified event (`inotify`)
- So we had to resort to long polling
- Really unfortunate because it's hard to know when the server will restart
- Will be fixed once we switch away to Docker for Mac

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
- Checkout widget, New create, new signin apps is in production!
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

![Usain Bolt Thumbs Up](../../img/giphy/usain-bolt-thumbs-up.gif)
<!-- .element: style="width: 60%" -->

/////

![Node Summit Logo](../../img/conf-logos/node-summit-white.png)
<!-- .element: style="width: 80%;border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## We're hiring!   <!-- .element: class="fragment" -->

NOTES:

/////

# YOU!
<!-- .element: style="font-size:12em" -->

NOTES:

=====

![Take a Bow](../../img/giphy/animated-take-a-bow.gif)
<!-- .element: style="width: 50%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So that's it!
- Slides are available on Twitter and Blog
- Ask questions on Twitter, via email or AMA!
- Thanks
