<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 50%;" class="content-overlay">
  
  <h1>State of the React Ecosystem</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@ReactNext](https://twitter.com/ReactNext)</p>

  <br />

  <p>November 4, 2018</p>
  
  </div>
</div> 

NOTES:
**RESTART THE TIMER!!!!**

- So excited to be here in Israel
  * One of my bucket list countries to visit
- If you're new to React you might hear that on top of learning React
  * You need to know Redux, css-in-js, server-side rendering, etc.
  * All at the same time
  * It can be so overwhelming
- And then React is just a UI library
  * Need to pick libraries for fetching data, managing, data, etc.
  * How can you pick something if you don't yet know what you need?
  * How can you pick the right thing, if you've never used it before?
- So I want to walk through the different libs in the React ecosystem
  * 1/ So you can get an idea of how to prioritize what to learn
  * 2/ I'll also try to give a list of options for each category and my preference
- For those of you who have been doing React for a while
  * Hopefully there'll be a thing or two that'll be new for you
  * If not, you can use the info I provide when your coworkers ask you why you picked a lib
  * It no longer has to be "Because... I liked it?"

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:

=====

<!-- .slide: data-background="url(../../img/family/family-selfie-madrid.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Christian, Husband, Father
- _Family introductions_
- Wife Rashida is pregnant with our 3rd child

/////

![Eventbrite wordmark logo](../../img/eventbrite/wordmark-orange.svg)
<!-- .element: class="plain" style="width: 85%" -->

NOTES:
- I'm a Principal Frontend Engineer at Eventbrite in San Francisco
- We're an online Events & Ticketing platform
- Work on our Frontend Platform team
  * Doing FE infra + design system work
  * We've been using React for 2.5 years
  * Migrated from Backbone and have never looked back

=====
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
_[4 minutes]_

- Ok, enough about me
- Let's talk about the React Solar System
- Going to be *a lot* of stuff covered
  * Probably not going to teach you how to use any given lib
  * Instead my goal is to expose you to the libs so you can investigate
  * Will also give my preferences
- Tweeted a link to slides cuz there will be **a lot** of resources

=====
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>0. React</h1>
  </div>
</div>

NOTES:
- At the beginning obviously is React

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 75%">
    <div style="display:flex;align-items:center;justify-content:space-between;">
      <a href="https://facebook.github.io/react/tutorial/tutorial.html" target="_blank" style="width: 45%">
        <img src="../../img/react/react-logo.png" class="plain" />
      </a>
      <div>
        <h2><a href="https://egghead.io/courses/advanced-react-component-patterns">Component patterns</a></h2>
        <h2><a href="https://reactjs.org/docs/error-boundaries.html">Error boundaries</a> <sup style="font-size: .5em">16</sup></h2>
        <h2><a href="https://reactjs.org/docs/optimizing-performance.html#profiling-components-with-the-chrome-performance-tab">Performance</a> <sup style="font-size: .5em">16.5</sup></h2>
        <h2><a href="https://reactjs.org/docs/fragments.html">Fragments</a> <sup style="font-size: .5em">16.2</sup></h2>
        <h2><a href="https://reactjs.org/docs/code-splitting.html#reactlazy">Suspense</a> <sup style="font-size: .5em">16.6</sup></h2>
        <h2><a href="https://reactjs.org/docs/context.html">Context</a> <sup style="font-size: .5em">16.3</sup></h2>
      </div>
    </div>
  </div>
</div>


NOTES:
- First, learn React and learn it _really_ well
  * Sounds like an obvious statement
  * But it's important to focus on this first
  * Learn how to maintain state properly & leverage "virtual DOM"
- After the basics, keep up with the latest features...
- Advanced component patterns
  * Presentational vs. container components
  * Sharing component logic with higher-order components or render props (or future "hooks")
- Using Fragments & Context API
- Implementing error boundaries
- Monitoring and optimizing performance
- Leveraging new Suspense system with auto-code splitting
- If you're interested in learning more about React fundamentals...

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/robert-herbst.jpg" alt="Robert Herbst" class="speaker-headshot" />
      <br />
      Robert Herbst
    </p>

    <h2>Advanced Patterns</h2>

    <p>10:30 (Hall A)</p>
  </div>
</div>

NOTES:
- Robert is giving a talk right after this on advanced component patterns

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/patrick-hund.png" alt="Patrick Hund" class="speaker-headshot" />
      <br />
      Patrick Hund
    </p>

    <h2>Breaking Down Your Web App</h2>

    <p>12:30 (Hall A)</p>
  </div>
</div>

NOTES:
- Patrick's talk is on properly compenentizing your app

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/yoav-niran.jpg" alt="Yoav Niran" class="speaker-headshot" />
      <br />
      Yoav Niran
    </p>

    <h2>React Responsively, Render Responsibly</h2>

    <p>13:05 (Hall B)</p>
  </div>
</div>

NOTES:
- Yoav is going to teach us how to analyze and improve the performance of our apps

=====
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>1. Tooling</h1>
  </div>
</div>

NOTES:
_[6 minutes]_

- But enough about React itself
  * The purpose of this talk is to look at the libs in the ecosystem
- Probably the biggest complaint w/ React isn't React itself
  * But the tooling needed to get set up
- I think the problem is that there's so much choice in this area
  * You need to know how the tools work before you could get up and running

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 40%">
    <h2>React Dev Tools</h2>
    <p>Help debug React props & state</p>

    <img src="../../img/nav-react/react-dev-tools-2018.jpg" alt="Screenshot of React Dev Tools install" style="width: 100%" />

    <p>Available for <a href="https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en" target="_blank">Chrome</a> and <a href="https://addons.mozilla.org/en-US/firefox/addon/react-devtools/" target="_blank">Firefox</a></p>

    <p>(Performance debugging in v16.5)</p>
  </div>
</div>

NOTES:
- Let's start easy
- The React Dev Tools are super helpful in debugging React components
- You just browse the React component tree just like the DOM tree
  * And you can look at the component props as well as the state
- Available for Chrome & Firefox. Sorry Edge users.
- And just recently with the release of React 16.5.0 enabling performance debugging

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 70%">
    <h2>Bundlers</h2>
    <p>Help gather dependencies, transpile ES6+, etc.</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 18%;">
        <a href="https://webpack.github.io/" target="_blank"><img src="../../img/nav-react/webpack-logo.png" class="plain" /></a>
        <a href="https://webpack.github.io/" target="_blank">Webpack</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="http://rollupjs.org/" target="_blank"><img src="../../img/nav-react/rollup-logo.svg" class="plain" /></a>
        <a href="http://rollupjs.org/" target="_blank">Rollup</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="https://parceljs.org/" target="_blank"><img src="../../img/nav-react/parcel-logo.png" class="plain" style="width: 100%" /></a>
        <a href="https://parceljs.org/" target="_blank">Parcel</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="http://prepack.io/" target="_blank"><img src="../../img/nav-react/prepack-logo.png" class="plain" style="width: 100%" /></a>
        <a href="http://prepack.io/" target="_blank">Prepack*</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="http://requirejs.org/" target="_blank"><img src="../../img/nav-react/requirejs-logo.png" class="plain" /></a>
        <a href="http://requirejs.org/" target="_blank" style="text-decoration: line-through">RequireJS</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- If you're building out your own custom stack there's a lot to think about

- First you have to figure out which bundling system you'll use
  * This is space has a lot of players
- Webpack is the prevailing bundler right now
  * But you have to add loaders and other configurations to make it do what you need
- Rollup works specifically with ES6 modules
  * Introduced the concept of "tree-shaking" feature that results in less generated code
  * But instead of bundling the code into one file, it transpiles individual files
  * Good for libraries
- Parcel is a new tool that boasts blazing fast build times
  * It also is "zero-config" so it has a lot of functionality out of the box
- Prepack is another new tool for making JS code run faster
  * From Facebook
  * Computations that can be done at compile-time instead of run-time get eliminated
  * Still in early DEV stage so not quite ready for production
- RequireJS is the original, but just isn't well suited at all for modern web development practices
- I'd say go with Webpack
  * It's still constantly evolving
  * Webpack has "tree-shaking" too
  * There's a whole ecosystem around it
- It's at this step where the "JavaScript fatigue" really kicks in
  * Your typical JS developer doesn't want to or know how to configure these bundlers
  * Just work please

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 60%">
    <h2>Task runners</h2>
    <p>Help execute shell commands, generate files, etc.</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 25%;">
        <a href="http://gruntjs.com/" target="_blank" style="display:block"><img src="../../img/nav-react/grunt-logo.svg" class="plain"/></a>
        <a href="http://gruntjs.com/" target="_blank">Grunt</a>
      </div>
      <div style="flex:0 0 25%;">
        <a href="http://gulpjs.com/" target="_blank" style="display:block"><img src="../../img/nav-react/gulp-logo.svg" class="plain" /></a>
        <a href="http://gulpjs.com/" target="_blank">Gulp</a>
      </div>
      <div style="flex:0 0 25%">
        <a href="https://docs.npmjs.com/misc/scripts" target="_blank" style="display:block"><img src="../../img/nav-react/npm-logo.png" class="plain" /></a>
        <a href="https://docs.npmjs.com/misc/scripts" target="_blank">NPM</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- Build files, run shell scripts, etc.
- Grunt was the original & dominant
  * Then because grunt files became so unmanageable
- Gulp approached it with streams in a functional way
- But with "building fatigue" and the fact that webpack could do so much of this for us
- NPM scripts have lately become the most popular
  * Essentially wrappers around command line calls
- If things are simple, use npm scripts.
- If things are complex, use Gulp since it's functional

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 60%">
    <h2>Static Analyzers</h2>
    <p>Help catch errors in written code before runtime</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 30%;">
        <a href="http://eslint.org/" target="_blank"><img src="../../img/nav-react/eslint-logo.svg" class="plain"/></a>
        <a href="http://eslint.org/" target="_blank">ESLint</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="https://flowtype.org/" target="_blank" style="display:block"><img src="../../img/nav-react/flow-logo.png" class="plain" /></a>
        <a href="https://flowtype.org/" target="_blank">Flow</a>
      </div>
	    <div style="flex:0 0 30%;">
        <a href="https://www.typescriptlang.org/" target="_blank"><img src="../../img/nav-react/typescript-logo.png" class="plain" /></a>
		    <a href="https://www.typescriptlang.org/" target="_blank">TypeScript</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- The static analyzers help you catch errors in your code before it ever executes
  * Can add these to your editor to get feedback in realtime
- **ESLint:** originally just for stylistic code preferences
  * Can catch common errors, including in JSX
- Flow & Typescript are both static _type_ checkers
- Flow is exclusively for type checking
- TypeScript is a superset of JavaScript that includes type checking plus future JavaScript;
  * It introduced classes before they were in ES2015
  * It has interfaces which JS does not
- I have used Flow, and in practice is not so great
  * Leaning more towards TypeScript
  * Seems to just be better at typing
  * But it's more "all-in" than Flow

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Create React App</h2>
    <p>Create React apps with no build configuration</p>

    <pre class="large" style="margin:5% 0"><code>$> npx create-react-app react-next

$> cd react-next

$> yarn start

### For production

$> yarn build</code></pre>

    <p><a href="https://reactjs.org/blog/2018/10/01/create-react-app-v2.html" target="_blank">CRA 2.0</a>: Babel 7, Webpack 4, TypeScript, CSS Modules, etc.</p>
  </div>
</div>


NOTES:
- So this is everything you need to set up your React app!
  * And I didn't even go into a bunch of nitty gritty details
- This had been the biggest complaint about React
  * How to get started


- If you don't need highly custom stack, you can use Create React App
  * Created by the React team
  * Allows you to bootstrap super quick w/ zero-config
  * And if you need to config something it doesn't support you can "eject"
- Creates an optimized bundle you can ship to production
- Much better than the (bloated) boilerplates / starter-kits
- v2 just shipped last month!

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Tooling resources</h2>

    <ul>
      <li><a href="https://github.com/joshwcomeau/guppy" target="_blank">Guppy</a></li>
      <li><a href="https://github.com/creationix/nvm" target="_blank">Node Version Manager</a></li>
      <li><a href="https://github.com/zkat/npx" target="_blank">`npx`</a></li>
      <li><a href="https://github.com/sindresorhus/awesome-npm" target="_blank">Awesome npm resources and tips</a></li>
      <li><a href="https://blog.risingstack.com/yarn-vs-npm-node-js-package-managers/" target="_blank">Yarn vs NPM</a></li>
      <li><a href="https://webpack.js.org/configuration/dev-server/" target="_blank">`webpack-dev-server`</a></li>
      <li><a href="https://flow.org/en/docs/react/" target="_blank">Flow + React</a></li>
      <li><a href="https://www.typescriptlang.org/docs/handbook/react-&-webpack.html" target="_blank">TypeScript & React</a></li>
    </ul>
  </div>
</div>

NOTES:
- Here are some miscellaneous resources regarding all the tools we talked about

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/gil-fink.jpg" alt="Gil Fink" class="speaker-headshot" />
      <br />
      Gil Fink
    </p>

    <h2>Wiring TypeScript into React</h2>

    <p>13:20 (Hall B)</p>
  </div>
</div>

NOTES:
- Very quickly mentioned TypeScript
- Gil in his lightning talk will go over it much more!

=====
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>2. Styling</h1>
  </div>
</div>


NOTES:
_[9 minutes]_

- Let's talking about styling because visuals are just as important as interaction
- There are _at least_ 5 ways to tackle the styling problem

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Global CSS</h2>
    <p>Use CSS that exists on the page outside of React</p>

    <pre class="large"><code class="lang-javascript">const Card = ({title, imageUrl, message}) => (
  &lt;div className="card">
    &lt;h2 className="card\__title">{title}&lt;/h2>
    &lt;img src={imageUrl} className="card\__image" />
    &lt;p className="card\__message">{message}&lt;/p>
  &lt;/div>
)</code></pre>
  </div>
</div>

NOTES:
- You'd use the Global CSS option if you are transitioning to React
  * Already have your CSS being built by some other process
  * Create new React components with existing CSS classes
- Bootstrap or Foundation would fall under this as well


/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Global CSS</h2>

    <pre class="large"><code class="lang-css">
/\* global.scss \*/

/\* lots of other styles before \*/

.card { }
.card\__title { }
.card\__image { }
.card\__message { }

/\* lots of other styles after \*/</code></pre>

  <p>
    <a href="http://getbem.com/" target="_blank">BEM</a>,
    <a href="https://smacss.com/" target="_blank">SMACSS</a> or
    <a href="https://github.com/stubbornella/oocss/wiki">OOCSS</a> for class name-spacing
  </p>
  </div>
</div>

NOTES:
- Use BEM syntax as a convention to prevent name collisions

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Component CSS</h2>
    <p>Associate React components with CSS snippet</p>

    <pre class="large"><code class="lang-javascript">import './Card.scss'

const Card = ({title, imageUrl, message}) => (
  &lt;div className="card">
    &lt;h2 className="card\__title">{title}&lt;/h2>
    &lt;img src={imageUrl} className="card\__image" />
    &lt;p className="card\__message">{message}&lt;/p>
  &lt;/div>
)</code></pre>

    <div class="code-highlight" style="height: 70px; top: 253px;"></div>
  </div>
</div>

NOTES:
- Component CSS is the exact same as Global CSS
  * Except the CSS is imported by the Component
  * Instead of some external process that bundles everything
  * Therefore if the Component isn't used in the app the CSS won't be included in the bundle

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Component CSS</h2>
    <p>Associate React components with CSS snippet</p>

    <pre class="large"><code class="lang-css">/\* Card.scss \*/

.card { }
.card\__title { }
.card\__image { }
.card\__message { }</code></pre>
  </div>
</div>

NOTES:
- Same BEM style CSS class names convention because eventually it'll all be merged
- If the convention is broken you could still have collisions
- Hopefully your global CSS was already modularized, so this transition shouldn't be tough

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>CSS Modules</h2>
    <p>Automatically scope CSS class names to the component</p>

    <pre class="large"><code class="lang-javascript">import css from './Card.scss'

const Card = ({title, imageUrl, message}) => (
  &lt;div className={css.root}>
    &lt;h2 className={css.title}>{title}&lt;/h2>
    &lt;img src={imageUrl} className={css.image} />
    &lt;p className={css.message}>{message}&lt;/p>
  &lt;/div>
)</code></pre>

    <div class="code-highlight" style="height: 70px; top: 253px;"></div>
  </div>
</div>


NOTES:
- CSS Modules are similar to Component CSS
  * except the import of the CSS will return an object lookup with a generated class name

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>CSS Modules</h2>
    <p>Automatically scope CSS class names to the component</p>

    <pre class="large"><code class="lang-css">/\* Card.scss (source) \*/

.root { }
.title { }
.image { }
.message { }</code></pre>
  </div>
</div>

NOTES:
- No need for naming conventions
- Just name the classes what they are w/o worry about collision

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>CSS Modules</h2>
    <p>Automatically scope CSS class names to the component</p>

    <pre class="large"><code class="lang-css">/\* Card.css (generated) \*/

.Card\__root\__\_d74hQ { }
.Card\__title\__\_37fhU { }
.Card\__image\__\_ndh2e { }
.Card\__message\__\_84QQj { }</code></pre>
  </div>
</div>

NOTES:
- The generated CSS classes will be unique so there's no way they can collide
- The generated markup will also have the same class names

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Inline styles</h2>
    <p>Forgo CSS classes in favor of inline styles</p>

    <pre class="large"><code class="lang-javascript">import styles from './Card.styles'

const Card = ({title, imageUrl, message}) => (
  &lt;div style={styles.root}>
    &lt;h2 style={styles.title}>{title}&lt;/h2>
    &lt;img src={imageUrl} style={styles.image} />
    &lt;p style={styles.message}>{message}&lt;/p>
  &lt;/div>
)</code></pre>

    <div class="code-highlight" style="height: 70px; top: 253px;"></div>
  </div>
</div>


NOTES:
- Then there's the "screw CSS" option w/ inline styles
  * Tired of dealing with class name collisions, specificity, unexpected cascade
  * Have lots of dynamic styles which can be challenging with CSS
- There was a big huge push for this in React mainly because of React Native
  * it doesn't support CSS, only inline styles
- If you want to share components across React & React Native you can't use CSS

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Inline styles</h2>
    <p>Forgo CSS classes in favor of inline styles</p>

    <pre class="large"><code class="lang-javascript">// Card.styles.js
export default {
  root: {
    display: 'flex',
    flexDirection: 'row'
  },
  title: {
    fontWeight: 'bold',
    fontSize: '2em'
  },
  ...
}</code></pre>
  </div>
</div>

NOTES:
- Inline styles use `camelCase` version of the property names instead of `kebab-case`
- Problem with inline styles in React is that it only supports what inline styles support
  * No media queries, pseudo-selectors, keyframe animations, etc

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 75%">
    <h2>`css-in-js`</h2>
    <p>Define your CSS using JavaScript</p>
    
    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 22%;">
        <a href="https://emotion.sh/" target="_blank"><img src="../../img/nav-react/emotion-logo.png" class="plain" /></a>
        <a href="https://emotion.sh/" target="_blank">Emotion</a>
      </div>
      <div style="flex:0 0 24%;">
        <a href="http://cssinjs.org/react-jss/" target="_blank"><img src="../../img/nav-react/jss-logo.png" class="plain" /></a>
        <a href="http://cssinjs.org/react-jss/" target="_blank">JSS</a>
      </div>
      <div style="flex:0 0 24%;">
        <a href="https://formidable.com/open-source/radium/" target="_blank"><img src="../../img/nav-react/radium-logo.svg" class="plain" /></a>
        <a href="https://formidable.com/open-source/radium/" target="_blank">Radium</a>
      </div>
      <div style="flex:0 0 28%;">
        <a href="http://styled-components.com/" target="_blank"><img src="../../img/nav-react/styled-components-logo.png" class="plain" /></a>
        <a href="http://styled-components.com/" target="_blank">styled components</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- New libraries have popped up to try to solve that issue in various clever ways
  * Most take what's defined as inline styles but map to unique CSS classes
  * Get the best of both worlds: JavaScript-scoped styling + full CSS functionality
- So if you're starting out, you may wanna start with vanilla CSS
  * But as you start bumping up against these problems, `css-in-js` solves those problems
  * And once you get comfortable with a `css-in-js` library then you can use it all the time

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Styling Resources</h2>
  
    <ul>
      <li><a href="https://medium.com/seek-blog/a-unified-styling-language-d0c208de2660" target="_blank">_A Unified Styling Language_</a></li>
      <li><a href="https://github.com/gajus/react-css-modules" target="_blank">React CSS Modules</a></li>
      <li><a href="http://www.material-ui.com/" target="_blank">Material UI</a></li>
      <li><a href="https://react.foundation/" target="_blank">React + Foundation</a></li>
      <li><a href="https://react-bootstrap.github.io/" target="_blank">React-Bootstrap</a></li>
      <li><a href="https://github.com/JedWatson/classnames" target="_blank">`classnames`</a></li>
      <li><a href="https://polished.js.org/" target="_blank">polished</a></li>
      <li><a href="http://postcss.org/" target="_blank">PostCSS</a></li>
    </ul>
  </div>
</div>

NOTES:
- Here are some miscellaneous resources regarding styling

/////
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/kaylie-kwon.jpg" alt="Kaylie Kwon" class="speaker-headshot" />
      <br />
      Kaylie Kwon
    </p>

    <h2>Motion in React</h2>

    <p>11:05 (Hall B)</p>
  </div>
</div>

NOTES:
- Kaylie is going to talk about styling in React
- Specifically about ways in which we can apply motion to increase user delight

=====
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>3. Single-Page Apps</h1>
  </div>
</div>

NOTES:
_[14 minutes]_

- Moving along to libraries needed for Single Page Apps
- Two main groups of libs

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 45%">
    <h2>Data fetching</h2>
    <p>Retrieve data to populate your app</p>
  
   <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:3em">
      <div style="flex:0 0 45%;">
        <a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank">Fetch API</a>
      </div>
      <div style="flex:0 0 45%;">
        <a href="https://github.com/axios/axios" target="_blank">axios</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- Your favorite batteries-included JS framework (like Angular) has a mechanism for making AJAX requests
  * React does not come with one because it's just the UI side
  * So the second you need to make an AJAX request, you need to figure out how to do it
- You could use jQuery, but that could lead you to to using it improperly with React
- Two main options for data fetching: native browser Fetch API & `axios` library
- Fetch API
  * Native to the browser
  * Promise-based
  * Need to polyfill for unsupported browsers
- `axios`
  * Existed before Fetch API
  * Watch to do requests w/o jQuery
  * Also promised-based
  * Has IE-11 support
  * Also includes request aliases like `get`, `post`, `delete`, etc.
  * Supports cancelling requests too
- Actually never used `axios`, always used Fetch API

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Fetch API</h2>
    <p>Handle AJAX natively</p>

    <pre class="large"><code class="lang-javascript">window.fetch('api.benmvp.com', {method: 'GET'})
  .then((response) => {
    // do something w/ response
  })
  .catch((err) => {
    // handle error
  })</code></pre>
  </div>
</div>

NOTES:
- Example using the native fetch API
- There's also an implementation for Node called `node-fetch`
  * `isomorphic-fetch` so your code can run in both environments

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Fetch Resources</h2>
  
    <ul>
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank">Using Fetch</a></li>
      <li><a href="http://www.benmvp.com/learning-es6-promises/" target="_blank">Learning ES6: Promises</a></li>
      <li><a href="https://github.com/github/fetch" target="_blank">`window.fetch` polyfill</a></li>
      <li><a href="https://github.com/benmvp/react-workshop/blob/master/04-fetch/" target="_blank">React Fundamentals Workshop - Fetch</a></li>
    </ul>
  </div>
</div>

NOTES:
-

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 45%">
    <h2>Routing</h2>
    <p>Keep your UI in sync with the URL</p>
  
   <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 45%;">
        <a href="https://github.com/ReactTraining/react-router" target="_blank"><img src="../../img/nav-react/react-router-logo.png" class="plain" /></a>
        <a href="https://github.com/ReactTraining/react-router" target="_blank">React Router</a>
      </div>
      <div style="flex:0 0 45%;">
        <a href="https://reach.tech/router" target="_blank"><img src="../../img/nav-react/reach-router-logo.svg" class="plain" style="margin-bottom: 2em" /></a>
        <a href="https://reach.tech/router" target="_blank">Reach Router</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- Then there's routing to keep your UI in sync w/ the URL
- React Router is the main router
  * v4 was a complete API change which had drawbacks
  * Most prevalent in use
- Reach Router was a complete rethink by Ryan Florence
  * Intended to be accessible by default
  * Manages focus of your app on route transitions
  * Has ambiguous path ranking algorithm
  * Relative links, "not found" default components, etc.
- Active development is happening on both
- Give Reach Router a try

=====
<!-- .slide: data-background="url(../../img/nav-react/tomoe-steineck-787193-blue-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>4. Forms</h1>
  </div>
</div>

NOTES:
_[16 minutes]_

- Let's be real, forms are hard
  * Forms with validation are hard
  * And in React, it's no different
- Forms are hard because, the requirements are always different
  * Form level errors
  * Form element level errors
  * Synchronous validation
  * Async validation via AJAX
  * Validation that depends on the values of multiple fields
  * Errors that should show immediately (used username)
  * Errors that should wait until form submission
- React has a guide on Forms
  * But speaks mostly about how to maintain form state
  * Nothing about form validation & the complications

/////
<!-- .slide: data-background="url(../../img/nav-react/tomoe-steineck-787193-blue-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 65%">
    <h2>Form state managers</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-between ;margin-top:5%">
      <div style="flex:0 0 30%;">
        <a href="http://final-form.org/" target="_blank"><img src="../../img/nav-react/react-final-form-logo.png" class="plain" style="width: 65%" /></a>
        <a href="http://final-form.org/" target="_blank" style="display: block">Final Form</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="https://jaredpalmer.com/formik/" target="_blank"><img src="../../img/nav-react/formik-logo.svg" class="plain" style="width: 60%" /></a>
        <a href="https://jaredpalmer.com/formik/" target="_blank" style="display: block">Formik</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="https://redux-form.com/" target="_blank"><img src="../../img/nav-react/redux-form-logo.png" class="plain" /></a>
        <a href="https://redux-form.com/" target="_blank">Redux Form</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- The original is Redux Form
  * But relied on having Redux (we haven't gotten to)
  * It's also a pretty big lib for simple forms
  * Kept adding on feature requests
- Erik decided to do a rebuild
  * Created React Final Form
  * No dependencies; small footprint
  * Works with React render props
  * New features are added via plugins
  * Battle-proven with all of the existing features of Redux Form
  * Has 30+ examples/recipes
- While React Final Form was happening
  * Jared created Formik
  * Also wanted a Redux-free form implementation
  * Basically built at the same time
  * More or less feature parity

///// 

<!-- .slide: data-background="url(../../img/nav-react/tomoe-steineck-787193-blue-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Form Resources</h2>
  
    <ul>
      <li><a href="https://reactjs.org/docs/forms.html" target="_blank">Forms in React</a></li>
      <li><a href="https://github.com/benmvp/react-workshop/tree/master/src/react/05-email-form" target="_blank">React FUNdamentals Workshop - Forms</a></li>
    </ul>
  </div>
</div>

=====
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
_[17 minutes]_

- At this point we actually have everything we need to build Production-level apps
  * React (obviously)
  * Tooling w/ CRA that creates production builds
  * Styling
  * Single Page-Apps
  * Forms
- But there's more to cover
- Moving into the needs of large-scale apps

=====
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>5. Testing</h1>
  </div>
</div>

NOTES:
_[18 minutes]_

- I hate to put testing so far, but the previous 4 really are more important

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <h2>Testing Utilities</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-between; margin-top:5%">
      <div style="flex:0 0 30%;">
        <a href="https://reactjs.org/docs/test-utils.html" target="_blank"><img src="../../img/react/react-logo.png" class="plain" style="width:45%;" /></a>
        <a href="https://reactjs.org/docs/test-utils.html" target="_blank">ReactTestUtils</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="http://airbnb.io/enzyme" target="_blank" style="display:block">Enzyme</a>
      </div>
      <div style="flex:0 0 40%;">
        <a href="https://github.com/kentcdodds/react-testing-library" target="_blank" style="display:block"><img src="../../img/nav-react/react-testing-library-logo.png" class="plain" style="width:40%" /></a>
        <a href="https://github.com/kentcdodds/react-testing-library" target="_blank">react-testing-library</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- The utilities are about unit testing your components *without* having to run in a browser
- `ReactTestUtils`
  * Has rudimentary utilities
  * Likely don't want to use
- Enzyme is the dominant one
  * Been around basically since the beginning of React
  * Has a very jQuery-like interface for inspecting & interacting w/ components
  * We use it at Eventbrite
  * Provides lots of utility methods
  * But a lot of the utilities you really shouldn't use in unit testing
  * Too easy to write tests that assume implementation details of your components
- `react-testing-library`
  * Created by Kent C. Dodds in response to Enzyme problem
  * Gaining in popularity
  * Enables & encourages writing tests that use your components as end users use them
  * Wanna try it out on my next projects
- All work in your favorite test runner: Jest, Mocha + Chai, etc.

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Jest + Enzyme</h2>

    <pre class="large"><code class="lang-javascript">import {mount} from 'enzyme'
import Button from './Button'

test('toggles active state onClick', () => {
  const component = mount(
    &lt;Button style="primary">Go&lt;/Button>
  )
  const button = component.find('button')

  button.simulate('click')

  expect(button).toHaveClassName('btn--active')
})</code></pre>

    <div class="code-highlight" style="height: 70px; top: 685px;"></div>
  </div>
</div>

NOTES:
- This is how we can unit test a component
- It still blows my mind that we can do this **without** a browser
- When unit testing React components, you want to test the logic in the component
  * But only via its public API
  * What it renders, and the callback handler props it calls

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Testing Resources</h2>
  
    <ul>
      <li><a href="https://github.com/FormidableLabs/enzyme-matchers" target="_blank">`jest-enzyme`</a></li>
      <li><a href="https://github.com/benmvp/react-workshop/tree/master/src/testing" target="_blank">React Testing FUNdamentals Workshop</a></li>
      <li><a href="https://github.com/eventbrite/javascript/blob/master/react/testing.md" target="_blank">Eventbrite React Testing Best Practices</a></li>
      <li><a href="https://facebook.github.io/jest/blog/2016/07/27/jest-14.html" target="_blank">Jest 14.0: React Tree Snapshot Testing</a></li>
      <li><a href="https://github.com/avajs/ava/blob/master/docs/recipes/react.md" target="_blank">Ava + React</a></li>
    </ul>
  </div>
</div>

=====
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>6. App Data Management</h1>
  </div>
</div>

NOTES:
_[20 minutes]_

- We're starting to get further out from the center
- Up until this point, we've implicitly been using React to store application data
- Once the data becomes too complex or too many components want to modify that data it's time for a data management library!

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 50%">
    <h2>Flux Implementations</h2>
    <p>Make application state mutations predictable</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <a href="http://redux.js.org/" target="_blank"><img src="../../img/nav-react/redux-logo.png" class="plain" /></a>
		    <a href="http://redux.js.org/" target="_blank">Redux</a>
      </div>
	    <div style="flex:0 0 45%;">
        <a href="http://mobxjs.github.io/mobx/" target="_blank"><img src="../../img/nav-react/mobx-logo.png" class="plain" /></a>
		    <a href="http://mobxjs.github.io/mobx/" target="_blank">MobX</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- Most people use Redux
  * Been a bit of a backlash
  * Mainly because people have been using it before they need it and w/o understanding it
  * Using it before they really needed it
  * Look we're talking about Redux at Step 6!
- Redux uses the concept of reducers where you generate new state on actions
- Mobx uses Observables that subscribe to mutations to state

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 65%">
    <h2>Immutability</h2>
    <p>Provide immutable collections for JavaScript</p>

    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 30%;">
        <a href="https://facebook.github.io/immutable-js/" target="_blank"><img src="../../img/nav-react/immutable-logo.png" class="plain" /></a>
      </div>
	    <div style="flex:0 0 30%;">
        <a href="https://github.com/rtfeldman/seamless-immutable" target="_blank">`seamless-immutable`</a>
      </div>
	    <div style="flex:0 0 30%;">
        <a href="https://github.com/mweststrate/immer" target="_blank"><img src="../../img/nav-react/immer-logo.png" class="plain" /></a>
      </div>
    </div>
  </div>
</div>


NOTES:
- While on the subject of mutating state...
- By default, JavaScript arrays, objects and other collections are mutable
  * Normally you would just enforce a standard that data cannot be mutated
  * That's how React works
  * This leads to a lot of defensive copying with the spread operator
  * Making lots of copies can hurt performance
- Instead you can use a library like `Immutable`, `seamless-immutable` or `immer` to have true immutable objects
- `Immutable` is the big player, yet another library from Facebook
  * Only used it a bit
  * Found the API a bit cumbersome
  * Constantly going to and from Immutable and native objects
  * Don't _really_ want my React components to have to care, just Redux
- `seamless-immutable` is an alternative that has data structures that are backwards-compatible
  * They work just like Arrays or Objects except they don't mutate and have extra functionality
  * A lot lighter than Immutable
- `immer` takes a completely different approach
  * Just found out about it last month
  * Instead of creating a whole new set of immutable objects with their own API
  * It provides a `produce()` helper
  * You give the function the object you want to mutate & a function that does the mutation
  * And it returns the "next state" of the object
  * Very similar to the "reducer" concept introduced by Redux
  * Seems almost built for React
  * Huge pro is that it works w/ normal JS objects/arrays

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/michel-weststrate.jpg" alt="Michel Weststrate" class="speaker-headshot" />
      <br />
      Michel Weststrate
    </p>

    <h2>Immer, Immutability and the Wonderful World of Proxies</h2>

    <p>12:30 (Hall A)</p>
  </div>
</div>

NOTES:
- Luckily for us (and me) Michel is going to dive deep into how immer works
- You'll be able to see the positive developer experience it gives

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/react-next/adam-klein.jpg" alt="Adam Klein" class="speaker-headshot" />
      <br />
      Adam Klein
    </p>

    <h2>How to Write Bad Code in Redux</h2>

    <p>14:30 (Hall A)</p>
  </div>
</div>

NOTES:
- And Adam is going to talk to us about how to write bad Redux code
- Cuz he's fed up of us all writing good Redux 😉

=====
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Other considerations</h1>
  </div>
</div>

NOTES:
_[22 minutes]_

- There are other considerations too
- Don't have time to discuss them but at least wanted y'all to see 'em

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start;">
  <div class="content-overlay" style="width: 45%">

    <h2>7. Server-side Rendering</h2>
    <div style="display:flex;align-items:flex-end;justify-content:space-between;">
      <div style="flex:0 0 22%;">
        <a href="https://nextjs.org/"><img src="../../img/nav-react/nextjs-logo.svg" class="plain" style="margin-bottom: 1em" /></a>
        <a href="https://nextjs.org/">Next.js</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="https://www.gatsbyjs.org/"><img src="../../img/nav-react/gatsby-logo.svg" class="plain" /></a>
        <a href="https://www.gatsbyjs.org/" style="display:block">Gatsby</a>
      </div>
      <div style="flex:0 0 28%;">
        <a href="https://github.com/jaredpalmer/razzle"><img src="../../img/nav-react/razzle-logo.png" class="plain" style="background-color: #ddd; margin-bottom: 2em" /></a>
        <a href="https://github.com/jaredpalmer/razzle" style="display:block">Razzle</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="https://expressjs.com/">Express</a>
      </div>
    </div>
  </div>
</div>
<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <h2>8. API Optimization</h2>
    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:-10%">
      <div style="flex:0 0 30%;">
        <a href="https://facebook.github.io/relay/"><img src="../../img/nav-react/relay-logo.svg" class="plain" style="width:100%;" /></a>
        <a href="https://facebook.github.io/relay/">Relay</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="http://dev.apollodata.com/"><img src="../../img/nav-react/apollo-logo.svg" class="plain" style="width:100%;margin:2em 0" /></a>
        <a href="http://dev.apollodata.com/">Apollo</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="http://netflix.github.io/falcor/"><img src="../../img/nav-react/falcor-logo.svg" class="plain" style="width:100%;margin:3em 0" /></a>
        <a href="http://netflix.github.io/falcor/" style="display:block">Falcor</a>
      </div>
  </div>
</div>

NOTES:
- For **Performance & SEO** you want to server-side render
- Also have options for **optimizing REST API** requests
- Don't have time to get into these, but...

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start; margin-bottom: 1em">
  <div class="content-overlay">
    <h2>Server-side Rendering Resources</h2>
  
    <ul>
      <li><a href="https://github.com/brillout/awesome-ssr" target="_blank">Awesome SSR</a>
      <li><a href="https://github.com/bitinn/node-fetch" target="_blank">`node-fetch`</a> / <a href="https://github.com/matthew-andrews/isomorphic-fetch" target="_blank">`isomorphic-fetch`</a></li>
      <li><a href="https://github.com/nfl/react-helmet" target="_blank">`react-helmet`</a></li>
      <li><a href="https://koajs.com/" target="_blank">Koa</a></li>
    </ul>
  </div>
</div>

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>API Optimization Resources</h2>
  
    <ul>
      <li><a href="https://www.howtographql.com/" target="_blank">How to GraphQL</a></li>
      <li><a href="https://github.com/apollographql/apollo-client-devtools" target="_blank">Apollo Client Devtools</a></li>
      <li><a href="https://www.prisma.io/" target="_blank">Prisma</a></li>
      <li><a href="https://www.graph.cool/" target="_blank">Graphcool</a></li>
      <li><a href="https://github.com/chentsulin/awesome-graphql" target="_blank">Awesome GraphQL</a></li>
    </ul>
  </div>
</div>

NOTES:
- ...here are some resources for each

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Quick Recap</h1>
  </div>
</div>

NOTES:
_[25 minutes]_

- Quick tl;dr in case you missed anything

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 80%">
    <div style="display:flex;flex-wrap:wrap;align-items:flex-start;justify-content:space-around">
	    <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>0. React & JavaScript</div>
        <a href="https://facebook.github.io/react/" target="_blank"><img src="../../img/react/react-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em;display:flex;flex-direction:column;justify-content:flex-end">
        <div>1. Tooling</div>
        <a href="https://github.com/facebook/create-react-app" target="_blank" style="margin-top: 1em;display: block">Create React App</a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>2. Styling</div>
        <a href="https://emotion.sh/" target="_blank"><img src="../../img/nav-react/emotion-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>3. Single-Page Apps</div>
        <a href="https://reach.tech/router" target="_blank"><img src="../../img/nav-react/reach-router-logo.svg" class="plain" style="width: 65%; margin-top: 1.0em" /></a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>4. Forms</div>
        <a href="http://final-form.org/" target="_blank"><img src="../../img/nav-react/react-final-form-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>5. Testing</div>
        <a href="http://airbnb.io/enzyme" target="_blank" style="margin-top: 1em;display: block">Enzyme</a>
      </div>
      <div style="flex: 0 0 33%">
        <div>6. App Data Management</div>
        <a href="http://redux.js.org/" target="_blank"><img src="../../img/nav-react/redux-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%">
        <div>7. Performance & SEO</div>
        <a href="https://nextjs.org/" target="_blank"><img src="../../img/nav-react/nextjs-logo.svg" class="plain" style="width: 50%" /></a>
      </div>
      <div style="flex: 0 0 33%">
        <div>8. API Optimization</div>
        <a href="http://dev.apollodata.com/" target="_blank"><img src="../../img/nav-react/apollo-logo.svg" class="plain" style="width:50%" /></a>
      </div>
    </div>
  </div>
</div>

NOTES:
- 0/ Obviously start off with React & learn it well
  * Can't emphasize this enough!
- 1/ For tooling using Create React App
  * Until you know what part of the infra you want to invest your time
- 2/ For styling probably start of with CSS
  * But then take a look at Emotion
- 3/ Give new Reach Router a try
  * Of course the Fetch API
- 4/ Give React Final Form a try for sophisticated form handling
- 5/ Use Enzyme (or `react-testing-library`) + Jest for your unit testing
- 6/ Redux for app state management
- 7/ For SSR rendering look into Next.js
  * (but use Gatsby for any sort of static site)
- 8/ If you jump into GraphQL take a look at Apollo


- **Cool thing:** Can tailor your stack to your team and existing codebase

=====
<!-- .slide: data-background="url(../../img/webdev/matt-jones-42954-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 40%" class="content-overlay">
  
  <h1>Ben Ilegbodu</h1>

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="/" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  <br />

  <p>Ask me anything!<br /><a href="http://www.benmvp.com/ama/" target="_blank">benmvp.com/ama</a></p>
  
  </div>
</div>

NOTES:
- So that's it!
- Just flooded you with a lot of information
  * Slides are available online
- Hopefully 1, 2 or all 8 of these suggestions will prove useful to you
  * Got some notes scribbled to go check things out
  * You don't need to be overwhelmed and try to learn at once
  * Get good at one and build on it


- **Conference:** Inviting me all the way out here to share my knowledge/experience with y'all
- **YOU!** For being such an engaged audience
  * If you've got questions feel free to find me during the conference
  * Or ping me in Twitter or my AMA


- Thanks!
