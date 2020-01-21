<!-- .slide: data-background="url(../../img/perfect-lib/jeshoots-com-VdOO4_HFTWM-tools-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 50%;" class="content-overlay">

  <h1>The “perfect” library tooling</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@jsconfhi](https://twitter.com/jsconfhi)</p>

  <br />

  <p>February 5, 2020</p>

  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- It's "perfect" (in quotes) because it's obviously highly subjective
  * These are naturally my opinions
- But they're birthed out building and consuming hundreds of libraries
- I'm always obsessed with doing things the "best way"
  * Even when I'm just starting
- So these are learnings over the years doing platform-y things
  * In open-source & on the job
  * As well as watch how more prolific folks have done it

=====
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Whenever we're talking about non-end-user features
  * We need to ask ourselves what exactly is the benefit
  * Does this even matter?
- If it's not a feature for the end user
  * Then it needs to be a feature for the dev
  * So that they can build faster/better for end user
- Otherwise, we find ourselves bike-shedding

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 70%">
    <a href="https://kentcdodds.com/blog/why-users-care-about-how-you-write-code" target="_blank">
      <img src="../../img/perfect-lib/kent-c-dodds-why-users-care-about-how-you-write-code.png" alt="Article by Kent C. Dodds entitled 'Why users care about how your write code'" class="plain" />
    </a>
    <p>
      <a href="https://kentcdodds.com/blog/why-users-care-about-how-you-write-code" target="_blank">
        <em>Why users care about how you write code</em>
      </a>
    </p>
  </div>
</div>

NOTES:
- Kent C. Dodds wrote a blog post entitled _Why users care about how you write code_
- He asserts: "The only thing that matters in software is the experience of the user."
- But: "The experience of the user is indirectly, but strongly coupled to how we build software"
- Therefore the post can be summed up as:
  * "Our measure of success should be how well we deliver what the user wants (and no more)"
  * So "our choice of tools should be based on that fundamental goal"

=====
<!-- .slide: data-background="url(../../img/perfect-lib/nesa-by-makers-kwzWjTnDPLk-black-developers-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Users === Developers</h1>
  </div>
</div>

NOTES:
- In this case of our "perfect" library the "focus on the user" principle still applies too
  * Except, this time the "user" **is** the developer
- The library should provide the functionality it's designed to provide
  * In a well thought out API
  * I **won't** be talking about any of that today
- Everything else related to the repo has to also enable developers to build better user experiences
  * It's all the "other stuff" that we'll be talking about today

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
<!-- .slide: data-background="#000" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%">
    <img src="../../img/family/ilegbodu-family-christmas-2019.jpg" alt="Ilegbodu family at Christmas 2019" />
  </div>
</div>

NOTES:

- My name is Ben Ilegbodu
- Christian, Husband, Father
- _Family introductions_
- We live in Pittsburg, CA (far east bay)
- Also a Google Developer Expert & Microsoft MVP in Web Technologies

/////

![Stitch Fix Corporate logo (light)](../../img/stitchfix/lockup-solid-vert-gender-neutral-dark.svg)
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
  * Colleagues **James** & **Nathan** are here!

=====
<!-- .slide: data-background="url(../../img/perfect-lib/jeshoots-com-VdOO4_HFTWM-tools-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Ok, enough about me
- Let's talk about making this perfect repo
- Remember we're shifting are perspective to what our users, the developers, need

=====
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>1. Helpful docs</h1>
  </div>
</div>

NOTES:
- The first thing we need are helpful docs
- Docs that explain:
  * How to install the library
  * Examples of how to use the library
  * Full API spec once I know how to use the library
- Question: **So what makes this possible?**

/////
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Write docs first!</h1>
  </div>
</div>

NOTES:
- My suggestion is to write the docs first **before** implementation
- Why? Becase writting docs is hard
- It ensures that the docs actually get written!
  * There's nothing fun or exiciting about writing docs
  * We don't really wanna write them after we have a working implementation
- **NEXT SLIDE**

/////
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 70%">
    <img src="../../img/perfect-lib/no-docs-example.png" alt="An example of a repo with no docs" />
  </div>
</div>

NOTES:
- How many times have you seen repo with no docs?
  * I see this happen a lot with monorepo packages
- **NEXT SLIDE**

/////
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Write docs first!</h1>
  </div>
</div>

NOTES:
- We write the docs when we know how it works the least
  * After we've implemented, it's much harder to explain
  * It's harder to put yourself in the shoes of a newbie
  * We're more likely to add examples to tell **ourselves** how it should work
- We're more likely to have a cohesive API
  * As we try to make the API easy to use
  * We may need to revise functions we've already documented
  * But not a big deal cuz it's just Markdown files
- We can get feedback from others before implementation
  * In a format that's much better than an implementation spec

/////
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 75%">
    <div style="display:flex;flex-wrap:wrap;align-items:flex-start;justify-content:space-around">
      <div style="flex: 0 0 50%; margin-bottom: 2em;text-align: left;">
        <h3>References</h3>
        <ul>
          <li>is <strong>information-oriented</strong></li>
          <li>describes the machinery</li>
          <li>is accurate and complete</li>
        </ul>
      </div>
      <div style="flex: 0 0 50%; margin-bottom: 2em;text-align: left;">
        <h3>How-to guides</h3>
        <ul>
          <li>is <strong>goal-oriented</strong></li>
          <li>shows how to solve a problem</li>
          <li>is a series of steps</li>
        </ul>
      </div>
      <div style="flex: 0 0 50%; margin-bottom: 2em;text-align: left;">
        <h3>Explanations</h3>
        <ul>
          <li>is <strong>understanding-oriented</strong></li>
          <li>explains</li>
          <li>provides background &amp; context</li>
        </ul>
      </div>
	    <div style="flex: 0 0 50%; margin-bottom: 2em;text-align: left;">
        <h3>Tutorials</h3>
        <ul>
          <li>is <strong>learning-oriented</strong></li>
          <li>allows newbie to get started</li>
          <li>is a lesson</li>
        </ul>
      </div>
    </div>
    <p>
      <a href="https://www.divio.com/blog/documentation/" target="_blank"><em>What nobody tells you about documentation</em></a></a>
    </p>
  </div>
</div>

NOTES:
- So what sort of docs should you write?
- Turns out that there are at least **four types** of docs
- Tutorials, How-to guides, Explanation & Reference
  * Let's use `lodash` as an example
- **References** would be the API docs
  * Here are the parameters `pick()` takes and its return value
  * These are great for those who already know how to use `lodash`
- **How-to guides** are examples showing common use cases for lodash functions
  * These are typically paired with API docs
  * More complex ones are recipes or sample repos of how to use one or multiple functions
- **Explanations** are blogs/talks/videos to explain why using `_.chain` is bad
  * They clarify and illuminate a particular topic
  * They go more in depth than the API doc's coverage of a topic
- **Tutorials** would be `lodash` workshops we'd find **Egghead** or **Frontend Masters** or online
  * Lessons that take the reader by the hand to build an app with `lodash`
  * These are perfect newbies who may not even know what `lodash` is
- For your "perfect" library, you should have **References** & **How-to guides**

/////
<!-- .slide: data-background="url(../../img/perfect-lib/calle-macarone-15wIddvL5dU-emergency-instructions-guide-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 70%">
    <img src="../../img/perfect-lib/benmvp-cli-readme-table-of-contents.png" alt="An example table of contents from the @benmvp/cli repo" />
  </div>
</div>

NOTES:
- So in summary, my suggestion for the repo's `README` is:
- First, ALL the badges you can think of
  * Package version, build states, downloads, etc.
- Short description of the library's purpose
- Installation instructions, _including any necessary peer dependencies_
  * Need to include both `npm` & `yarn` instructions
- Quick guide on how to do common things
- Full API docs
  * May link to other Markdown files
  * Each function or configuration should include a **real-world example**
- Technical details
  * How it's faster, tech used, etc.
  * I hate when this is up top for multiple page scrolls!
- Contribution Guidelines
- License info

=====
<!-- .slide: data-background="url(../../img/perfect-lib/pop-zebra-wp81DxKUd1E-safety-helmets-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>2. TypeScript types</h1>
  </div>
</div>


NOTES:
- With helpful docs, the dev can develop their app
- In which case they'll need and want TypeScript types
- TypeScript is a typed superset of JavaScript that compiles to plain JavaScript.
- Now this may be be bit controversial
  * It's certainly my own bias
  * But the numbers back me up (from State of JS survey)

/////
<!-- .slide: data-background="url(../../img/perfect-lib/pop-zebra-wp81DxKUd1E-safety-helmets-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 75%">
    <h2>TypeScript adoption</h2>

    <div style="height: 750px; width:25%; margin:0 auto; position:relative; ">
      <div style="width: 50%; height: 100%; box-sizing: border-box; border: 10px solid black"></div>
      <div style="width: 100%; border-bottom: 3px solid black; display: flex; justify-content: space-around; position: absolute; bottom: 21%; left: 0">
        <span>21%</span>
        <a href="http://2016.stateofjs.com/2016/flavors/" target="_blank">2016</a>
      </div>
      <div style="width: 100%; border-bottom: 3px solid black; display: flex; justify-content: space-around; position: absolute; bottom: 33%; left: 0">
        <span>33%</span>
        <a href="https://2017.stateofjs.com/2017/flavors/results/" target="_blank">2017</a>
      </div>
      <div style="width: 100%; border-bottom: 3px solid black; display: flex; justify-content: space-around; position: absolute; bottom: 46.7%; left: 0">
        <span>47%</span>
        <a href="https://2018.stateofjs.com/javascript-flavors/overview/" target="_blank">2018</a>
      </div>
      <div style="width: 100%; border-bottom: 3px solid black; display: flex; justify-content: space-around; position: absolute; bottom: 58.5%; left: 0">
        <span>59%</span>
        <a href="https://2019.stateofjs.com/javascript-flavors/" target="_blank">2019</a>
      </div>
    </div>
  </div>
</div>

NOTES:
- TypeScript has become super popular
- 2018 was the year everyone "discovered" TypeScript
- Only 1/3 of devs had used TypeScript in 2017
- In 2018, it was 47%
- In 2019, it was nearly 60%
  * Add in those that are interested in learning: **80%**
- 8 out of every 10 developer will need TypeScript definitions from your lib
  * In order to build their app using your lib
- Question: **So what makes it possible to make TypeScript definitions available?**


/////
<!-- .slide: data-background="url(../../img/perfect-lib/pop-zebra-wp81DxKUd1E-safety-helmets-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 85%">
    <a href="http://definitelytyped.org/" target="_blank">
      <img src="../../img/perfect-lib/definitelytyped-screenshot.png" alt="A screenshot of the DefinitelyTyped homepage" class="plain" />
    </a>
    <p>
      <a href="http://definitelytyped.org/" target="_blank">DefinitelyTyped</a>
    </p>

  </div>
</div>

NOTES:
- One option is build your app in JavaScript
  * And then add TypeScript type declaration files to DefinitelyTyped
  * A repo of high quality TypeScript type definitions
- Nearly 7000 library type definition files are in the repo
  * `React`, `lodash`, `node`, etc
- The drawback is that you have to know quite a bit of TypeScript to generate these files manually
- And as your library updates, you'll have to keep the types in sync
- This can be a lot of work, so my suggestion is...


/////
<!-- .slide: data-background="url(../../img/perfect-lib/pop-zebra-wp81DxKUd1E-safety-helmets-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 75%">
    <a href="http://www.typescriptlang.org/docs/handbook/migrating-from-javascript.html" target="_blank">
      <img src="../../img/perfect-lib/typescript-migrating-from-javascript-tutorial.png" alt="A TypeScript tutorial on how to migrate from JavaScript" class="plain" />
    </a>
    <p>
      <a href="https://code.visualstudio.com/docs/languages/typescript" target="_blank">VS Code + TypeScript = ❤️</a>
    </p>
  </div>
</div>

NOTES:
- Write your library in TypeScript of course!
- There's definitely a learning curve to TypeScript, no doubt
- But in the interest of serving your users (the developers)
  * Writing in TypeScript is the best way to provide type definition files
  * Because they will be auto-generated
  * (more on how they make it into your package later)
- Written definition files are often buggy
  * It's almost better to have no definitions, than buggy ones
- It's also difficult to write types for code written un-typed
  * When code is untyped, we can make shortcut assumptions
  * These aren't allowed in TypeScript
  * So writing types could be challenging or impossible
- Visual Studio Code has great integrations with TypeScript too!

=====
<!-- .slide: data-background="url(../../img/perfect-lib/katka-pavlickova-Sf5Q7Ljjf58-volkswagen-beetles-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>3. Bug-free</h1>
  </div>
</div>

NOTES:
- So now I know how it works w/ the docs & have my TypeScript types to develop with
- While developing, there's nothing more frustrating than coming across a library bug
- Because we're pretty trusting initially, and think it's us
  * And spend countless hours debugging trying to figure out why it isn't working
- So for our library to be "perfect"
  * Need to do our absolute best to prevent 100% of bugs
- The question of course is
  * **What makes this possible?**

/////
<!-- .slide: data-background="url(../../img/perfect-lib/katka-pavlickova-Sf5Q7Ljjf58-volkswagen-beetles-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 31%;">
        <a href="https://www.typescriptlang.org/" target="_blank" style="display: block"><img src="../../img/nav-react/typescript-logo.png" class="plain" style="width: 95%" /></a>
		    Type checking
      </div>
      <div style="flex:0 0 31%;">
        <a href="http://eslint.org/" target="_blank" style="display: block"><img src="../../img/nav-react/eslint-logo.svg" class="plain" style="width: 95%"/></a>
        Linting
      </div>
      <div style="flex:0 0 31%;">
        <a href="https://jestjs.io/" target="_blank" style="display: block"><img src="../../img/nav-react/jest-logo-dark.svg" class="plain" style="width: 95%"/></a>
        Testing + Coverage
      </div>
  </div>
</div>

NOTES:
- The 3-headed monster of Type checking, Linting & Testing + Coverage
- **Type checking** comes with developing in TypeScript, which we just discussed
  * So not only is developing w/ TypeScript good for providing types for our users
  * It's also good for our users because it helps us avoid bugs!
  * The kind of bugs where things are unexpectedly `undefined`
  * Or you refactor a function and forget to update it somewhere
  * With VS Code this can happen _as you develop_
- **Linting** comes via ESLint
  * This also can happen _as you develop_ in your favorite editor
  * TypeScript catches a lot of the non-stylist errors ESLint catches
  * There are still some that are _likely_ errors
  * And then there are additional plugins for environments like React
- **Testing + Coverage** comes with Jest
  * Allows you to write unit tests
  * Can also check what percentage of your code has been tested
  * Unit testing is huge in keeping your lib bug-free
  * But of course it depends on you actually writing tests

/////
<!-- .slide: data-background="url(../../img/perfect-lib/katka-pavlickova-Sf5Q7Ljjf58-volkswagen-beetles-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Jest Projects</h2>
    <p>Run typing, linting & tests all within Jest</p>

    <pre class="large"><code class="lang-javascript">{
  "projects": [
    { "displayName": "test" },
    {
      "displayName": "lint",
      "runner": "jest-runner-eslint",
      "testMatch": ["&lt;rootDir>/**/*.ts"]
    }, {
      "displayName": "type",
      "runner": "jest-runner-tsc",
      "testMatch": ["&lt;rootDir>/**/*.ts"]
    }
  ]
}</code></pre>
  </div>
</div>

NOTES:
- Typically you'd run typing, linting & testing with 3 separate commands
  * But with Jest projects, you can run them all through Jest
- Jest is a platform that's broken up into 3 main parts
  * The "file collector" in the beginning that determines which files to run on
  * The "error reporter" at the end that displays success or failure
  * The "runner" in the middle which runs what we're validating
- Instead of running the Jest test runner, we can run eslint or `tsc` for Typescript
- This enables to run linting in watch mode, which `eslint` command doesn't support
  * Allows them to be run in parallel
  * But w/ consistent and grouped error messaging
- Simply call `jest` as the `"test"` script in `package.json`

/////
<!-- .slide: data-background="url(../../img/perfect-lib/katka-pavlickova-Sf5Q7Ljjf58-volkswagen-beetles-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-yaml">name: CI
on: [push, pull_request]
jobs:
  main:
    strategy:
      matrix:
        node: [10, 12, 13]
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node }}
      - run: npm ci
      - run: npm test
        env:
          CI: true</code></pre>
  </div>
</div>

NOTES:
- Lastly, it's not enough that we run our tests locally
  * Need to ensure that all code pushed to origin is validated
- It's vital that you have continuous integration (CI) setup
  * There are many CI tools out there
  * But lately I've been using Github actions and loving it
  * Can use it Github actions w/o registering for another service
- Here's a Github workflow to run tests on Node 10, 12 & 13
  * I always run on the even versions (LTS) and latest odd

/////
<!-- .slide: data-background="url(../../img/perfect-lib/katka-pavlickova-Sf5Q7Ljjf58-volkswagen-beetles-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://www.youtube.com/watch?v=ZJ43STkmK-4" target="_blank">Jest as a Platform</a> ⏯️</li>
      <li><a href="https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin" target="_blank"><code>@typescript-eslint/eslint-plugin</code></a></li>
      <li><a href="https://github.com/jest-community/jest-runner-eslint" target="_blank"><code>jest-runner-eslint</code></a> + <a href="https://github.com/azz/jest-runner-tsc" target="_blank"><code>jest-runner-tsc</code></a></li>
      <li><a href="https://github.com/jest-community/jest-watch-typeahead" target="_blank"><code>jest-watch-typeahead</code></a></li>
      <li><a href="https://github.com/features/actions" target="_blank">Github Actions</a></li>
    </ul>
  </div>
</div>

NOTES:
- Here's a video to talk by Rogelio Guzman on "Jest as a Platform"
- Miscellaneous packages for setting up TypeScript + Eslint + Jest
- All about Github actions


=====
<!-- .slide: data-background="url(../../img/perfect-lib/russ-ward-18MJRuL4tUE-plasma-cutter-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>4. Fixes come quickly</h1>
  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/perfect-lib/russ-ward-18MJRuL4tUE-plasma-cutter-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 45%">

  </div>
</div>

NOTES:

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Recap</h1>
  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 90%">

  </div>
</div>

NOTES:

=====
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1><code>@benmvp/cli</code></h1>
  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 45%">

  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 45%">
    <a href="https://twitter.com/jcreamer898/status/1217857477427040258" target="_blank">
      <img src="../../img/perfect-lib/jonathan-creamer-divops-tweet.png" alt="Jonathan Creamer tweet about starting a community for Frontend tooling called #divops" />
    </a>
    <p>
      <a href="https://bit.ly/div-ops-slack" target="_blank">Slack</a>
      | <a href="https://www.reddit.com/r/divops/" target="_blank">Subreddit</a>
    </p>
  </div>
</div>


NOTES:
- My friend Jonathan Creamer is passionate about Frontend tooling
- He's coined the term "divops" for the industry

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
- Hopefully there are a few new things you've learned
  * I've also likely forgotten some things so I'd love your feedback!
- **Conference:** Inviting me to share my knowledge/experience with y'all (**Kelly** + crew)
- **YOU!** For being such an engaged audience
  * Not going to take any questions
  * But if you've got questions, feel free to find me afterwards
  * I also have swag to give away!
  * But if you're introverted or miss the opportunity, ping me in Twitter or my AMA
- Thank you so much and enjoy the rest of the conference!
