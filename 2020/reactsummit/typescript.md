<!-- .slide: data-state="title-page" data-background="url(../../img/ts-react/typewriter-james-pond-Z0uzZSM5i4M-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 65%;" class="content-overlay">

  <h1>TypeScript + React = ❤️</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020) | [#ReactSummit](https://twitter.com/hashtag/ReactSummit)</p>

  <br />

  <p>October 16, 2020</p>


  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- Hello there!
- First off, Happy 5th Anniversary to React Summit!
- And welcome to "TypeScript + React = ❤️"
  * Kinda wish I had used 🔥 instead
  * Because that's how awesome I think the partnership is
- I wanna spend our time showing TS features
  * That can prevent bugs in our React apps
- So I'm assuming that you have developed in React before
  * But you know little to no TypeScript
  * Even if you know lots of TS you'll get tons out of this
  * But for those that don't know TS I will be explaining the concepts

- **Slides are available online**

**RESTART THE TIMER!!!!**

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
  * and is the type of the `props` argument
- You can name `AppProps` anything you like

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
- Similarly, you can't pass a prop if it hasn't been defined
- How many times have you seen a prop being passed to a component
  * And it's not in the `PropTypes`
  * And it doesn't _seem_ to be used in the code
  * But you're afraid to remove it because... you're just not sure
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
  * But if you look at the code, the props are _definitely_ required
  * They are bugs waiting to happen
- TypeScript interface properties are **required** by default
  * So without doing anything special you're guaranteed that the values will exist
  * Nice!
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

const App = ({ players, count = 2 }: AppProps) => {
  const topPlayers = players.slice(0, count)

  // render topPlayers in UI
}</code></pre>
    <div class="code-highlight" style="height: 70px; top: 284px;"></div>
    <div class="code-highlight" style="height: 70px; top: 459px;"></div>
  </div>
</div>


NOTES:
- You can use `?` to denote a prop is optional
  * Which means its value is `undefined` when not passed
- Now if I omit `count` when rendering `<App />`
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
- If you change the name of a prop, all the places using it must be updated
  * Let's say the prop was originally `names` and I changed it to `players`
  * You search & replace to fix all the places
  * But did you get them all? How can you be 100% sure?
  * Well TS will complain if you miss a spot
- A derivative of this is when you simply mistype a prop
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
  * There's nothing forcing the `PropTypes` to be 100%
- TS is now getting in your way and preventing you from being lazy
  * But also saving you because you have to define _exactly_ what's available
  * You can't access properties off the `user` prop unless you define what they are
  * So if we decide to rename `isPrimary` to `primary` in `Address`
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
- This one is probably my favorite
- With prop types it's just `PropTypes.func`
- There's nothing that tells the user of the component what parameters it'll pass when called
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
- Now with TS you have to define both the args as well as return value
- And once again, if we decide to add a 2nd param to `onChange`
  * Or change the types
  * TS will error unless we fix **all** the places
- How many times have you forgotten to change a function handler in some places?
  * And they are usually called as a result of user interaction
  * Meaning you're much less likely to hit the error while manually testing
  * You have to rely on great test coverage
  * And we all know how that goes...

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VI) One with the other</h2>

    <p>Valid configurations</p>
    <pre class="large"><code class="lang-html">&lt;Text&gt;not truncated&lt;Text&gt;
&lt;Text truncate&gt;truncated&lt;Text&gt;
&lt;Text truncate showExpand&gt;truncated w/ expand&lt;Text&gt;</code></pre>

    <p style="margin-top:50px">Invalid configurations</p>
    <pre class="large"><code class="lang-html">&lt;Text truncate={false} showExpand&gt;not truncated&lt;Text&gt;
&lt;Text showExpand&gt;only expand&lt;Text&gt;</code></pre>
    <pre class="large"><code class="lang-shell">Property 'truncate' is missing in type
'{ children: Element; showExpanded: true; }' but required in type
'{ truncate: true; showExpanded?: boolean | undefined; }'.</code></pre>
  </div>
</div>

NOTES:
- Sometimes you have a component with dependent props
- Let's say you have `<Text>` component that allows you to truncate text with a `truncate` prop
- It also has a `showExpand` prop to provide a link to click to expand the truncated text
- The `showExpand` prop doesn't make sense w/o the `truncate` prop
  * So you want to make that configuration an error right?
  * It's a much better developer experience for users of the `<Text>` component
- So how do we make this happen?

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VI) One with the other</h2>

    <pre class="large"><code class="lang-typescript">interface CommonProps {
  children: React.ReactNode,
  // other props...
}
type TruncateProps =
  | { truncate?: false, showExpanded: undefined }
  | { truncate: true, showExpanded?: boolean }
type Props = CommonProps & TruncateProps

const Text = (props: Props) => {
  // props.truncate = boolean | undefined
  // props.showExpanded = boolean | undefined
}</code></pre>
    <p><a href="https://www.typescriptlang.org/docs/handbook/unions-and-intersections.html#discriminating-unions" target="_blank">Discriminating Unions</a></p>
    <div class="code-highlight fragment current-visible" style="height: 239px; top: 173px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 182px; top: 403px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 455px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 514px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 573px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 125px; top: 743px;"></div>
  </div>
</div>

NOTES:
- There are a couple of ways you can set this up
  * This is my preferred approach
- **ONE:** First you define your `CommonProps`
  * This has all the props that will always exist
- **TWO:** Then `TruncateProps` type is what's called a "discriminating union"
- **THREE:** First is for when the `truncate` prop is `false` or `undefined` (i.e. unspecified)
  * In this case, you set `showExpanded` to be `undefined`
  * Translation: `showExpanded` cannot be set when `truncate` is `false` or `undefined`
- **FOUR:** Second is for when the `truncate` prop is specifically set to `true` and only `true`
  * And in this case `showExpanded` is an optional `boolean`
  * We're allowed to make this extra configuration
- **FIVE:** Then `Props` is the intersection or combination of `CommonProps` & `TruncateProps`
- **SIX:** And finally in the code both `truncate` & `showExpanded` are typed as optional booleans

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VII) Extending HTML components</h2>

    <pre class="large"><code class="lang-html">&lt;Button
  variant="primary"
  size="large"

  type="button"
  onClick={() => { /\* ... \*/ }}
  disabled
  id="main_btn"
&gt;
  Go
&lt;/Button&gt;</code></pre>
  </div>
</div>

NOTES:
- Let's look at another advanced pattern
- Let's say I've got my `<Button>` component that's a wrapper over HTML `<button>`
- It has some props to control the visual design (`variant` & `size`)
  * But I also want to support all of the `<button>` props
  * Like `type`, `onClick`, `disabled`, etc.
  * And of course have them all type checked
- We already do this sort of thing without TS
  * Pass along unknown props to the underlying `<button>` element
- But there's no validation in vanilla JS
  * So I could pass any prop
  * Relying on the runtime error from React to tell me whether or not this prop is invalid on `<button>`

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VII) Extending HTML components</h2>

    <pre class="large"><code class="lang-typescript">interface NewProps {
  variant: 'primary' | 'secondary'
  size: 'default' | 'small' | 'large'
}

type Props = NewProps
  & Omit&lt;React.ComponentProps&lt;"button"&gt;, keyof NewProps&gt;

const Button = ({ variant, size, ...buttonProps }: Props) => {
  // do stuff with variant & size
  return &lt;button {...buttonProps} /&gt;
}</code></pre>
    <p><a href="https://www.typescriptlang.org/docs/handbook/utility-types.html#omittype-keys" target="_blank">Utility types</a></p>
    <div class="code-highlight fragment current-visible" style="height: 239px; top: 173px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 125px; top: 455px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 514px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 125px; top: 455px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 743px;"></div>
  </div>
</div>

NOTES:
- Instead, this is what the TypeScript definitions could look like
  * Again, there are several ways to accomplish this
- **ONE:** You first define whatever are the new props as `NewProps`
  * In this case, `variant` & `size`
- **TWO:** Then we want to define `Props` as the intersection of `NewProps` & `<button>` element props
  * But there may be a chance that the `<button>` element already has `variant` or `size` props
  * In which case we want to override those props
  * We want all the `<button>` element props **except** the new ones we're defining
  * **THREE:** We use `keyof` to get all the prop names of `NewProps`
  * Remove or omit those props using the `Omit<>` utility generic
  * **FOUR:** Then we merge in our `NewProps`
  * If we don't `Omit<>` and have a name collision, weird things happen in TS
- **FIVE:** Then in the component code we can spread `buttonProps` like we always do
  * Except `buttonProps` is fully typed
  * So users of `<Button>` wouldn't be able to specify an `href` prop for instance
  * But we'll get auto-completion for `disabled`, `type`, and other props

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 100%">
    <h2>VIII) Parameterized props</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-html">&lt;List
  items={['ball', 'bat', 'hat']}
&gt;
  {(item) => (
    <div>
      {item.length}
    </div>
  )}
&lt;List&gt;</code></pre>
      </div>
      <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-html">&lt;List
  items={[23, 45, 62, 13]}
&gt;
  {(item) => (
    <div>
      {item.toFixed(2)}
    </div>
  )}
&lt;List&gt;</code></pre>
      </div>
    </div>
  </div>

  </div>
</div>

NOTES:
- Last TS feature I'm going to show you
- Let's say you have a `<List>` that has a render prop for each item
- But `<List>` is generic so it doesn't know what sort of items it's getting
  * Doesn't care about the items themselves just displaying them (dividers, etc)
  * The render prop does the work of rendering the UI of the items
- My biggest beef with render props is that I literally have no idea what data I'm getting
  * And in this case `<List>` needs to be able to handle different types
  * On the left we pass an array of `string`s and call `.length` on the data
  * On the right we pass an array of `number`s and call `.toFixed(2)` on the data
- We want to be able to know the type of the `item` param in the render prop
  * Based on the type of the `items` prop
  * You can imagine if `items` were arrays of objects how much more necessary this would be

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>VIII) Parameterized props</h2>

    <pre class="large"><code class="lang-typescript">interface Props&lt;T&gt; {
  items: T[]
  children: (item: T) => React.ReactNode
}
const List = &lt;T,&gt;({ items, children }: Props&lt;T&gt;) => (
  <ul className="list">
    {items.map((item) => (
      &lt;li key={item} className="item">
        {children(item)}
      &lt;/li>
    ))}
  </ul>
)</code></pre>
    <p><a href="https://ts.chibicode.com/generics" target="_blank"><em>TypeScript Generics for People Who Gave Up on Understanding Generics</em></a></p>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 403px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 239px; top: 173px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 230px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 286px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 403px; left: 420px; width: 146px"></div>
  </div>
</div>


NOTES:
- A render prop is just a special function prop
  * That happens to return React
  * But it can be typed just like any other prop function
- And with the power of **generics**, it can be _generically_ typed
  * **ONE:** The `List` component defines a generic parameter type `T`
  * **TWO:** It's passed to `Props<T>`
  * **THREE:** Which says that the `items` are an array of `T` types
  * **FOUR:** And the render prop is gonna be passed an item of type `T`
- Type inference also works with generics
  * Therefore when I render a `<List>` and pass strings, `T` is now a `string`
  * When I render a `<List>` and pass numbers, `T` is now a `number`
  * So `<List>` is generic, or parameterized as I call it
- **FIVE:** One thing I want to note is the `<T,>` bit
  * The comma is necessary when defining the component using arrow functions
  * Otherwise the parser can't tell if it's JSX or an arrow function

=====
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://react-typescript-cheatsheet.netlify.app/" target="_blank">React TypeScript Cheatsheet</li>
      <li><a href="https://www.youtube.com/watch?v=nePDL5lQSE4" target="_blank">What are TypeScript Generics?</a> ⏯️</li>
      <li><a href="https://www.typescriptlang.org/tsconfig" target="_blank"><code>tsconfig.json</code></a></li>
      <li><a href="https://www.typescriptlang.org/docs/handbook/babel-with-typescript.html" target="_blank">Using Babel with TypeScript</a></li>
      <li><a href="https://github.com/typescript-eslint/typescript-eslint/tree/master/packages/eslint-plugin" target="_blank"><code>@typescript-eslint/eslint-plugin</code></a></li>
      <li><a href="https://www.benmvp.com/blog/react-prop-types-with-typescript/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank"><em>React PropTypes with TypeScript</em></a></li>
      <li><a href="https://fettblog.eu/typescript-react/" target="_blank"><em>TypeScript and React</em></a></li>
      <li><a href="https://github.com/antonjb/TypeScript-Learning-Plan" target="_blank">TypeScript Learning Plan</a></li>
    </ul>
  </div>
</div>

NOTES:
- I included links to lots of resources throughout the slides
  * But I've got some additional ones here for you
- The most useful will likely be the first one
  * The **React TypeScript Cheatsheet**
  * Provides a lot of recipes for common situations
- Also, I only talked about function components
  * Like I mentioned, you can use TS w/ class components too but hooks w/ functions are the future
  * However if you need class examples, some of the resources have them

/////
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 100%">
    <div style="display:flex;flex-wrap:wrap;align-items:center;justify-content:space-around">
      <div style="flex: 0 0 60%;">
        <a href="https://www.benmvp.com/minishops/typescript-for-react-developers/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">
          <img src="../../img/ts-react/typescript-for-react-developers.png" alt="A Screenshot of the TypeScript for React Developers minishop page on benmvp.com" class="plain" style="width: 100%" />
        </a>
      </div>
      <div style="flex: 0 0 40%; text-align: left;">
       <ul>
        <li><a href="https://www.benmvp.com/minishops/typescript-for-react-developers/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">TypeScript for React Developers</a></li>
        <li><a href="https://www.benmvp.com/minishops/zero-to-react-with-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">Zero to React with Hooks</a></li>
        <li><a href="https://www.benmvp.com/minishops/migrating-to-react-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">Migrating to React Hooks</a></li>
        <li><a href="https://www.benmvp.com/minishops/sharing-react-component-logic/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">Sharing React Component Logic</a></li>
      </ul>
    </div>
  </div>
</div>

NOTES:
- I periodically host a series of short, 3-hour remote React workshops
  * I call them "minishops"
- One of them is called "TypeScript for React Developers"
  * So if you're interested in hands-on learning of using TS + React you should check it out
  * As well as the others listed
- I'm doing a free giveaway for conference attendees
  * Go to my site (benmvp.com) and check out the minishops page
  * Find **one** you like AND can attend
  * Send out a tweet w/ the link and tag me in
  * I'll pick one and give you a free ticket
  * Bonus points if you include a selfie of you watching this talk 😄

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=reactsummit-2020" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:
- So that's it!
- I know I just flooded you with a whole bunch of information
- Hopefully you found it all insightful
  * And it's motivated you to use TS in your next (or current) React project
- Again, the slides are already available online
- Ask questions on Twitter (@benmvp)
- Thanks!
- Hope you enjoy the rest conference!
