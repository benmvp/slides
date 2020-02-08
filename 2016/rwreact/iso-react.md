# Isomorphic React w/o Node??

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#RWReact](https://twitter.com/hashtag/RWReact)  

<br />

October 18, 2016  

NOTES:
- My name is Ben Ilegbodu
- Posted link to slides on twitter if you want to follow along

=====

## What this talk is **not** about... 😞

<br />

- Why to use React
- How to build a React app
- Implementation details in code

/////

## What this talk is about! 😄

<br />

- "Isomorphic React" sans Node*
- Architecture design

NOTES:
- "Isomorphic JavaScript" or "Isomorphic React" is the idea of using the same templates rendered client-side on the server
- Eventbrite had to solve the problem of rendering React components server-side on non-Node web server
- Hoping our experiences, both good & bad, will help you if you find yourself in the same boat

=====

ben-ilegbodu.json

<div style="display:flex">
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
_[1 minute]_

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

NOTES:
- Currently a Senior UI Engineer at Eventbrite
- Eventbrite is an online ticketing & events platform
- Many conferences & events use it for registration
- I work on our Frontend Platform team and we're wrapping up a huge push to transition from Backbone/Marionette to... React

=====

### Isomorphic React

<div style="display:flex;align-items:center;justify-content:space-around;">
    <img src="../../img/react/react-logo.png" style="background:none;box-shadow:none;border:none"/>
    <div>
        <h2>SEO</h2>
        <h2>Performance</h2>
    </div>
</div>

NOTES:
- Transitioned to React
- Isomorphic JavaScript is the concept of sharing the same templates rendered in the browser on the server for initial load
- Server-side rendering is important & critical for the transition to be viable
  - SEO
  - Performance
- React, unlike other JS frameworks/libraries, is setup to render server-side, as we'll see

/////

![Node.js logo](../../img/react-sans-node/nodejs-black.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 50%" -->

NOTES:
- Node is needed to render React components server-side because we need a full-fledged JS interpreter
- Typically, with "Isomorphic React" you would have a Node/Express web server
  * With help of routing lib like `react-router`, render components to a string included in HTML response
  * Normally components are just (efficiently) rendered to the DOM client-side
- BUT Because Eventbrite has existed for a decade, our backend isn’t Node

/////

![Python logo](../../img/react-sans-node/python.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

### (python)

NOTES:
- We use Python/Django for our back-end web server
- And it obviously can't interpret JS, so the obvious issue is how do we render React components?
- _Anybody else use Python/Django?_

/////

## Python + Handlebars logo

### ([Pybars](https://github.com/wbond/pybars3))

NOTES:
- Currently solved the “dual rendering issue” using a lib called Pybars
- Our templates are written in Handlebars & Pybars converts the Handlebars into Python functions that return a string
  * It's like what happens in the original JS
  * Except it's super-duper slow because it was poorly written
- Same solution wouldn’t work for React; you’d essentially need to recreate Node in Python
  * Although we did consider it for a few seconds
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
- Answer: switch to Node!
- OPS would've immediately shot down any notion of replacing Django w/ a Node/Express web server
- Not because Node/Express is bad
- Unfamiliar for Ops. Frontend developers are familiar, but they'd actually have to maintain these servers for critical pages
- We still have the typical legacy ball-of-mud huge app in our Django layer
- Working on factoring out things to SOA, but it's a lot! Long process
- Would have to replicate a lot of legacy logic in our Node server that's in Django
- Already making a huge “gamble” with React

/////

![Confused Urkel](../../img/giphy/confused-urkel.gif)
<!-- .element: style="width: 75%" -->

NOTES:
- Web server **must** be Django (for OPS)
- Server-side rendering of React **must** be Node (for JS)

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
- Gonna walk through some pseudocode to explain the architecture at a high level

=====

## "Stateless" Render Server

```sh
REQUEST:
- URL endpoint
    ex. http://localhost:9009/render
- Path to React component
    ex. /js/react/HelloWorld.jsx
- Component props
    ex. {name: 'Ben'}

RESPONSE:
- Rendered markup
    ex. <div data-reactid="1">Hello Ben!</div>
```
<!-- .element: class="large" -->

NOTES:
- It's an internal service that given a React component and its props it'll return a string of rendered markup
- "Stateless" because the server has access to the file system of all React components which _is_ state
- No AJAX, on DB calls, no environment lookup, etc.

/////

## React Component

```js
// js/react/HelloWorld.jsx

const HelloWorld = ({name}) => (
    <div>Hello {name}!</div>
);
```
<!-- .element: class="large" -->

NOTES:
- Say for example we had this sample React `HelloWorld` component
- It takes a `name` prop and renders a `<div>` with some text

/////

## cURL Request

`````sh
> curl \
>   -H "Content-Type: application/json" \
>   -X POST \
>   -d '{"path":"/js/react/HelloWorld.jsx",props:{name:"Ben"}}' \
>   http://localhost:9009/render

<div data-reactid="1">Hello Ben!</div>
`````
<!-- .element: class="large" -->

NOTES:
- If reading cURL requests are your thing...
- Here's what the request/response looks like

/////

## Express Server

```js
app.post('/render', (req, res) => {
    let params = req.body;

    // Dynamic require to retrieve React component
    let Component = require(params.path);

    // Create element from component & props
    let element = React.createElement(Component, params.props);

    // Render element to a markup string
    let markup = ReactDomServer.renderToString(element);

    // return rendered markup
    res.send(markup);
});
```
<!-- .element: class="large" -->

NOTES:
- Digging deeper here's the super simple Express app
- Create the Component class from the specified component path by using `require()`
- Create an element applying the props to the Component class
- Leveraging React's [`renderToString`](https://facebook.github.io/react/docs/top-level-api.html#reactdomserver.rendertostring) to get the markup
- Because React is a declarative tree, we can turn our JS into a string! Most previous libs couldn't do this
- Return it as the response
- Of course there are many more implementation details (some of which I'll mention). But that's the gist

/////

## Django View

```python
component_props = {
    # Data coalesced from DB / SOA calls
    # Data coalesced from Django GET/POST params
    # Data coalesced from environment params
}

react_response = requests.post(
    render_server_url,
    headers={'Content-Type': 'application/json'},
    data=json_encoder({
        'props': component_props,
        'path': component_path,
    }))

context['react_page_markup'] = react_response.text
```
<!-- .element: class="large" -->

NOTES:
- The Python/Django code that renders the template makes the POST with the path & props
- Coalesce data directly from DB/SOA calls, Django request / environment params
- EVERYTHING must be passed because it's "statless"
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

/////

## Network overhead?

Yes. 😞

NOTES:
- There is a network overhead
- Instead of rendering all in Django/Mako, we're making a roundtrip to render

/////

### However...

- Django + render servers on same machine
- Single React render per Django page render
- `renderToString` ≪ Pybars

NOTES:
- Latency is limited by having both servers on the same machine
- Found that the overhead + React rendering was faster than Pybars
- And we had actually already forked it to speed it up
- Single React render per Django render to limit requests
- Instead of rendering a bunch of tiny components sprinkled, we render the entire page

=====

![Swinging over a lake](../../img/giphy/lake-swing-over.gif)
<!-- .element: style="width: 65%" -->

NOTES:
- So hopefully if you are in the same situation we were, why I've presented thus far is pretty compelling
- No doubt you've got your own legacy code, and there'll be lots of different implementation details for you
- But I did want to highlight a few gotchas/pitfalls that we ran into so hopefully you can learn from us

=====

## Additional resources
- [Airbnb Hypernova](https://github.com/airbnb/hypernova)
- [`python-react`](https://github.com/markfinger/python-react) & [`react-render`](https://github.com/markfinger/react-render)
- [ReactJS.NET](https://reactjs.net/)
- [Nashorn](http://openjdk.java.net/projects/nashorn/) JS runtime in Java

=====

## (gif of thumbs up)

/////

![Real World React logo](../../img/react-sans-node/real-world-react.jpg)
<!-- .element: style="width: 50%;border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## We're [hiring](https://www.eventbrite.com/careers/)!
<!-- .element: class="fragment" -->

NOTES:
- Thanks to Eventbrite for hosting and in general being willing to host
- Meetups lose momentum because organizers can't find venues
- Want to call out Hillary & Deniz particularly for all of the efforts
- They go to so many conferences that they know all the buzzwords

/////

# YOU!

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct

=====

<!-- .slide: data-background="url(../../img/giphy/thanks-aladdin.gif) no-repeat center" data-background-size="contain"-->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

<br />

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
