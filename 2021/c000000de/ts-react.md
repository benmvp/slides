<!-- .slide: data-state="title-page" data-background="url(../../img/ts-react/typewriter-james-pond-Z0uzZSM5i4M-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 65%;" class="content-overlay">

  <h1>TypeScript + React = ❤️</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=c000000de-2021) | [#c000000de](https://twitter.com/hashtag/c000000de)</p>

  <br />

  <p>February 27, 2021</p>


  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- Hello there!
- Excited and honored to be a part of the first c000000de conference
  * Shout-out to Henri for his hard work in putting this together
- And welcome to "TypeScript + React = ❤️"
  * Kinda wish I had used 🔥 instead
  * Because that's how awesome I think the partnership is
- I wanna spend our time showing off a couple of TS features
  * That can prevent bugs in our React apps
- So I'm assuming that you have developed in React before
  * But you know little to no TypeScript
  * Even if you know lots of TS you'll get tons out of this
  * But for those that don't know TS I will be explaining the concepts
- Normally at an in-person event I could see your faces
  * I'll be monitoring the chat as best I can as we go
  * So feel free to chime in as we go

- **Slides are available online**

**RESTART THE TIMER!!!!**

/////

<!-- .slide: data-background="url(../../img/giphy/stand-up-steph-curry.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But before we continue can I get everyone to stand up?

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
- We live in Pittsburg, CA (SF Bay Area)
- I'm a Principal Frontend Engineer at Stitch Fix
- Also a Google Developer Expert & Microsoft MVP in Web Technologies

=====
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>TypeScript React function component</h2>

    <pre class="large"><code class="lang-typescript">interface AppProps {
  // define props and types
}

const App = (props: AppProps) => {
  // use props and render UI
}</code></pre>

    <div class="code-highlight" style="height: 70px; top: 174px; left: 337px; width: 257px"></div>
    <div class="code-highlight" style="height: 70px; top: 400px; left: 579px; width: 301px"></div>
  </div>
</div>

NOTES:
- But enough about me
  * Let's dive into React + TS
- One thing I want to make clear as we begin...
- A React component is just a function
- There's nothing _really_ special about it
- Takes props in and returns JSX
- Can be treated & typed like any other TS function
- To start off, you use an `interface` to define the props
  * and it is the type of the `props` argument
- You can name `AppProps` anything you like
  * I usually go with just `Props` but used `AppProps` here for greater clarity

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
    <pre class="large"><code class="lang-shell">Property 'loading' does not exist on type 'AppProps'</code></pre>
    <div class="code-highlight" style="height: 70px; top: 459px;"></div>
  </div>
</div>

NOTES:
- Ok, so the first benefit...
- With TS, props **cannot** be used within a component without a definition
- How many times have you had props in a component used w/o any `PropTypes` definition?
  * In this case we're trying to use `props.loading` w/o defining in props
- There are ESLint rules to catch this sort of thing, but they are limited

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>I) Props must be listed</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App message="hi" count={5} /&gt;

</code></pre>
    <pre class="large"><code class="lang-shell">Property 'count' does not exist on type
'IntrinsicAttributes & AppProps'</code></pre>
  </div>
</div>


NOTES:
- Similarly, you can't pass a prop if it hasn't been defined either
- How many times have you seen a prop being passed to a component
  * And it's not in the `PropTypes`
  * And it doesn't _seem_ to be used in the code
  * But you're afraid to remove it because... you're just not sure
  * TypeScript gives us the confidence because it just wouldn't allow it
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
}</code></pre>

    <pre class="large"><code class="lang-typescript">&lt;App
  names={['Bron', 'Kawhi', 'KD', 'AD', 'Giannis']}
/&gt;</code></pre>
    <pre class="large"><code class="lang-shell">Property 'count' is missing in type '{ names: string[]; }'
but required in type 'AppProps'</code></pre>
  </div>
</div>

NOTES:
- React `PropTypes` are optional by default
- I see lots of examples where `PropTypes` are defined
  * But none of them are marked with `isRequired`
  * But if you look at the code and how they're used, the props are _definitely_ required
  * These are bugs waiting to happen
- TypeScript interface properties are **required** by default
  * So without doing anything special you're guaranteed that the values will exist
  * Nice!
- So if I call the component, leaving off a required prop (`count` in this case)
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

const App = ({ players, count = 2 }: AppProps) => {
  const topPlayers = players.slice(0, count)

  // render topPlayers in UI
}</code></pre>
    <div class="code-highlight" style="height: 70px; top: 284px;"></div>
    <div class="code-highlight" style="height: 70px; top: 459px;"></div>
  </div>
</div>


NOTES:
- However, we can use `?` to denote that a prop is optional
  * Which means its value is `undefined` when not passed
- Now, if I omit `count` when rendering `<App />`
  * There's no error and it'll default to `2`

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>III) Prop refactors are caught</h2>

    <pre class="large"><code class="lang-typescript">
&lt;App
  id="2"
  names={['Bron', 'Kawhi', 'KD', 'AD', 'Giannis']}
/&gt;

</code></pre>
    <pre class="large"><code class="lang-shell">Property 'names' does not exist on type
'IntrinsicAttributes & AppProps'.</code></pre>
    <div class="code-highlight" style="height: 70px; top: 343px;"></div>
  </div>
</div>


NOTES:
- If we change the name of a prop, all the places using it must be updated
  * Let's say the prop was originally `names` and I changed it to `players` w/in the component
  * We can search & replace to fix all the places
  * But did we get them all? How can we be 100% sure?
  * Well TS will complain if we miss a spot
- A derivative of this is when we simply mistype a prop
  * TS will complain immediately as well

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
- It's a lot of work to define a deeply nested shape
  * Even with eslint rules we find ways to "cheat"
  * There's nothing forcing the `PropTypes` to be 100% accurate
- TS is now getting in our way and preventing us from being lazy
  * But also saving us because we have to define _exactly_ what's available
  * We can't access properties off the `user` prop unless we define what they are
  * So if we decide to rename `isPrimary` in `Address` to just `primary`
  * We'll get TS errors in the `App` component
- So TS continues to be very beneficial in refactors

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>V) Function props have explicit signature</h2>

    <pre class="large"><code class="lang-typescript">const Input = ({ name, value, onChange }) => {
  // do input-y stuff & call onChange
}

Input.propTypes = {
  variant: PropTypes.enum(['filled', 'outlined']).isRequired,
  value: PropTypes.string.isRequired,
  onChange: PropTypes.func.isRequired,
}</code></pre>
    <div class="code-highlight" style="height: 70px; top: 571px;"></div>
  </div>
</div>


NOTES:
- Ok, this last one is probably my favorite
- With React prop types, all we get is `PropTypes.func` for functions
- There's nothing that tells the user of the component what parameters the function will pass when called
  * Or if it expects anything returned

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

const Input = ({ name, value, onChange }: Props) => {
  // do input-y stuff & call onChange
}</code></pre>
    <div class="code-highlight" style="height: 70px; top: 343px;"></div>
  </div>
</div>

NOTES:
- Now with TS we have to define both the arguments as well as return value
- And once again, if we decide to add a 2nd param to `onChange`
  * Or change the types
  * TS will error unless we fix **all** the places
- How many times have you forgotten to change a function handler in some places?
  * And they are usually called as a result of user interaction
  * Meaning we're much less likely to hit the error while manually testing
  * We have to rely on great test coverage
  * And we all know how that goes...

=====
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://www.benmvp.com/blog/react-prop-types-with-typescript/?utm_source=benmvp&utm_medium=slides&utm_campaign=c000000de-2021" target="_blank"><em>React PropTypes with TypeScript</em></a></li>
      <li><a href="https://react-typescript-cheatsheet.netlify.app/" target="_blank">React TypeScript Cheatsheet</li>
      <li><a href="https://www.typescriptlang.org/tsconfig" target="_blank"><code>tsconfig.json</code></a></li>
      <li><a href="https://www.typescriptlang.org/docs/handbook/babel-with-typescript.html" target="_blank">Using Babel with TypeScript</a></li>
      <li><a href="https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin" target="_blank"><code>@typescript-eslint/eslint-plugin</code></a></li>
      <li><a href="https://fettblog.eu/typescript-react/" target="_blank"><em>TypeScript and React</em></a></li>
      <li><a href="https://github.com/antonjb/TypeScript-Learning-Plan" target="_blank">TypeScript Learning Plan</a></li>
    </ul>
  </div>
</div>

NOTES:
- I've got some resources here for you
  * I wrote a blog post on mapping from React prop types to TypeScript types
  * The React/TypeScript cheatsheet will help with many common scenarios
- Also, I only talked about function components
  * You can use TS w/ class components too but hooks in functions are the future
  * However if you need class examples, some of the resources have them

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=c000000de-2021" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:
- And that's it!
- Hopefully you found this quick look at TypeScript in React insightful
  * And it's motivated you to use TS in your next (or current) React project
- Shoutout again to Henri for putting this all together
  * And for you all attending
  * It's my hope that you'll be inspired to speak and share your knowledge as well
- Again, the slides are already available online
- Ask questions on Twitter (@benmvp)
- Thanks!
- Hope you enjoy the rest conference!
