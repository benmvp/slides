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

## What this talk is **not** about... 😐

<br />

- Why to use React
- How to develop in React
- How to set up React environment

/////

## What this talk is about! 😄

<br />

- "Isomorphic JavaScript"
- Rendering React server-side sans Node (web server)

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
  "role": "Sr. UI Engineer",
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
- Isomorphic JavaScript is the concept of using the same templates rendered in the browser on the server for initial load
- Server-side rendering is important
  - SEO
  - Performance
- React, unlike other JS frameworks/libraries, is setup to render server-side

/////

![Node.js logo](../../img/react-sans-node/nodejs-black.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 50%" -->

NOTES:
- Node is needed to render React components server-side because we need a full-fledged JS interpreter
- Typically, with "Isomorphic React" you would have a Node/Express web server
  * With help of routing lib like `react-router`, render components to a string included in HTML response
  * Normally components are efficiently rendered to the DOM client-side
- Because Eventbrite has existed for a decade, our backend isn’t Node

/////

![Python logo](../../img/react-sans-node/python.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none; height: auto; width: 45%" -->

### (python)

NOTES:
- We use Python/Django (_anybody else?_)
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
- OPS would've immediately shot down any notion of replacing Django w/ a Node/Express web server
- Not because Node/Express is bad
- Unfamiliar for Ops. They'd actually have to maintain these servers for critical pages
- We still have the typical ball-of-mud huge app in our Django layer
- Working on factoring out things to services, but it's a lot!
- Would have to replicate a lot of legacy logic in our Node server that's in Django
- Already making a huge “gamble” with React

/////

# Pybars

(gif of shim/hack)

NOTES:
- Currently solved the “dual rendering issue” using a lib called Pybars
- Our templates are written in Handlebars & Pybars converts the Handlebars into Python functions that return a string
  * It's like what happens in the original JS
  * Except it's super-duper slow because it was poorly written
- Same solution wouldn’t work for React; you’d essentially need to recreate Node in Python
  * Although we did consider it for a few seconds

/////

![Confused Urkel](../../img/giphy/confused-urkel.gif)
<!-- .element: style="width: 75%" -->

NOTES:
- Web server **must** be Django
- Server-side rendering of React **must** be Node

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
    <div style="flex:0 0 35%;">
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
    ex. /js/react/example/HelloWorld.jsx
- Component props
    ex. {name: 'Ben Ilegbodu'}

RESPONSE:
Rendered markup
    ex. <div data-reactid="1">Hello Ben Ilegbodu!</div>
```
<!-- .element: class="large" -->

NOTES:
- It's a service that given a React component and its props it'll return a string of rendered markup
- "Stateless" because the server has access to the file system of all React components which _is_ state

/////

## "Stateless" Render Server

`````sh
> curl \
>   -H "Content-Type: application/json" \
>   -X POST \
>   -d '{"path":"/js/react/example/HelloWorld.jsx"}' \
>   http://localhost:9009/render

<div data-reactid="1">Hello Ben Ilegbodu!</div>
`````
<!-- .element: class="large" -->

NOTES:
- If reading cURL requests are your thing...

/////

## "Stateless" Render Server

```js
app.post('/render', (req, res) => {
    Component = require(req.body.path)
    element = createElement(Component, req.body.props)
    markup = renderToString(element)

    res.send(markup)
})
```
<!-- .element: class="large" -->

NOTES:
- Digging deeper here's the super simple Express app
- Create the Component class from the specified component path by using `require()`
- Create an element applying the props to the Component class
- Leveraging React's [`renderToString`](https://facebook.github.io/react/docs/top-level-api.html#reactdomserver.rendertostring), get the markup
- Return it as the response
- Of course there are many more implementation details (some of which I'll mention). But that's the gist

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
- The server can render any component, but it's intended to render the entire (visible) page
- So the HTML template for a given page, may look something like this
- Take the string of markup rendered and inject it into the page template
- We still have to rely on server template (Mako) to render the page scaffolding
- EB is made up of multiple SPAs so the template is a bit more complicated, but this is idea

/////

## Django View

```python
# POST to http://localhost:9009/render
#   - path
#   - props
# context['react_page_markup'] = response.body
# render template
```
<!-- .element: class="large" -->

NOTES
- The Python/Django code that renders the template makes the POST with the path & props
- It gets the markup response and adds it to the context for the template to render
- Again this is a simplification of what's going on
- The actual code is actually factored out into a response helper so that any page can easily use it

/////

## Setup

- On same machine
- Behind firewall
- Single React render per page render

NOTES:
- There is a network overhead
- Latency is limited by having both servers on the same machine
- Found that the overhead + React rendering was faster than Pybars
- One react render per page render


/////

# Framework

NOTES:
- Have narrow scaffolding in Django for each page that would make a request to render server given app + props


=====

## Additional resources

- [_Learning ES6_](/learning-es6-series/)
- [Eventbrite React coding styleguide](https://github.com/eventbrite/javascript/tree/master/react)
- [`eslint-config-eventbrite-react`](https://github.com/eventbrite/javascript/tree/master/packages/eslint-config-eventbrite-react)
- [React Fundamentals Workshop](https://github.com/benmvp/react-workshop)

=====

# Shoutouts

/////

![Front Porch Conf](../../img/react-esnext/front-porch.svg)
<!-- .element: style="width: 40%;border: 0; background: none; margin: 0; box-shadow: none;" -->

/////

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: style="border: 0; background: none; margin: 0; box-shadow: none;" -->

## We're hiring!   <!-- .element: class="fragment" -->

/////

# YOU!

![Bleacher Report crowd](../../img/react-esnext/front-porch-crowd.jpg)
<!-- .element: style="width:50%" -->

NOTES:
- It's my hope that, the main reason I do this, is so you can feel excited & confident to start using ES6 syntax in your code to make it clearer and more succinct

=====

<!-- .slide: data-background="url(../../img/giphy/thanks-jack-sparrow.gif) no-repeat center" data-background-size="contain"-->

# THANKS!     <!-- .element: style="-webkit-text-stroke: white 2px" -->

NOTES:

/////

# Questions?

<br />

## Ben Ilegbodu

<br />

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)

<br />

Code examples: [github/benmvp/react-esnext](https://github.com/benmvp/react-esnext)
