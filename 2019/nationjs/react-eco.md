<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 50%;" class="content-overlay">

  <h1>Navigating the Ecosystem</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@nationjs](https://twitter.com/nationjs)</p>

  <br />

  <p>December 6, 2019</p>

  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- If you're new to React you might hear that on top of learning React
  * You need to know Redux, css-in-js, server-side rendering, etc.
  * All at the same time
  * It can be so overwhelming
_ **How many of you have used React before?**
- React is still just a UI library
  * Need to pick libraries for fetching data, managing state, etc. for full framework
  * How can you pick the right thing, if you've never used it before?
- So I want to walk through the different libs in the React ecosystem
  * 1/ Provide my opinion of which category of libs you should prioritize first
  * 2/ I'll also try to give a list of options for each category and my preference
- For those of you who have been doing React for a while
  * Hopefully there will be a thing or two that'll be new for you
  * If not, you can use the info I provide when your coworkers ask you why you picked a lib
  * Have a better argument than just "Because... I liked it?"

=====
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>React</h1>
  </div>
</div>

NOTES:
- Before we jump in the ecosystem
  * Lemme quickly chat about React first

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 75%">
    <div style="display:flex;align-items:center;justify-content:space-between;">
      <a href="https://facebook.github.io/react/tutorial/tutorial.html" target="_blank" style="width: 45%">
        <img src="../../img/react/react-logo.png" class="plain" />
      </a>
      <div>
        <h2><a href="https://egghead.io/courses/advanced-react-component-patterns">Component patterns</a></h2>
        <h2><a href="https://reactjs.org/docs/concurrent-mode-intro.html">Concurrent Mode</a>🔥</h2>
        <h2><a href="https://reactjs.org/docs/error-boundaries.html">Error boundaries</a> <sup style="font-size: .5em">16</sup></h2>
        <h2><a href="https://reactjs.org/docs/optimizing-performance.html#profiling-components-with-the-chrome-performance-tab">Performance</a> <sup style="font-size: .5em">16.5</sup></h2>
        <h2><a href="https://reactjs.org/docs/fragments.html">Fragments</a> <sup style="font-size: .5em">16.2</sup></h2>
        <h2><a href="https://reactjs.org/docs/code-splitting.html#reactlazy">Suspense</a> <sup style="font-size: .5em">16.6</sup></h2>
        <h2><a href="https://reactjs.org/docs/context.html">Context</a> <sup style="font-size: .5em">16.3</sup></h2>
        <h2><a href="https://reactjs.org/docs/hooks-intro.html">Hooks</a> <sup style="font-size: .5em">16.8</sup></h2>
      </div>
    </div>
  </div>
</div>


NOTES:
- For those just starting out, learn React and learn it _really_ well
  * Sounds like an obvious statement
  * But it's important to focus on this first
  * Learn how to maintain state properly & leverage reconciler (aka "virtual DOM")
  * If you're coming from MVC model, one-way data flow can be counter-intuitive
- After the basics, keep up with the latest features...
  * React continues to evolve
- Advanced component patterns
  * Presentational vs. container components
  * Sharing component logic with higher-order components / render props / hooks
- Implementing error boundaries (v16)
- Using Fragments (v16.2) & Context API (v16.3)
- We can monitor and optimize performance (v16.5)
- Leveraging new Suspense system with auto-code splitting (v16.6)
- Hooks which completely changed how we write components (v16.8)
- Concurrent Mode which was announced at React Conf in October (still experimental)

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 40%">
    <h2>React Dev Tools</h2>
    <p>Help debug React props & state</p>

    <img src="../../img/nav-react/react-dev-tools-v4.png" alt="Screenshot of React Dev Tools v4" style="width: 100%" />

    <p>Available for <a href="https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi?hl=en" target="_blank">Chrome</a> and <a href="https://addons.mozilla.org/en-US/firefox/addon/react-devtools/" target="_blank">Firefox</a></p>

    <p>(Performance debugging in v16.5)</p>
  </div>
</div>

NOTES:
- Also want to point out the React Dev Tools
  * They are super helpful in debugging React components
- You browse the React component tree just like the DOM tree
  * And you can look at the component props as well as the state
  * Keeps improving to provide more debugging capability
  * Just recently with the release of React 16.5 enabling performance debugging
- Available for Chrome, Firefox, and now Chromium-based Edge

/////
<!-- .slide: data-background="url(../../img/nav-react/craig-lovelidge-362228-yellow-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/nationjs/kathryn-grayson-nanz.jpg" alt="Kathryn Grayson Nanz" class="speaker-headshot" />
      <br />
      Kathryn Grayson Nanz
    </p>

    <h2>Creating a Component Library in React</h2>

    <p>10:45a</p>
  </div>
</div>

NOTES:
- This is a high-level overview talk
  * And the purpose is the ecosystem, not React itself
- If you wanna know more of the basics of building React components
  * **Kathryn** will be providing insights on creating a component lib from scratch
  * Right after this talk

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-steph-curry.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- Before we continue can I get everyone to stand up?

/////
<!-- .slide: data-background="#000 url(../../img/family/ilegbodu-family-photo-2019.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- My name is Ben Ilegbodu
- Christian, Husband, Father
- _Family introductions_
- We live in Pittsburg, CA (far east bay)
- Also a Google Developer Expert & Microsoft MVP in Web Technologies

/////

![Stitch Fix Corporate logo (light)](../../img/stitchfix/lockup-solid-vert-gender-neutral-light.svg)
<!-- .element: class="plain" style="width: 75%" -->

NOTES:
- Just recently started working at Stitch Fix
  * As a Frontend Architect
  * Which I'm super excited about
- Stitch Fix is an online personal styling service
  * Take the effort out of shopping by providing a selection of clothes picked just for you
  * And sent to your door on a frequency that you choose
  * Combines technology & data science
  * With an actual human stylist
- We're hiring!
  * Headquarters is in SF
  * But we have remote engineers all over the country
  * Colleague **Ross** is here!

=====
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Ok, enough about me
- Let's talk about the React ecosystem
- Going to be *a lot* of stuff covered
  * Not going to be able to teach you how to use any given lib
  * Instead my goal is to expose you to the libs so you can investigate
  * Will also give my preferences
- Tweeted a link to slides cuz there will be **a lot** of resources

=====
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>1. Tooling</h1>
  </div>
</div>

NOTES:
- Probably the biggest complaint w/ React isn't React itself
  * But the tooling needed to get set up
- I think the problem is that there's so much choice in this area
  * You need to know how the tools work before you could get up and running

/////
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 80%">
    <h2>Bundlers</h2>
    <p>Help gather dependencies, transpile ES6+, etc.</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 15%;">
        <a href="https://developers.google.com/closure/compiler/" target="_blank"><img src="../../img/nav-react/closure-logo.svg" class="plain" /></a>
        <a href="https://developers.google.com/closure/compiler/" target="_blank">Closure</a>
      </div>
      <div style="flex:0 0 15%;">
        <a href="https://parceljs.org/" target="_blank"><img src="../../img/nav-react/parcel-logo.png" class="plain" style="width: 100%" /></a>
        <a href="https://parceljs.org/" target="_blank">Parcel</a>
      </div>
      <div style="flex:0 0 15%;">
        <a href="http://prepack.io/" target="_blank"><img src="../../img/nav-react/prepack-logo.png" class="plain" style="width: 100%" /></a>
        <a href="http://prepack.io/" target="_blank">Prepack*</a>
      </div>
      <div style="flex:0 0 15%;">
        <a href="https://www.pika.dev/blog/pika-web-a-future-without-webpack/" target="_blank"><img src="../../img/nav-react/pika-web-logo.jpg" class="plain" /></a>
        <a href="https://www.pika.dev/blog/pika-web-a-future-without-webpack/" target="_blank"><code>@pika/web</code></a>
      </div>
      <div style="flex:0 0 15%;">
        <a href="http://rollupjs.org/" target="_blank"><img src="../../img/nav-react/rollup-logo.svg" class="plain" /></a>
        <a href="http://rollupjs.org/" target="_blank">Rollup</a>
      </div>
      <div style="flex:0 0 15%;">
        <a href="https://webpack.github.io/" target="_blank"><img src="../../img/nav-react/webpack-logo.png" class="plain" /></a>
        <a href="https://webpack.github.io/" target="_blank">Webpack</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- If you're building out your own custom stack there's a lot to think about


- First you have to figure out which bundling system you'll use
  * This is space has a lot of players
- **Webpack** is the prevailing bundler right now
  * But you have to add loaders and other configurations to make it do what you need
  * It has its own huge ecosystem
- **Rollup** works specifically with EcmaScript modules
  * Introduced the concept of "tree-shaking" feature that results in less generated code
  * But instead of bundling the code into one file, it transpiles individual files
  * Good for libraries
- **Parcel** is a newer tool that boasts blazing fast build times
  * It also is "zero-config" so it has a lot of functionality out of the box
- **Google Clousre Compiler** is a very mature code analyzer & optimizer
  * It analyzes it, removes dead code & rewrites/minimizes what's left
  * It's pretty complicated to set up an run (requires Java JDK installed)
- **Prepack** is yet another new tool for making JS code run faster
  * From Facebook
  * Computations that can be done at compile-time instead of run-time get eliminated
  * Still in early DEV stage so not quite ready for production
  * It's been that way for a while now
- **`@pika/web`** is relatively new
  * Installs modern npm dependencies in a way that lets them run natively in the browser
  * **Without** a bundler like webpack
  * Even if they have dependencies themselves
  * Like Rollup, works with ESM packages
- I'd say go with Webpack
  * It's still constantly evolving
  * Webpack has "tree-shaking" too
  * There's a whole ecosystem around it
- It's at this step where the "JavaScript fatigue" really kicks in
  * Your typical JS developer doesn't want to or know how to configure these bundlers
  * Just work please

/////
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

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
- Continuing on we have task runners
  * Build files, run shell scripts, etc.
- **Grunt** was the original & dominant
  * Then because Grunt files became so unmanageable
- **Gulp** approached it with streams in a functional way
  * But still can have large Gulp files
- But with "building fatigue" and the fact that webpack could do so much of this for us
- **NPM scripts** have lately become the most popular
  * Essentially wrappers around command line calls
- If things are simple, use npm scripts.
- If things are complex, use Gulp since it's functional

/////
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

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
- **Flow** is exclusively for type checking
- **TypeScript** is a superset of JavaScript that includes type checking plus future JavaScript:
  * It introduced classes before they were in ES2015
  * It has interfaces and enums which JS does not
- 2018 seemed to be the "Year of TypeScript"
  * Excitement continues to grow now in 2019
  * The industry has seemed to have selected TypeScript
  * The integration with VSCode is 👍🏾

/////
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Create React App</h2>
    <p>Create React apps with no build configuration</p>

    <pre class="large" style="margin:5% 0"><code>$> npx create-react-app nationjs

$> cd nationjs

$> npm start

### For production

$> npm run build</code></pre>

    <p><a href="https://reactjs.org/blog/2018/10/01/create-react-app-v2.html" target="_blank">CRA 2.0</a>: Babel 7, Webpack 4, TypeScript, CSS Modules, etc.</p>
  </div>
</div>


NOTES:
- So that was everything you need to set up your React app!
  * And I didn't even go into a bunch of nitty gritty details
- This had been the biggest complaint about React
  * How to get started

-----

- If you are just getting started or don't need highly custom stack, you can use Create React App
  * Created by the React team
  * Allows you to bootstrap super quick w/ zero-config
  * Can still configure it a great deal
  * And if you need to config something it doesn't support you can "eject"
- Creates an optimized bundle you can ship to production
- Much better than the (bloated) boilerplates / starter-kits
- v2 shipped a year ago with lots of updated infra

/////
<!-- .slide: data-background="url(../../img/nav-react/erin-simmons-382355-sea-life-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Tooling resources</h2>

    <ul>
      <li><a href="https://medium.com/@ajmeyghani/javascript-bundlers-a-comparison-e63f01f2a364" target="_blank"><em>JavaScript Bundlers, a Comparison</em></a></li>
      <li><a href="https://www.youtube.com/watch?v=QFKZmBMgvus" target="_blank">What's New with React Dev Tools 4</a> ⏯️</li>
      <li><a href="https://github.com/joshwcomeau/guppy" target="_blank">Guppy</a></li>
      <li><a href="https://github.com/zkat/npx" target="_blank">`npx`</a></li>
      <li><a href="https://github.com/creationix/nvm" target="_blank">Node Version Manager</a></li>
      <li><a href="https://www.youtube.com/watch?v=-wBNV7i_b9o" target="_blank">TypeScript & React</a> ⏯️</li>
      <li><a href="https://github.com/sindresorhus/awesome-npm" target="_blank">Awesome npm resources and tips</a></li>
      <li><a href="https://github.com/jamiebuilds/scritch" target="_blank">`scritch`</a></li>
      <li><a href="https://blog.risingstack.com/yarn-vs-npm-node-js-package-managers/" target="_blank"><em>Yarn vs NPM</em></a></li>
      <li><a href="https://webpack.js.org/configuration/dev-server/" target="_blank">`webpack-dev-server`</a></li>
      <li><a href="https://flow.org/en/docs/react/" target="_blank">Flow + React</a></li>

    </ul>
  </div>
</div>

NOTES:
- Here are some miscellaneous resources regarding all the tools we talked about
- Guppy is a GUI for managing React app infra and running tasks

=====
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>2. Styling</h1>
  </div>
</div>


NOTES:
- Now that we can build an app, we need to make it look good
  * Because visuals are just as important as interaction
- There are _at least_ **5 ways** to tackle the styling problem

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 85%">
    <h2>Styling</h2>
    <p>Style your components</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 18%;">
        <a href="https://getbootstrap.com/" target="_blank"><img src="../../img/nav-react/bootstrap-logo.svg" class="plain" /></a>
        <a href="https://getbootstrap.com/" target="_blank">Global CSS</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="https://create-react-app.dev/docs/adding-a-stylesheet/" target="_blank"><img src="../../img/why-react/css-3-logo.svg" class="plain" style="width: 60%" /></a>
        <a href="https://create-react-app.dev/docs/adding-a-stylesheet/" target="_blank">Component CSS</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="https://github.com/gajus/babel-plugin-react-css-modules" target="_blank"><img src="../../img/nav-react/react-css-modules-logo.png" class="plain" /></a>
        <a href="https://github.com/gajus/babel-plugin-react-css-modules" target="_blank">CSS Modules</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="https://reactjs.org/docs/dom-elements.html#style" target="_blank"><img src="../../img/react/react-logo.png" class="plain" /></a>
        <a href="https://reactjs.org/docs/dom-elements.html#style" target="_blank">Inline Styles</a>
      </div>
      <div style="flex:0 0 18%;">
        <a href="https://emotion.sh/" target="_blank"><img src="../../img/nav-react/css-in-js-logo.svg" class="plain" /></a>
        <a href="https://emotion.sh/" target="_blank">css-in-js</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- **Global CSS** and **Component CSS** are similar
  * Components reference CSS classes that have to be appropriately namespaced to prevent collisions
  * **Global CSS** would be something like Bootstrap or Foundation which is built completely separate
  * **Component CSS** is actually imported by the component
  * Therefore if the Component isn't used in the app the CSS won't be included in the bundle
  * Need a bundler that can handle importing CSS (like CRA)
- 3rd option is **CSS Modules**
  * There's lots to like about CSS Modules
  * CSS Modules are similar to Component CSS
  * Except the import of the CSS returns sandboxed class names
  * The generated CSS classes will be unique so there's no way they can collide
  * Also need a bundler, there's a babel plugin
- The folks who choose the **Inline Styles** option are in the "screw CSS" camp
  * Tired of dealing with specificity wars, unexpected cascade, etc.
  * Were adding `!important` everywhere
  * Having lots of dynamic styles which can be challenging with CSS
  * There was a big huge push for this early in React when React Native came out
  * Problem is it only supports what inline styles support
  * No media queries, pseudo-selectors, keyframe animations, etc
- New **`css-in-js`** libraries have popped up to try to solve that issue in various clever ways
  * Most take what's defined as inline styles but map to unique CSS classes
  * Get the best of both worlds: JavaScript-scoped styling + full CSS functionality

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

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
- Emotion is the newest and super popular
  * It's taken learnings from all the others to create a flexible API

-----

- So if you're starting out, you may wanna start with Component CSS
  * Because `css-in-js` libs are yet another API to learn
  * But as you start bumping up against problems w/ CSS
  * Try out `css-in-js` solution like Emotion
  * And once you get comfortable with a `css-in-js` library then you can use it all the time

/////
<!-- .slide: data-background="url(../../img/nav-react/james-thornton-741535-sea-anemone-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Styling Resources</h2>

    <ul>
      <li><a href="https://medium.com/dailyjs/what-is-actually-css-in-js-f2f529a2757" target="_blank"><em>What actually is CSS-in-JS</em></a></li>
      <li><a href="https://github.com/gajus/babel-plugin-react-css-modules" target="_blank">React CSS Modules</a></li>
      <li><a href="https://github.com/nairinarinyan/react-scoped-styles" target="_blank">`react-scoped-styles`</a></li>
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
- `react-scoped-styles` is similar to CSS Modules but you don't have to import the CSS module
  * Works on file naming convention

=====
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>3. Single-Page Apps</h1>
  </div>
</div>

NOTES:
- Moving along to libraries needed for Single Page Apps
- Two main subcategories

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 45%">
    <h2>Data fetching</h2>
    <p>Retrieve data to populate your app</p>

   <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:3em">
      <div style="flex:0 0 45%;">
        <a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank"><img src="../../img/nav-react/fetch-logo.svg" class="plain" /></a>
        <a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank">Fetch API</a>
      </div>
      <div style="flex:0 0 45%;">
        <a href="https://github.com/axios/axios" target="_blank"><h3 style="margin-bottom: 2.5em"><code>axios</code></h3></a>
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
- **Fetch API**
  * Native to the browser
  * Promise-based
  * Need to polyfill for unsupported browsers
- **`axios`**
  * Existed before Fetch API
  * A way to do requests w/o jQuery
  * Also promised-based
  * Has IE11 support
  * Also includes request aliases like `get`, `post`, `delete`, etc.
  * Supports cancelling requests too
- Actually never used `axios`, always used Fetch API

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Fetch Resources</h2>

    <ul>
      <li><a href="https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API/Using_Fetch" target="_blank">Using Fetch</a></li>
      <li><a href="https://github.com/github/fetch" target="_blank">`window.fetch` polyfill</a></li>
      <li><a href="https://reactjs.org/docs/hooks-effect.html#tip-optimizing-performance-by-skipping-effects" target="_blank">Using the Effect Hook</a></li>
      <li><a href="https://use-http.com/" target="_blank"><code>use-http</code></a> / <a href="https://github.com/simoneb/axios-hooks" target="_blank"><code>axios-hooks</code></a></li>
      <li><a href="https://blog.logrocket.com/how-to-make-http-requests-like-a-pro-with-axios/" target="_blank"><em>How to make HTTP requests like a pro with Axios</em></a></li>
      <li><a href="https://codeburst.io/how-to-fetch-data-from-an-api-with-react-hooks-9e7202b8afcd" target="_blank"><em>How To Fetch Data From An API With React Hooks</em></a></li>
      <li><a href="http://www.benmvp.com/learning-es6-promises/" target="_blank">Learning ES6: Promises</a></li>
    </ul>
  </div>
</div>

NOTES:


/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 45%">
    <h2>Routing</h2>
    <p>Keep your UI in sync with the URL</p>

   <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 45%;">
        <a href="https://reacttraining.com/react-router/" target="_blank"><img src="../../img/nav-react/react-router-logo.png" class="plain" /></a>
        <a href="https://reacttraining.com/react-router/" target="_blank">React Router</a>
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
- **React Router** is the main router
  * v4 was a complete API change to be more component-based
  * But it had some drawbacks
  * However, it's still most prevalent in use
- **Reach Router** was a complete rethink
  * Intended to be accessible by default
  * Manages focus of your app on route transitions
  * Has flexible routing to figure out which route matches
  * Relative links, "not found" default components, etc.
- They are going to merge together  (hooks-based API)
  * Into `react-router`, but the API will be similar to `@reach/router`
  * If you have a few routes use `@reach/router` (easier to migrate in a commit)
  * If you have lots of routes use `react-router` (fully backwards compatible w/ iterative migration)

/////
<!-- .slide: data-background="url(../../img/nav-react/ishan-seefromthesky-798062-school-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Routing Resources</h2>

    <ul>
      <li><a href="https://reacttraining.com/blog/reach-react-router-future/" target="_blank"><em>The Future of React Router and @reach/router</em></a></li>
      <li><a href="https://redux.js.org/advanced/usage-with-react-router" target="_blank">Redux Usage with React Router</a></li>
      <li><a href="https://tylermcginnis.com/react-router-code-splitting/" target="_blank"><em>Redux Usage with React Router</em></a></li>
      <li><a href="https://tylermcginnis.com/react-router-recursive-paths/" target="_blank"><em>Recursive paths with React Router</em></a></li>
      <li><a href="https://tylermcginnis.com/react-router-sidebar-breadcrumbs/" target="_blank"><em>Rendering a Sidebar or Breadcrumbs with React Router v4</em></a></li>
    </ul>
  </div>
</div>

NOTES:

=====
<!-- .slide: data-background="url(../../img/nav-react/tomoe-steineck-787193-blue-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>4. Forms</h1>
  </div>
</div>

NOTES:
- Let's be real, no one _really_ likes forms
  * Forms are not that hard
  * But forms **with validation** are definitely hard
  * And in React, it's no different
- Forms of different size
  * Two-field login form
  * Many-field and nested checkout form
- The validation requirements are always different
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
    <p>Manage complex form validity</p>

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
- The original is **Redux Form**
  * But relied on having Redux (we haven't gotten to)
  * It's also a pretty big lib for simple forms
  * Kept adding on feature requests
- Erik decided to do a rebuild
  * Created **React Final Form**
  * No dependencies (Redux independent); small footprint
  * In fact there's a base `Final Form` which is framework agnostic
  * New features are added via plugins
  * React version is hooks compatible
  * Battle-proven with all of the existing features of Redux Form
  * Has 30+ examples/recipes
- While React Final Form was happening
  * Jared created **Formik**
  * Also wanted a Redux-free form implementation
  * Basically built at the same time
  * More or less feature parity
- If you've used Redux Form, React Final Form has similar API

/////

<!-- .slide: data-background="url(../../img/nav-react/tomoe-steineck-787193-blue-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Form Resources</h2>

    <ul>
      <li><a href="https://github.com/rmolinamir/react-formalized" target="_blank">`react-formalized`</a></li>
      <li><a href="https://upmostly.com/tutorials/form-validation-using-custom-react-hooks/" target="_blank"><em>Form Validation using Custom React Hooks</em></a></li>
      <li><a href="https://reactjs.org/docs/forms.html" target="_blank">Forms in React</a></li>
      <li><a href="https://github.com/benmvp/react-workshop/tree/master/src/react/05-email-form" target="_blank">React FUNdamentals Workshop - Forms</a></li>
    </ul>
  </div>
</div>

NOTES:
- `react-formalized` is a collection of pre-styled HTML form elements

=====
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>5. Testing</h1>
  </div>
</div>

NOTES:
- Testing is super important for the integrity of your app
- It's funny, none of us _really_ enjoy writing tests
  * But we wish there were a lot of tests when we're refactoring
  * Like bumping packages

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <h2>Testing Utilities</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-between; margin-top:5%">
      <div style="flex:0 0 30%;">
        <a href="https://cypress.io" target="_blank"><img src="../../img/nav-react/cypress-logo.png" class="plain" style="background:white" /></a>
        <a href="https://cypress.io" target="_blank">Cypress</a>
      </div>
      <div style="flex:0 0 30%;">
        <a href="http://airbnb.io/enzyme" target="_blank" style="display:block">Enzyme</a>
      </div>
      <div style="flex:0 0 40%;">
        <a href="https://testing-library.com/react" target="_blank" style="display:block"><img src="../../img/nav-react/react-testing-library-logo.png" class="plain" style="width:40%" /></a>
        <a href="https://testing-library.com/react" target="_blank">React Testing Library</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- **Cypress** is predominantly used for end-to-end testing
  * Runs in a browser, but isn't slow Selenium or Webdriver
  * But can also used a development platform for TDD
  * Becoming increasingly popular
  * Call also use it with a visual testing utility like Percy
- **Enzyme** is probably most common
  * Been around basically since the beginning of React
  * Has a very jQuery-like interface for inspecting & interacting w/ components
  * Provides lots of utility methods
  * But a lot of the utilities you really shouldn't use in unit testing
  * Too easy to write tests that assume implementation details of your components
- `react-testing-library`
  * Created by Kent C. Dodds in response to Enzyme problem
  * Gaining a popularity
  * Encourages writing tests that use your components as end users use them
  * Best used as component integration tests
  * In between traditional unit tests and E2E tests
  * Wanna try it out on my next projects
- All work in your favorite test runner: Jest, Mocha + Chai, etc.

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: start">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/nationjs/matt-crowder.jpg" alt="Matt Crowder" class="speaker-headshot" />
      <br />
      Matt Crowder
    </p>

    <h2>Testing React</h2>

    <p>11:40a</p>
  </div>
</div>

NOTES:
- There's so much more I could say about testing
  * Especially `enzyme` vs `react-testing-library`
  * But thankfully **Matt** will be teaching how to rewrite effective, non-brittle tests for our apps
- After the break!

/////
<!-- .slide: data-background="url(../../img/nav-react/jong-marshes-452773-sea-turtle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Testing Resources</h2>

    <ul>
      <li><a href="https://github.com/testing-library/jest-dom" target="_blank"><code>jest-dom</code></a> / <a href="https://github.com/FormidableLabs/enzyme-matchers" target="_blank"><code>jest-enzyme</code></a></li>
      <li><a href="https://kentcdodds.com/blog/making-your-ui-tests-resilient-to-change" target="_blank"><em>Making your UI tests resilient to change</em></a></li>
      <li><a href="https://www.youtube.com/watch?v=5XQOK0v_YRE" target="_blank">Intro to Cypress</a> ⏯️</li>
      <li><a href="https://www.youtube.com/watch?v=MXfZeE9RQDw" target="_blank">Cypress.io + Percy</a> ⏯️</li>
      <li><a href="https://medium.com/@nitinpatel_20236/unit-testing-custom-react-hooks-caa86f58510" target="_blank"><em>Unit Testing Custom React Hooks</em></a></li>
      <li><a href="https://github.com/Raathigesh/majestic/" target="_blank">Majestic</li>
      <li><a href="https://testingjavascript.com/" target="_blank">Testing JavaScript with Kent C. Dodds</a></li>
      <li><a href="https://facebook.github.io/jest/blog/2016/07/27/jest-14.html" target="_blank">React Tree Snapshot Testing</a></li>
      <li><a href="https://github.com/avajs/ava/blob/master/docs/recipes/react.md" target="_blank">Ava + React</a></li>
    </ul>
  </div>
</div>

NOTES:
- `jest-dom` & `jest-enzyme` have collections of Jest matchers for `react-testing-library` & enzyme objects
- Majestic is a zero-config GUI for Jest

=====
<!-- .slide: data-background="url(../../img/nav-react/shaun-low-498556-blue-gray-coral-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- At this point we actually have everything we need to build Production-level apps
  * 0/ React (obviously)
  * 1/ Tooling w/ CRA that creates production builds
  * 2/ Styling
  * 3/ Single Page-Apps
  * 4/ Forms
  * 5/ Testing
- But there's more to cover
- Moving into the needs of large-scale apps

=====
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>6. App Data Management</h1>
  </div>
</div>

NOTES:
- Everybody's favorite topic!
- Up until this point, we've implicitly been using components to store application data
  * Possibly using Context API to pass down global props like language, theme, etc.
- Once the data becomes too complex or too many components want to modify that data
  * _THEN_ it maybe time for a data management library!

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 75%">
    <h2>State Managers</h2>
    <p>Make application state mutations predictable</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 30%;">
        <a href="https://reactjs.org/docs/hooks-intro.html" target="_blank"><img src="../../img/react/react-logo.png" class="plain" /></a>
        <a href="https://reactjs.org/docs/hooks-intro.html" target="_blank">Hooks</a> + <a href="https://reactjs.org/docs/context.html" target="_blank">Context</a>
      </div>
	    <div style="flex:0 0 20%;">
        <a href="http://mobxjs.github.io/mobx/" target="_blank"><img src="../../img/nav-react/mobx-logo.png" class="plain" style="margin-bottom: 1.5em;" /></a>
		    <a href="http://mobxjs.github.io/mobx/" target="_blank">MobX</a>
      </div>
	    <div style="flex:0 0 20%;">
        <a href="http://redux.js.org/" target="_blank"><img src="../../img/nav-react/redux-logo.png" class="plain" style="margin-bottom: 1.5em;" /></a>
		    <a href="http://redux.js.org/" target="_blank">Redux</a>
      </div>
	    <div style="flex:0 0 30%;">
        <a href="https://xstate.js.org/docs/" target="_blank"><img src="../../img/nav-react/xstate-logo.svg" class="plain" style="margin-bottom: 2.5em;" /></a>
		    <a href="https://xstate.js.org/docs/" target="_blank">XState</a>
      </div>
    </div>
  </div>
</div>


NOTES:
- Look we're talking about Redux at Step 6!
  * This is when I think it makes sense to learn and add it in
- Most people use **Redux**
  * Been a bit of a backlash
  * I know the maintainers have felt that
  * Mainly because people have been using it before they need it and w/o understanding it
  * Or using a lib (like `redux-form`) that's forcing them
  * Their data isn't really changing, just need it passed to multiple components
  * Then there's questions of where component state should go
- **Redux** uses the concept of reducers where you generate new state on actions
  * Immutability is key!
  * Helps separate update of data from actions that cause them
- **Mobx** uses Observables that subscribe to mutations to state
  * Get to change the state with traditional methods
- **XState** is a library for modeling event-based state transitions
  * Diagram all the states of your app state and the events that trigger between the states
  * The goal is that you make sure you handle all the states and prevent mutually exclusive states
  * It's probably more difficult to set-up because it's based on mathematical finite state machines
  * Worth using if you have lots of states and transitions (events)
- Quite possible that with React **Context & Hooks** we won't even need Redux or MobX
  * We reach for Redux to easily get data to multiple components
  * Or to abstract manipulations of data into easily-testable utilities (reducers)
  * Can accomplish that with `useReducer` hook + context API

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 65%">
    <h2>Immutability</h2>
    <p>Provide immutable collections for JavaScript</p>

    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 30%;">
        <a href="https://facebook.github.io/immutable-js/" target="_blank" style="background-color: #fff;display:block"><img src="../../img/nav-react/immutable-logo.png" class="plain" /></a>
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
- Instead you can use a libraries to have true immutable objects
- **`Immutable`** is the big player, yet another library from Facebook
  * Only used it a bit
  * Found the API a bit cumbersome
  * Has its own set of objects: Collections, Dictionaries, etc.
  * Constantly going to and from Immutable and native objects
  * Don't _really_ want my React components to have to care, just Redux
- **`seamless-immutable`**
  * Alternative that has data structures that are backwards-compatible
  * They work just like Arrays/Objects except they don't mutate & have extra functionality
  * A lot lighter than `Immutable`
- **`immer`** takes a completely different approach
  * It doesn't use objects at all
  * It's a newer solution
  * You give `produce()` the object you want to mutate and a function that performs the mutation
  * Get to write the mutations in "normal" JavaScript
  * It efficiently batches up the mutations & returns the "next state" of the object

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/nationjs/dillon-mulroy.jpg" alt="Dillon Mulroy" class="speaker-headshot" />
      <br />
      Dillon Mulroy
    </p>

    <h2>Event Driven Redux</h2>

    <p>12:10p</p>
  </div>
</div>

NOTES:
- If you wanna learn more about managing state
- **Dillon** will be challenging the status quo on Redux best practices
  * Wants to shift our mental model to be more event-driven
  * May be the same spirit as `xstate`
- Right before lunch!

/////
<!-- .slide: data-background="url(../../img/nav-react/eva-tillmann-677057-clown-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>App Data Management Resources</h2>

    <ul>
      <li><a href="https://kentcdodds.com/blog/application-state-management-with-react" target="_blank"><em>Application State Management with React</em></a></li>
      <li><a href="https://github.com/zalmoxisus/redux-devtools-extension" target="_blank">Redux DevTools Extension</a></li>
      <li><a href="https://redux-starter-kit.js.org/" target="_blank">Redux Starter Kit</a></li>
      <li><a href="https://medium.com/octopus-labs-london/replacing-redux-with-react-hooks-and-context-part-1-11b72ffdb533" target="_blank"><em>Replace Redux with React Hooks + Context</em></a></li>
      <li><a href="https://github.com/markerikson/redux-ecosystem-links" target="_blank">Redux Ecosystem</li>
      <li><a href="https://github.com/xgrommx/mobx-ecosystem" target="_blank">MobX Ecosystem</li>
      <li><a href="https://github.com/jamiebuilds/unstated" target="_blank">Unstated</a></li>
      <li><a href="https://github.com/jamiebuilds/reduxxx" target="_blank">Reduxxx</a></li>
    </ul>
  </div>
</div>

NOTES:
- Redux Starter Kit - batteries-include toolset for making using Redux easier
  * Helpers for creating actions, reducers, selectors, etc
- Unstated is a Redux alternative to get rid of the boilerplate
  * Manage app state, much like component state
- Reduxxx - eliminates implicit dependencies by having components subscribe directly to app state
  * "Redux, explicit" hence the XXX
  * Makes code-splitting a lot easier because you don't have to try to inject new reducers
  * Designed as an API change to React itself

=====
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>7. Server-side Rendering</h1>
  </div>
</div>

NOTES:
- Chances are if you're building an app of significant size...
  * SEO & initial render speed will matter
- Rendering server-side can help both
  * This is called "Isomorphic/Universal React"
- Rendering the same components server-side improves initial startup performance
  * Because content is already there
- Google includes rendering speed in their ranking algorithm which affects SEO
  * Even though now they execute JavaScript
- There's also SMO (social media optimization) as well
  * Having content for social media sites like Twitter, Slack
  * They can use for richer previews
  * They're likely not executing JavaScript
- React provides a method that will render the component tree to a string
  * You can then include in server response

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <h2>Server-side rendering</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-between ;margin-top:5%">
      <div style="flex:0 0 22%;">
        <a href="https://www.gatsbyjs.org/"><img src="../../img/nav-react/gatsby-logo.svg" class="plain" /></a>
        <a href="https://www.gatsbyjs.org/" style="display:block">Gatsby</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="https://nextjs.org/"><img src="../../img/nav-react/nextjs-logo.svg" class="plain" style="margin-bottom: 1em" /></a>
        <a href="https://nextjs.org/">Next.js</a>
      </div>
      <div style="flex:0 0 22%;">
        <a href="https://nodejs.org"><img src="../../img/browsers/nodejs-logo.png" class="plain" /></a>
        <a href="https://nodejs.org">Node</a>
      </div>
      <div style="flex:0 0 28%;">
        <a href="https://github.com/jaredpalmer/razzle"><img src="../../img/nav-react/razzle-logo.png" class="plain" style="background-color: #ddd; margin-bottom: 2em" /></a>
        <a href="https://github.com/jaredpalmer/razzle" style="display:block">Razzle</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- A couple of different options for server-side rendering
- Original option was to roll your own solution
  * When you have a **Node** backend
  * Using Node server library, like _Express_ or _Koa_
  * Hook in one of the routers (`reach-router` / `react-router`)
  * Data fetching with `isomorphic-fetch`
- **Gatsby** is an amazing static-site generator
  * Use it for my site benmvp.com
  * It's all static pages: HTML, CSS & JS
  * Generated at build time
  * Creates a progressive web app, with data-prefetching for performance
  * Uses GraphQL to retrieve data for components
- **Next.js** is a framework for server-rendered React applications by Zeit
  * Has built-in routing, code-splitting, CSS support, data fetching, etc
  * Adding static generation so that the app can be hybrid
- **Razzle** is a library for bootstrapping server-side rendering
  * Abstracts all complex configuration needed for SSR into a single dependency
  * Great if you're not ready to buy into `Next.js` or React Server
  * Works with Vue, Angular & other libs as well
  * You still figure out your routing, data fetching, etc

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2><a href="http://www.benmvp.com/slides/2017/render/iso-react.html" target="_blank">SSR without a Node back-end...</a></h2>

    <a href="https://www.youtube.com/watch?v=zxtcr8Zuvfs" target="_blank">
      <img src="../../img/nav-react/iso-react-render-conf-2017.png" alt="" style="width: 880px" atl="Isomorphic React sans Node talk at RenderConf 2017" />
    </a>

    <p>RenderConf 2017</p>
  </div>
</div>


NOTES:
- If your backend is in Django / Rails / .Net / etc. it's a bit more challenging
- But I have a 2-yr old talk that explains it all!
  * It's how we solved it at Eventbrite cuz our backend is Django

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 40%">
    <p>
      <img src="../../img/nationjs/allison-kunz.png" alt="Allison Kunz" class="speaker-headshot" />
      <br />
      Allison Kunz
    </p>

    <h2>Intro to NextJS</h2>

    <p>4:20p</p>
  </div>
</div>

NOTES:
- If you are interested in the performance optimizations of server-side rendering...
- **Allison** will be giving a general overview of Next
  * Will be comparing it to CRA which is generally what we all use to build React apps

/////
<!-- .slide: data-background="url(../../img/nav-react/francisco-jesus-navarro-hernandez-534560-yellow-purple-starfish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Server-side Rendering Resources</h2>

    <ul>
      <li><a href="https://tylermcginnis.com/react-router-server-rendering/" target="_blank">_Server Rendering with React Router_</a>
      <li><a href="https://github.com/brillout/awesome-ssr" target="_blank">Awesome SSR</a>
      <li><a href="https://expressjs.com/" target="_blank">Express</a> / <a href="https://koajs.com/" target="_blank">Koa</a></li>
      <li><a href="https://github.com/bitinn/node-fetch" target="_blank">`node-fetch`</a> / <a href="https://github.com/matthew-andrews/isomorphic-fetch" target="_blank">`isomorphic-fetch`</a></li>
      <li><a href="https://github.com/nfl/react-helmet" target="_blank">`react-helmet`</a></li>
    </ul>
  </div>
</div>

NOTES:
- Traditionally your React app sits within a `<div>` in the HTML doc
  * Doesn't have access to anything in the `<head>`
  * `react-helmet` (by the NFL) provides and API to update it
  * server-side too

=====
<!-- .slide: data-background="url(../../img/nav-react/vlad-tchompalov-446902-brown-pepper-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>8. API Optimization</h1>
  </div>
</div>

NOTES:
- As your app grows larger you may find that you're making lots of REST API requests
- A single user action can result in 3+ AJAX requests
  * ...because of how the micro-services are divided
  * Managing sequential or parallel requests can get tricky
  * Also can create sluggish UI
- We sometimes solve this with rest by creating "uber APIs"
  * But then we're requesting a whole bunch of data we're not using
  * Bad for mobile
- There are cutting-edge technologies to tackle this problem

/////
<!-- .slide: data-background="url(../../img/nav-react/vlad-tchompalov-446902-brown-pepper-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 65%">
    <h2>API Optimization</h2>
    <p>Retrieve only the data you need</p>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
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
        <a href="http://netflix.github.io/falcor/" style="display:block"><strike>Falcor</strike></a>
      </div>
    </div>
  </div>
</div>


NOTES:
- Facebook & Netflix tackled the same problem with different approaches
- In both cases you get only the data you want, nothing more, nothing less
- Can no longer use your traditional REST APIs
  * However, you can start by putting this in front of backend REST APIs
- Facebook came up with **GraphQL**, a generic query language for APIs
- **Relay** & **Apollo** are connections of React to GraphQL on the client
  * You have to build out your GraphQL server
- **Falcor**
  * I mention Falcor because it was a thing
  * But Netflix doesn't even support it
  * GraphQL "won"
- Be aware that **Apollo** will basically take over your app
  * Can be good or bad
  * _Good_ in the sense that it basically reducers your need for Redux
  * _Bad_ if you already have Redux and you need to move things around

/////
<!-- .slide: data-background="url(../../img/nav-react/vlad-tchompalov-446902-brown-pepper-fish-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>API Optimization Resources</h2>

    <ul>
      <li><a href="https://www.howtographql.com/" target="_blank">How to GraphQL</a></li>
      <li><a href="https://www.youtube.com/watch?v=F_M8v6MK0Sc" target="_blank">GraphQL in 3 Components</a> ⏯️</li>
      <li><a href="https://github.com/apollographql/apollo-client-devtools" target="_blank">Apollo Client Devtools</a></li>
      <li><a href="https://www.prisma.io/" target="_blank">Prisma</a></li>
      <li><a href="https://www.graph.cool/" target="_blank">Graphcool</a></li>
      <li><a href="https://github.com/chentsulin/awesome-graphql" target="_blank">Awesome GraphQL</a></li>
    </ul>
  </div>
</div>

NOTES:
- How to GraphQL is a full-stack tutorial for GraphQL
- _GraphQL in 3 Components_ is a talk from Eve Porcello from React Rally 2018

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Quick Recap</h1>
  </div>
</div>

NOTES:
- _Deep breath_
- So that was a lot
  * Let's be real, you probably didn't catch everything
  * Chances are you got distracted by Slack or text
  * Or the squats wore you out
- Here's a quick tl;dr if you just want the answers

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 80%">
    <div style="display:flex;flex-wrap:wrap;align-items:flex-start;justify-content:space-around">
	    <div style="flex: 0 0 33%; margin-bottom: 0.8em">
        <div>0. React</div>
        <a href="https://facebook.github.io/react/" target="_blank"><img src="../../img/react/react-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%; margin-bottom: 0.8em;display:flex;flex-direction:column;justify-content:flex-end">
        <div>1. Tooling</div>
        <a href="https://github.com/facebook/create-react-app" target="_blank" style="display: block"><img src="../../img/nav-react/create-react-app-logo.svg" class="plain" style="width: 33%" /></a>
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
        <a href="https://testing-library.com/react" target="_blank"><img src="../../img/nav-react/react-testing-library-logo.png" class="plain" style="width:30%" /></a>
      </div>
      <div style="flex: 0 0 33%">
        <div>6. App Data Management</div>
        <a href="https://reactjs.org/docs/hooks-intro.html" target="_blank"><img src="../../img/react/react-logo.png" class="plain" style="width: 33%" /></a>
      </div>
      <div style="flex: 0 0 33%">
        <div>7. Server-side Rendering</div>
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
- Here are all the categories and my opinions
  * **Cool thing:** Can tailor your stack to your team and existing codebase
- 0/ Learn **React** _really well_
  * Especially hooks which are the future
- 1/ Use **Create React App** to get bootstrapped
  * eject when necessary
- 2/ Try out **Emotion** from styling
  * But probably start off with Component CSS
- 3/ Use **`@react/router`** for your routes
  * Or **`react-router`** if you have lots
- 4/ Use **`react-final-form`** for form validation w/o Redux
- 5/ Use **React Testing Library** for testing components w/o a browser
  * But you'll probably want **Cypress** + **Percy** too for happy path E2E tests
- 6/ See how far you can go with Hooks + Context
  * Only reach for **Redux** as a last resort
- 7/ Try out **Next.js** if you need server-side rendering
- 8/ Go ahead and use **Apollo** when you're requesting lots of data

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
  * Reminder: slides are available online
- Hopefully 1, 2 or all 8 of these suggestions will prove useful to you
  * You've got some notes scribbled to go check things out later
  * You don't need to be overwhelmed and try to learn at once
  * Get good at **one thing** and build on it
- **Conference:** Inviting me to share my knowledge/experience with y'all (**Grey**)
- **YOU!** For being such an engaged audience
  * Not going to take any questions
  * But if you've got questions, feel free to find me afterwards
  * I also have swag to give away!
  * But if you're introverted or miss the opportunity, ping me in Twitter or my AMA
- Thank you so much and enjoy the rest of the conference!
