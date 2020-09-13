<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 65%;" class="content-overlay">

  <h1>TypeScript + React = ❤️</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#TSConf](https://twitter.com/hashtag/TSConf)</p>

  <br />

  <p>October 9, 2020</p>


  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- TSConf is intended to be framework agnostic
  - Learn all the nitty gritty about TS
- They asked me to do a deep dive into React + TS


- **Slides are available online**

=====

# TS logo

NOTES:
- People ask “Why do I need to learn TypeScript when I already am productive with JavaScript”
- Especially since there'll be a learning curve
- I argue it’s a matter of perspective

/////

# jQuery logo

NOTES:
- Why do people who are productive in making apps with jQuery decide to learn something like React?

/////

# React logo

NOTES:
- They’ll find themselves struggling to do things in React that they can already do easily w/ jQuery
- Manipulating the DOM, for instance
- They’ll be “fighting” React instead of actually building the app
- But once they pass the learning curve, they’ll be able to build bigger and more sophisticated apps AND less buggy apps because they’re not maintaining state in the DOM triggered by events
- It’s because they already knew how to web dev with jQuery
- If they learned web dev for the start with React that sense of “is this necessary” isn’t there

/////

# React & JS logos

NOTES:
- It’s the same for JavaScript + TypeScript
- Because you already know how to build React apps in JavaScript, jumping to TypeScript may not seem worth it
- But if you were learning JavaScript as TypeScript from the beginning your perspective would be different
- No different than learning JS from the beginning and have to learn random quirks

/////

# React & TS logos

NOTES:
- Most talks on React + TypeScript just teach how to use TypeScript w/ React
- They are assuming you already wanna use TS and just wanna know how to

/////

# Kent's blog post

NOTES:
- But when adopting new tech we should always focus on the user
- The user doesn’t care what tech we use unless it makes the user experience better (less friction, more delightful, etc)

/////

# Bug photo

NOTES:
- Users definitely don’t want a buggy experience and of course, neither do we
- Cuz when there are bugs, users are less likely to use the product
- And when they use the product less, they purchase less
- And when they purchase less, we (the company) make less money
- And when we make less money, I (the developer employee) get fired!
- So my focus w/ TypeScript is on how using TS helps eliminate bugs

/////
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 65%;" class="content-overlay">

  <h1>How using TypeScript won’t get you fired!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#TSConf](https://twitter.com/hashtag/TSConf)</p>

  <br />

  <p>October 9, 2020</p>


  </div>
</div>

NOTES:
- In fact, I’m retitling the talk:
- How using TS won’t get you fired!
- 8 amazing bug-squashing features...
- just wait until you see #5!

=====

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
- We live in Pittsburg, CA (SF Bay Area)
- Also a Google Developer Expert & Microsoft MVP in Web Technologies

/////

![Stitch Fix Corporate logo (light)](../../img/stitchfix/lockup-solid-vert-gender-neutral-light.svg)
<!-- .element: class="plain" style="width: 75%" -->

NOTES:

- I'm a Principal Frontend Engineer at Stitch Fix
- Stitch Fix is an online personal styling service
  * Combines technology & data science
  * With an actual human stylist
  * Take the effort out of shopping by providing a selection of clothes picked just for you
  * And sent to your door on a frequency that you choose
- We're hiring!
  * Headquarters is in SF
  * But we have remote engineers all over the country

/////
<!-- .slide: data-background="url(../../img/giphy/james-harden-wesley-johnson-ankles.gif) no-repeat center" data-background-size="cover" -->

NOTES:
- Also a huge basketball / NBA fan
- Originally from Houston, so a huge Rockets fan

/////

# Minishops

NOTES:
- I do virtual workshops...
- I'm doing a giveaway...

=====

# Errors

NOTES:
- Most errors don’t occur when writing initially
  - But when making changes (refactoring)
  - Either 2 minutes later or 2 months later
  - That's when bugs get introduced
- Common errors / classes of bugs
  - `undefined` is not object
  - Variable `x` is not a function
  - Changing interfaces
    - Deprecated features
    - Changed types
- Gonna spend rest of our time showing TS features that can prevent this
- But I also hope to show you that you can prevent errors w/o too much TS
- There's lots TS can do but I want to focus on the React world

=====

# Anatomy of a function component

NOTES:
- A React component is just a function
- There's nothing _really_ special about it
- Takes props in and returns JSX
- Can be treated & typed like any other TS function
- Use an `interface` to define the props and is type of argument

=====

# Props

/////

# PropTypes vs. TypeScript

NOTES:
- You may be thinking React already has `PropTypes`
  - What's the difference
- `PropTypes` are runtime checks
  - So you either have to render the component locally
  - Or render it as part of a test
- Failed validation does not prevent the component from rendering
  - Errors will as a result, however
  - It's on the dev to notice and fix
- TypeScript is compile-time
  - The App won't even run if there are errors
  - It gets in your way, which will be really annoying at the start
  - We'll see lots of examples of that

/////

# 1. Props must be listed

NOTES:
- Can't be used w/in component w/o definition
- How many times have you had props in a component used w/o any definition?
- There are ESLint rules to catch this sort of thing, but they are limited

/////


NOTES:
- Can't be passed as props to component w/o definition

/////

# 2. Props are required by default

NOTES:
- See lots of examples where React PropTypes are defined
- But none of them are marked as required
- But if you look at the code, the props are _definitely_ required

/////


NOTES:
- Use `?` to denote a prop is optional

/////

NOTES:
- Default props uses object destructuring + defaulting

/////

# 3. Prop refactors are caught

NOTES:
- If you change the type of a value, all the places using it must be updated

/////

NOTES:
- If you change the name of a prop, all the places using it must be updated

/////

# 4. Can't avoid defining complex objects

NOTES:
- Without prop types, it's just this huge object w/ undocumented properties

/////

NOTES:
- Even with lint rules to enforce prop types
  - `PropTypes.object` or `PropTypes.shape({})
  - We're just lazy

/////

NOTES:
- TS is now getting in your way and preventing you from being lazy
  - But also saving you because you have to define _exactly_ what's available
- If object's properties change (in a shared place), compilation will break

/////

# 5. Function props have explicit signature

NOTES:
- With prop types it's just `PropTypes.func`

/////

NOTES:
- Now you have to define both the args as well as return value

/////

NOTES:
- How many times have you changed the args of a callback function
  - Forget to change one or two places?
- `PropTypes.func` wouldn't have caught it
  - Just a runtime error

/////

NOTES:
- By the way this is also really great for render props
  - Get to see everything that render prop is passing you

/////

# 6. Rest props are also typed

NOTES:
- Rest props are also typed

/////

NOTES:
- Can't pass extra props through w/ rest props either
- Types have to match as well

/////

# 7. Sharing props

NOTES:
- Can share props through extending interfaces
- Validation still works perfectly
- ESLint can't figure all of this out

/////

# 8. VS Code integration

https://twitter.com/erikras/status/1304479313274851328

NOTES:
- VS Code integration for Typescript is 🔥
- Shows errors inline without even having to save and load app
- I couldn't imagine writing TS w/o Code

////

NOTES:
- Provides auto-completion for prop names

/////

NOTES:
- Provide auto-completion for prop values (enums / booleans)

/////

NOTES:
- Even shows prop descriptions via jsDoc

/////

NOTES:
- Shows inline errors for everything, even regular JS

=====

# Hooks

NOTES:
- The biggest unique difference with TS + React is with props
  - Because that's the biggest unique aspect of React
  - And for React function components everything I described is standard for functions
- The rest of React is really just regular TS vs JS
- But let's talk about some hooks

/////

# `useState`

/////

NOTES:
- Infers the type from the initial value

/////

NOTES:
- However if the initial value is `null` you'll need to declare the type
- Similarly if the initial value is one type of a union of types

/////

# `useEffect`

/////

NOTES:
- Nothing really special since `useEffect` just takes in a function
- It does ensure that you only return `undefined` or a clean-up function

/////

# `useReducer`

/////

NOTES:
- Can use what's called a "discriminated union" to define reducer actions

/////

# Custom hooks

NOTES:
- In general custom hooks are just regular functions
  * So you would type them like any TS function

/////

NOTES:
- However it's common in hooks to return a tuple like `useState`
- In which case you'll want to use `as const`
- Otherwise type inference will incorrect guess the type

=====

# Advanced patterns

/////

# One w/ the other

Example calls

NOTES:
- Let's say you have `<Text>` component that allows you to truncate text with `truncate` prop
- It also has a `showExpand` to provide link to click to expand
- The `showExpand` prop doesn't make sense w/o `truncate` prop

/////

Sample interfaces

NOTES:
- This is what the props definition could look like

/////

# Wrapping HTML components

Example calls

NOTES:
- Let's say I've got my `<Button>` component that's a wrapper over HTML `<button>`
- It has some props to control the visual design, but I want to support `<button>` props
  * And have the all type checked
- Without TS we sort of implicitly do this spreading rest props on the `<button>`
- But there's no validation - I could pass anything
  * Relying on the runtime error from React to tell me that this prop is invalid on `<button>`

////

Sample interface

NOTES:
- This is what it'd look like

/////

# Parameterized props

Example call for render prop

NOTES:
- Let's say you have a `<List>` that has a render prop for each item
- `<List>` is generic so it doesn't know what sort of items it's getting
  * Doesn't care about the items themselves just displaying them (dividers, etc)
- My biggest beef with render props is that I literally have no idea what I'm getting

/////

Sample component def

NOTES:
- But a render prop is just a special function prop, which now can be typed
- And with the power of generics, it can be _generically_ typed

=====

# Setup

/////

CRA

NOTES:
- Easiest way of getting set up as always is with Create React App
- Use `--typescript` arg
- Adds a basic `tsconfig.json` for you
- There's also a way to add TS to an existing CRA app

/////

Non-CRA

NOTES:
- For non-CRA apps, it's pretty straightforward
- In the past, you had to ditch Babel and use TS for JS transpiling & type checking
- Now TS & Babel work together
  * Add `@babel/preset-typescript` to babel config
  * Handles understanding TS and transpiling to JS just like your other plugins
- Also need to add a `tsconfig.json`

/////

tsc for CI

NOTES:
- Generally for PRs I'm not building the app in CI
  * Make the checks as fast as possible
- Therefore, you _should_ add a type check step in addition to tests & lint
- Only using the TS compiler for type-checking, Babel handles transpiling
  * IMO Babel does a better job of transpiling
  * Its ecosystem around plugins is much more robust than what TS offers

/////

DefinitelyTyped

NOTES:
- `DefinitelyTyped` is an amazing repository of type definitions
  * Has all of your favorite packages
- In order for you to be able to accurately type your React code
  * Your dependencies need to be typed as well

## Do I have to switch over all at once?

NOTES:
- NO! Not at all
- I always advise against big rewrites
  * Again, the whole purpose is to deliver a better quality app for your users
  * You spending weeks/months rewritting is not helping them
- I suggest taking it component by component
  * With Babel JS can import TS no-problem
  * You'll want to try to avoid the reverse because then you're missing type info
- So I suggest starting with utilities/helpers first
  * Those with little to no dependencies
  * Then work your way outwards
  * The top-level App component would likely be last

=====

# Resources

- [React TypeScript Cheatsheet](https://react-typescript-cheatsheet.netlify.app/)
- [`@typescript-eslint/eslint-plugin`](https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin)

NOTES:
- Only talked about function components
- You can use TS w/ class components too although hooks w/ functions are the way to go
- These resources will help

=====

(medicine background)

# TypeScript is not a cure-all!

NOTES:
- I know I've been super excited about TS
  * But it's not a cure-all
- It's just a tool like anything else
  * Still need code review
  * Still need tests for run-time things
  * But hopefully you'll need less of both
- There's a **learning curve** for TS
  * That's the COST
  * At SFIX I gave a workshop on TypeScript + React
  * Then a team at ganged up on a single PR to get feet wet
- VALUE: need to keep a lot less in your head about how components & object data work
  * TS types now keep that info

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="/" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:
- That's it!
- Ask questions on Twitter (@benmvp)
- Thanks!
- Enjoy the rest of the conference
