<!-- .slide: data-state="title-page" data-background="url(../../img/ts-react/typewriter-james-pond-Z0uzZSM5i4M-unsplash.jpg) no-repeat center" data-background-size="cover" -->

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
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 50%;" class="content-overlay">
    <a href="https://www.typescriptlang.org/" target="_blank"><img src="../../img/nav-react/typescript-logo.png" class="plain" /></a>
  </div>
</div>

NOTES:
- People ask “Why do I need to learn TypeScript when I already am productive with JavaScript”
- Especially since there'll be a learning curve
- I argue it’s a matter of perspective

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 50%;" class="content-overlay">
    <a href="https://jquery.com/" target="_blank"><img src="../../img/ts-react/jquery-logo-light.png" class="plain" /></a>
  </div>
</div>

NOTES:
- Why do people who are productive in making apps with jQuery decide to learn something like React?

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 50%;" class="content-overlay">
    <a href="https://reactjs.org/" target="_blank"><img src="../../img/react/react-logo.png" class="plain" /></a>
  </div>
</div>

NOTES:
- They’ll find themselves struggling to do things in React that they can already do easily w/ jQuery
- Manipulating the DOM, for instance
- They’ll be “fighting” React instead of actually building the app
- But once they pass the learning curve, they’ll be able to build bigger and more sophisticated apps AND less buggy apps because they’re not maintaining state in the DOM triggered by events
- It’s because they already knew how to web dev with jQuery
- If they learned web dev for the start with React that sense of “is this necessary” isn’t there

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 70%">
    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <a href="https://reactjs.org/" target="_blank"><img src="../../img/react/react-logo.png" class="plain" /></a>
      </div>
      <div style="flex:0 0 45%;">
        <a href="https://www.javascript.com/" target="_blank" style="display: block"><img src="../../img/nav-react/javascript-logo-flat.svg" class="plain" /></a>
      </div>
  </div>
</div>

NOTES:
- It’s the same for JavaScript + TypeScript
- Because you already know how to build React apps in JavaScript, jumping to TypeScript may not seem worth it
- But if you were learning JavaScript as TypeScript from the beginning your perspective would be different
- No different than learning JS from the beginning and have to learn random quirks

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 70%">
    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <a href="https://reactjs.org/" target="_blank"><img src="../../img/react/react-logo.png" class="plain" /></a>
      </div>
      <div style="flex:0 0 45%;">
        <a href="https://www.typescriptlang.org/" target="_blank"><img src="../../img/nav-react/typescript-logo.png" class="plain" /></a>
      </div>
  </div>
</div>

NOTES:
- Most talks on React + TypeScript just teach how to use TypeScript w/ React
- They are assuming you already wanna use TS and just wanna know how to

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
- Whenever we're talking about non-end-user features
  * We need to ask ourselves what exactly is the benefit?
  * Does this even matter?
- Because if it's **not** a feature for the end user
  * Then it **needs** to be a feature for the developer
  * So that _they_ can build faster/better for end user
- Otherwise, we find ourselves bike-shedding
- Kent C. Dodds wrote a blog post says exactly that
  * We need to measure success based on how well we can deliver what the user wants
  * Our choice of tooling should be based on that goal (and no more)

/////
<!-- .slide: data-background="url(../../img/perfect-lib/alessandra-caretto-cAY9X4rPG3g-bicycle-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 70%;" class="content-overlay">
    <img src="../../img/ts-react/dung-beetle-paulo-ziemer-oV3zTK7vuP0-unsplash.jpg" class="plain" />
  </div>
</div>

NOTES:
- Users definitely don’t want a buggy experience and of course, neither do we
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

![Screenshot of TypeScript for React Developers Minishop](../../img/ts-react/typescript-for-react-developers.png)
<!-- .element: class="plain" style="width: 75%" -->

- [TypeScript for React Developers](https://www.benmvp.com/minishops/typescript-for-react-developers/?utm_source=benmvp&utm_medium=slides&utm_campaign=tsconf-2020)
- [Zero to React with Hooks](https://www.benmvp.com/minishops/zero-to-react-with-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=tsconf-2020)
- [Migrating to React Hooks](https://www.benmvp.com/minishops/migrating-to-react-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=tsconf-2020)
- [Sharing React Component Logic](https://www.benmvp.com/minishops/sharing-react-component-logic/?utm_source=benmvp&utm_medium=slides&utm_campaign=tsconf-2020)

NOTES:
- I do virtual workshops...
- I'm doing a giveaway...

=====
<!-- .slide: data-background="url(../../img/ts-react/grass-field-ales-krivec-4miBe6zg5r0-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>TypeScript React function component</h2>

    <pre class="large"><code class="lang-typescript">interface AppProps {
  // define props and types
}

const App = (props: AppProps) => {
  // use props and render UI
}</code></pre>
  </div>
</div>

NOTES:
- One thing as we get started...
- A React component is just a function
- There's nothing _really_ special about it
- Takes props in and returns JSX
- Can be treated & typed like any other TS function
- Use an `interface` to define the props and is type of argument
- Can name `AppProps` anything you like
- _Can_ define class components in TS, but I'm only gonna show functions
- Hooks are the future, so we should be moving that way anyway

=====
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>1. Props</h1>
  </div>
</div>

NOTES:
- Let's talk all about how props typing works in TS

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 60%">
    <img src="../../img/ts-react/ts-compile-failure.png" alt="Screenshot of TypeScript compile failure" style="width: 100%" />
  </div>
</div>

NOTES:
- You may be thinking React already has `PropTypes`
  - What's the difference?
- `PropTypes` are runtime checks
  - So you either have to render the component locally
  - Or render it as part of a test
- Failed validation does not prevent the component from rendering
  - Component may have runtime errors as a result of failing prop types
  - But they may be in corner cases
  - It's on the dev to notice in console and care enough to fix
- TypeScript is compile-time
  - The App won't even run if there are errors
  - It gets in your way, which will be really annoying at the start
  - We'll see lots of examples of that

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>I) Props must be listed</h2>

    <pre class="large"><code class="lang-typescript">interface AppProps {
  message: string
}

const App = (props: AppProps) => {
  if (props.loading) {
    return <span>Loading...</span>
  }

  return <div>{props.message}</div>
}</code></pre>
    <pre class="large"><code class="lang-text">Property 'loading' does not exist on type 'Props'</code></pre>
  </div>
</div>

NOTES:
- Props cannot be used within component without definition
- How many times have you had props in a component used w/o any definition?
- There are ESLint rules to catch this sort of thing, but they are limited

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>I) Props must be listed</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App message="hi" count={5} /&gt;

</code></pre>
    <pre class="large"><code class="lang-text">Property 'count' does not exist on type
'IntrinsicAttributes & AppProps'</code></pre>
  </div>
</div>


NOTES:
- Similarly, you can't pass a prop if it hasn't been defined
- How many times have you seen a prop being passed to a component
  * It's not in the `PropTypes` either
  * But you're afraid to remove it because... you're just not show
  * TypeScript gives you the confidence because it wouldn't allow it
- The error message can seem a bit cryptic to be honest
  * But as you encounter them more often you'll get used to them

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>II) Props are required by default</h2>

    <pre class="large"><code class="lang-typescript">interface AppProps {
  players: string[]
  count: number
}

const App = (props: AppProps) => {
  const topPlayers = props.players.slice(0, props.count)

  // render topPlayers
}</code></pre>
  </div>
</div>

NOTES:
- React `PropTypes` are optional by default
- See lots of examples where `PropTypes` are defined
  * But none of them are marked with `isRequired`
  * But if you look at the code, the props are _definitely_ required
  * A bug waiting to happen
- TypeScript interfaces are **required** by default
  * So without doing anything special you're guaranteed that the values will exist

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>II) Props are required by default</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App
  names={['Bron', 'Kawhi', 'KD', 'Giannis', 'AD']}
/&gt;

</code></pre>
    <pre class="large"><code class="lang-text">Property 'count' is missing in type '{ names: string[]; }'
but required in type 'AppProps'</code></pre>
  </div>
</div>

NOTES:
- So If I call the component, leaving off a required prop (`count` here)
- It will yell at me, and again not compile

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>II) Props are required by default</h2>

    <pre class="large"><code class="lang-typescript">interface AppProps {
  players: string[]
  count?: number
}

const App = ({players, count = 2}: AppProps) => {
  const topPlayers = players.slice(0, count)

  // render topPlayers
}</code></pre>
  </div>
</div>


NOTES:
- Use `?` to denote a prop is optional
- Which means of course its value is `undefined` when not passed
- Default props uses object destructuring + defaulting
- This replaces `defaultProps`
- Now if I omit `count` there's no error and it'll default to `2`
- This is typically how TS React function components look

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>III) Prop refactors are caught</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App
  id={2}
  players={['Bron', 'Kawhi', 'KD', 'Giannis', 'AD']}
/&gt;

</code></pre>
    <pre class="large"><code class="lang-text">Type 'number' is not assignable to type 'string'.</code></pre>
  </div>
</div>

NOTES:
- How about those times where you've changed the type of a prop
  * Like `id` going from a `number` to a `string`
  * And now you have to search & replace to fix all the places
  * But did you get them all? How can you be 100% sure?
- In TS all the places using it **must** be updated

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>III) Prop refactors are caught</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App
  id="2"
  names={['Bron', 'Kawhi', 'KD', 'Giannis', 'AD']}
/&gt;

</code></pre>
    <pre class="large"><code class="lang-text">Property 'names' does not exist on type
'IntrinsicAttributes & AppProps'.</code></pre>
  </div>
</div>


NOTES:
- If you change the name of a prop, all the places using it must be updated
  * Let's say the prop was originally `names` and I changed it to `players`
  * But I forgot to change a place
  * TS will complain
- A derivative of this is when you mistype a prop
  * TS will complain immediately as well

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>IV) Can't avoid defining complex objects</h2>

    <pre class="large"><code class="lang-typescript">const App = ({user}) => {
  const { city, isPrimary } = user.addresses.shipping

  // render using city and isPrimary
}</code></pre>
  </div>
</div>

NOTES:
- Typically if we're getting data from an API, its deeply nested data
- Without prop types, it's just this huge object w/ undocumented properties

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>IV) Can't avoid defining complex objects</h2>

    <pre class="large"><code class="lang-typescript">const App = ({user}) => {
  const { city, isPrimary } = user.addresses.shipping

  // render using city and isPrimary
}
App.propTypes = {
  user: PropTypes.shape({}).isRequired
}</code></pre>
  </div>
</div>


NOTES:
- We try to put in lint rules to force definitions
  * But we'll `PropTypes.object` or `PropTypes.shape({})
  * It's a lot of work to define a deeply nested shape
  * And then it gets out of date as new stuff gets added
  * There's no enforcement, eslint can only do so much

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>IV) Can't avoid defining complex objects</h2>

    <pre class="large"><code class="lang-typescript">interface Address { /\* city, isPrimary, etc \*/ }

interface User {
  name: string
  addresses: {
    shipping: Address
    billing?: Address
  }
}

interface AppProps {
  user: User
}</code></pre>
  </div>
</div>


NOTES:
- TS is now getting in your way and preventing you from being lazy
  * But also saving you because you have to define _exactly_ what's available
  * You can't access properties off the `user` prop unless you define what they are
- The `Address` interface may be a type defined in a shared place
  * So if we decide to rename `isPrimary` to `primary` in `Address`
  * We'll get TS errors in the `App` component
- TS is resilient to refactors

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>V) Function props have explicit signature</h2>

    <pre class="large"><code class="lang-typescript">const Input = ({name, value, onChange}) => {
  // do input-y stuff & call onChange
}

Input.propTypes = {
  variant: PropTypes.enum(['filled', 'outlined']).isRequired,
  value: PropTypes.string.isRequired,
  onChange: PropTypes.func.isRequired,
}</code></pre>
  </div>
</div>


NOTES:
- May be my favorite
- With prop types it's just `PropTypes.func`
- There's nothing that tells the user of the component what parameters it'll pass
  * And if it expects anything returned

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>V) Function props have explicit signature</h2>

    <pre class="large"><code class="lang-typescript">interface Props {
  variant: 'filled' | 'outlined'
  value: string
  onChange: (newValue: string) => void
}

const Input = ({name, value, onChange}: Props) => {
  // do input-y stuff & call onChange
}</code></pre>
  </div>
</div>

NOTES:
- Now you have to define both the args as well as return value
  * Typically callback functions don't have return values (`void`)
  * But in certain cases, you may
- And once again, if we decide to add a 2nd param to `onChange`
  * Or change types
  * TS will error unless we fix **all** the places
  * How many times have you forgotten to change it in some places
  * And since it's a callback it probably requires some user interaction
  * Meaning you're much less likely to hit the error while manually testing
  * Have to rely on great test coverage

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>V) Function props have explicit signature</h2>

    <pre class="large"><code class="lang-typescript">interface Props {
  users: User[]
  children: (user: User) => React.ReactNode
}

const UsersList = ({users, children}: Props) => (
  <aside>
    {users.map(user => (
      <div>{children(user)}</div>
    ))}
  </aside>
)</code></pre>
  </div>
</div>


NOTES:
- By the way this is also really great for render props
  * Get to see everything that render prop is passing you
  * `children` takes a `user` object and returns back React UI
  * The use of `<UsersList />` will be fully type-safe as well

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VI) Rest props are also typed</h2>

    <pre class="large"><code class="lang-typescript">interface Props {
  type?: 'button' | 'submit'
  disabled?: boolean
  onClick: () => void
  children: React.ReactNode
}

const Button = ({type = 'button', ...buttonProps}: Props) => {
  // buttonProps has \*only\* disabled/onClick/children

  return &lt;button type={type} {...buttonProps} /&gt;
}</code></pre>
  </div>
</div>

NOTES:
- Rest props are also typed
- We typically use rest props as a kitchen sink hole for pass-thru props
- But since we're defining the full interface
  * Only those props not mentioned are included
- As long as the types match w/ the underlying element/component
  * We can spread those props onward

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VI) Rest props are also typed</h2>

    <pre class="large"><code class="lang-typescript">
&lt;Button
  disabled={true}
  onClick={() => console.log('clicked')}
  title="Extra description"
&gt;
  Label
&lt;/Button&gt;

</code></pre>
    <pre class="large"><code class="lang-text">Property 'title' does not exist on type
'IntrinsicAttributes & Props'.</code></pre>
  </div>


NOTES:
- But we still can't pass extra props through, even with rest
  * We know that `<button>` accepts `title`
  * But the `Button` component has to define it
- Will talk about a way around this later in advanced patterns

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 50%">
    <h2>VII) VS Code integration 🔥</h2>

    <a href="https://twitter.com/erikras/status/1304479313274851328" target="_blank"><img src="../../img/ts-react/code-typescript-tweet-erikras.png" alt="Screenshot of Tweet from @erikras about TS + Code" style="width: 90%" /></a>

    <a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code</a>
  </div>
</div>


NOTES:
- The Visual Studio Code integration for Typescript is 🔥
  * VS Code is a free, open-source code editor that runs on all platforms
- Auto-completes as you type
  * They call it "IntelliSense"
- Shows errors inline without even having to leave the editor
  * Shortens the feedback loop
- I couldn't imagine writing TS without VS Code

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 50%">
    <h2>VII) VS Code integration 🔥</h2>

    <a href="https://twitter.com/erikras/status/1304479313274851328" target="_blank"><img src="../../img/ts-react/vscode-prop-name-auto-completion.png" alt="Prop name auto-completion in VS Code" style="width: 100%" /></a>
  </div>
</div>


NOTES:
- Provides auto-completion for prop names
- Notice `key` there at the bottom
  * The `key` prop is always a valid prop to be passed to components/elements
  * So it shows up even though the component itself doesn't define it

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 50%">
    <h2>VII) VS Code integration 🔥</h2>

    <a href="https://twitter.com/erikras/status/1304479313274851328" target="_blank"><img src="../../img/ts-react/vscode-prop-value-auto-completion.png" alt="Prop value auto-completion in VS Code" style="width: 100%" /></a>
  </div>
</div>


NOTES:
- Provide auto-completion for prop values (enums / booleans)
- In this case the `status` prop is an enum / union of `failed` & `success`

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 50%">
    <h2>VII) VS Code integration 🔥</h2>

    <a href="https://twitter.com/erikras/status/1304479313274851328" target="_blank"><img src="../../img/ts-react/vscode-property-value-auto-completion.png" alt="Object property value auto-completion in VS Code" style="width: 100%" /></a>
  </div>
</div>


NOTES:
- Provides auto-completion for object property values
- So if you have a deeply-nested prop, you can easy see what's inside
  * As you type!

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 90%">
    <h2>VII) VS Code integration 🔥</h2>

    <a href="https://twitter.com/erikras/status/1304479313274851328" target="_blank"><img src="../../img/ts-react/vscode-inline-error-reporting.png" alt="Inline error reporting in VS Code" style="width: 100%" /></a>
  </div>
</div>


NOTES:
- Shows inline errors for everything
  * I usually catch type errors before I even go over to the app
- I can't really do the developer experience justice with screenshots
  * You'll have to grab VS Code and start coding to see
  * I've converted over many vim users who wanna use TS over to VS Code

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

/////

https://twitter.com/benmvp/status/841412246957785088?s=19

NOTES:
- Heads up!
- You may find yourself _fighting_ TypeScript
  * You're trying to type check some JavaScript, but it just isn't working
  * You "know" it works, but TS is complaining
  * This is definitely going to happen
  * Remember with TS you're signing up for it to make your code strict
- But I want you to keep this thought from Jared in mind
  * Maybe if it's really hard to type check, the code itself is hard to understand


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
