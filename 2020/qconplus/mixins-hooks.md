<!-- .slide: data-state="title-page" data-background="url(../../img/mixins-hooks/road-nighttime-ricardo-rocha-nj1bqRzClq8-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 80%;" class="content-overlay">

  <h1>From Mixins to Custom Hooks</h1>
  <h3>History of sharing in React</h3>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020) | [#QConPlus](https://twitter.com/hashtag/QConPlus)</p>

  <br />

  <p>November 5, 2020</p>


  </div>
</div>

NOTES:
- Hello, hello everyone!
- **RESTART THE TIMER!!!!**
-
- **Slides are available online**
- **RESTART THE TIMER!!!!**

=====
<!-- .slide: data-background="url(../../img/ts-react/electric-cables-john-barkiple-l090uFWoPaI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 60%;" class="content-overlay">
    <a href="https://reactjs.org/" target="_blank"><img src="../../img/react/react-logo.svg" class="plain" /></a>
  </div>
</div>

NOTES:
- React's approach to building UIs makes sharing & reuse great!

/////
<!-- .slide: data-background="url(../../img/ts-react/electric-cables-john-barkiple-l090uFWoPaI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 100%">
    <h2>Sharing Components</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-javascript">const Players = ({ teamId }) => {
  // retrieve playerImages
  return (
    &lt;section>
      &lt;h1>All Players&lt;/h1>
      &lt;Slideshow
        images={playerImages}
        page={2}
        onNext={ ... }
      />
    &lt;/section>
  )
}</code></pre>
      </div>
      <div style="flex:0 0 45%; margin-left: 20px;">
        <pre class="large"><code class="lang-javascript">const Teams = () => {
  // retrieve teamLogos
  return (
    &lt;section>
      &lt;h1>All Teams&lt;/h1>
      &lt;Slideshow
        images={teamLogos}
        page={5}
        onNext={ ... }
      />
    &lt;/section>
  )
}</code></pre>
      </div>
    </div>
  </div>

  </div>
</div>

NOTES:
- React is especially great at sharing UI
- Here we have a `<Slideshow>` component
  * No doubt has lots of markup, styling & UI logic
- Using it in two components
  * `Players` component to have a slideshow of team players
  * `Teams` component to have a slideshow of team logos
- And we can configure them differently w/ props
  * Passing different values for the props

/////
<!-- .slide: data-background="url(../../img/ts-react/electric-cables-john-barkiple-l090uFWoPaI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Sharing Utilities</h2>

    <pre class="large"><code class="lang-javascript">const fetchImages = (teamId, page) => {
  const apiUrl = teamId ? '...' : '...'

  return fetch(apiUrl)
    .then((resp) => resp.json())
    .then((data) => data.images)
}</code></pre>
  </div>
</div>


NOTES:
- And because React is basically Just JavaScript™
  * Sharing helper functions is great too
  * Can call API utilities, data transformation helpers, etc

/////
<!-- .slide: data-background="url(../../img/ts-react/electric-cables-john-barkiple-l090uFWoPaI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Sharing Non-Visual Logic?</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-javascript">const Players = ({ teamId }) => {
  // retrieve playerImages
  return (
    &lt;section>
      &lt;h1>All Players&lt;/h1>
      &lt;Slideshow
        images={playerImages}
        page={2}
        onNext={ ... }
      />
    &lt;/section>
  )
}</code></pre>
      </div>
      <div style="flex:0 0 45%; margin-left: 20px;">
        <pre class="large"><code class="lang-javascript">const Teams = () => {
  // retrieve teamLogos
  return (
    &lt;section>
      &lt;h1>All Teams&lt;/h1>
      &lt;ImageList
        items={teamLogos}
        page={5}
        onPage={ ... }
      />
    &lt;/section>
  )
}</code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- But the tricky part is the non-visual logic
- I've got a `Players` component & a `Teams` component
  * They are going to render different UI, a `<SlideShow />` & an `<ImageList />`
  * But they both are gonna call the same API
  * They both need to maintain state of images/logos
  * And both of them need to act on when the page changes
- So they have similar state + logic but different UI
- Therefore we want to be able to re-use the code around...
  * Maintaining the current page
  * Calling the API when the current page changes
  * Getting the images from response
  * Maintaining the list of those images
- That way I could render the paginated player images or team logos as...
  * A slideshow
  * A list view
  * A grid view
  * Whatever
  * But not have to repeat the non-visual logic
- So I wanna take us on a journey of how we've tried to solve this problem
  * This problem of sharing non-visual logic

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
- I'm a Principal Frontend Engineer at Stitch Fix
- Also a Google Developer Expert & Microsoft MVP in Web Technologies

/////

![Stitch Fix Corporate logo (dark)](../../img/stitchfix/lockup-solid-vert-gender-neutral-dark.svg)
<!-- .element: class="plain" style="width: 75%" -->

NOTES:

- I'm a Principal Frontend Engineer at Stitch Fix
- Stitch Fix is an online personal styling service
  * Combines technology & data science
  * With an actual human stylist
  * Take the effort out of shdddddddddopping by providing a selection of clothes picked just for you
  * And sent to your door on a frequency that you choose
- We're hiring!
  * Headquarters is in SF
  * But we have remote engineers all over the country

=====

<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Mixins</h1>
    <h2>(React &lt;= 0.14)</h2>
  </div>
</div>

NOTES:
- Alright enough about me. Let's just right in
- The first approach to solve this was via mixins
- This pre-dates me because it basically ended with React 15 & classes
- But I did see lots of 0.14 code using mixins

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const Players = React.createClass({
  mixins: [ImagesMixin],
  render() {
    return (
      &lt;section>
        &lt;Slideshow
          images={this.state.images}
          page={this.state.curPage}
          onNext={this.handleNextPage}
        />
      &lt;/section>
    )
  },
})</code></pre>
  </div>
</div>

NOTES:
- We used `React.createClass` to create a component
- And it took an optional `mixins` property to define 1 or more mixins
  - We're using an `ImagesMixin` which I'll show
- In this case `ImagesMixin` defines `images` & `curPage` state variables
  * They are passed to the `<SlideShow />`
- And finally `this.handleNextPage` is called when slideshow changes
  * This is also defined in the mixin
- As you can see there's some magic happening
  * The state is magically available
  * I have to know that `handleNextPage` is provided

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const ImagesMixin = {
  getInitialState() { return { images: [], curPage: 1 } },
  componentDidMount() { this.updateImages() }
  componentDidUpdate(prevProps, prevState) {
    if (prevState.curPage !== this.state.curPage
      || prevProps.teamId !== this.props.teamId) {
      this.updateImages()
    }
  },
  updateImages() {
    fetchImages(this.props.teamId, this.state.curPage)
      .then((images) => { this.setState({ images }) })
  }
  handleNextPage(curPage) { this.setState({ curPage }) },
}</code></pre>
  </div>
</div>

NOTES:
- And here's the implementation of `ImagesMixin`
  * Kinda verbose compared to the custom hook
  * But let's walk through it
- Here's where the `images` & `curPage` state are defined
- In `componentDidMount` we call `updateImages` to retrieve the images initially
- In `componentDidUpdate` we call `updateImages`
  * Either when `curPage` state or `teamId` prop change
- `updateImages` is where we make the actual `fetchImages` call
  * And set `images` state w/ returned data
- And finally we provide the `handleNextPage` helper **for the components**
  * To update the current page
  * It's not actually called from w/in the mixin
- This is probably not exactly how I would've written it back then
  - I'm applying new JavaScript syntax & React coding style to old patterns 😂

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <h2>Gotchas with Mixins</h2>

    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-javascript">React.createClass({
  mixins: [
    I18nMixin,
    AuthMixin,
    ThemeMixin,
  ],
  render() {
    // use this.state
    // call helpers
    // render UI
  },
})</code></pre>
      </div>
      <div style="flex:0 0 45%;">
        <ul>
          <li>No ES class support</li>
          <li>Lots of indirection</li>
          <li>Naming collisions</li>
        </ul>
      </div>
  </div>
</div>

NOTES:
- Mixins worked okay, but there were several gotchas with them
- Classes were being introduced to JavaScript
  * They didn't support mixins
  * React team wanted to move to using ES classes instead of maintaining own class system
- Mixins inherently relied on indirection & agreements to work
  * Mixin might need the component to define a helper method/property
  * Or the mixin provides a helper method/property for the component
  * When there were multiple mixins it was hard to know where state came from
  * React was able to merge the lifecycle methods
  * But if a specific sequence was important, it was challenging
- Also there could be helper method name collisions
  * Would have to namespace to ensure they were unique
- React would warn if two mixins had a `getInitialState` w/ the same keys
  * But it was still possible to have cases where two mixins were clobbering state


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Higher-order components (HOCs)</h1>
    <h2>(React 15)</h2>
  </div>
</div>

NOTES:
- So because of all of those issues
  * React 15 migrated to ES classes & ditched mixins support
- Technically you could still do mixins in React 15
  * Because `createClass` still existed in React 15
  * But there was even an official blog post _Mixins Considered Harmful_
  * And then it was deprecated in React `15.5.0`
  * And moved to its own package `create-react-class`
  * It was completely removed in React 16
- So w/o mixins we needed a new strategy for solving this problem
  * Sharing non-visual logic
- The next pattern that became popular was higher-order components (HOCs)
  * They had existed way back in React 0.13
  * But they surged in popularity with mixins gone

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const withImages = (Component) => {
  return class Images extends React.Component {
    state = { images: [], curPage: 1 }
    // lifecycle methods + updateImages
    render() {
      return &lt;Component
        {...this.props}
        images={this.state.images}
        curPage={this.state.curPage}
        handleNextPage={ ... }
      /&gt;
    }
  }
}</code></pre>
  </div>
</div>

NOTES:
- An HOC was/is a function that takes an existing component
  * And returns another component that wraps the original
  * It was popularized by Dan Abramov
  * Before he even started working at Facebook yet
- So `withImages` is the HOC & it takes the `Component` as a parameter
  * And it returns a new class component called `Images`
  * It's a wrapper class
- `Images` has all the same `state` & lifecycle methods as the mixins approach
  * Except they are methods on the wrapper `Images` class
- The big difference is that the HOC **renders** the component passed in
  * It passes along all the existing `props`
  * But then adds to the props the state properties
  * As well as the `handleNextPage` callback function prop for updating the `curPage` state
- I used to call HOCs "component enhancers"
  * Because they enhance the wrapped component by providing additional props
- Prefixing the HOC with `with` was a common convention

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const Players = (props) => (
  &lt;section>
    &lt;Slideshow
      images={props.images}
      page={props.curPage}
      onNext={props.handleNextPage}
    />
  &lt;/section>
)
export default withImages(Players)</code></pre>
  </div>
</div>

NOTES:
- The HOC is used similar to the mixin
  * Except the component is receiving props instead of state
  * This approach is **composition** over mixing in
- The exported component is the actual component that'll be used in UIs
- But by wrapping `Players` with `withImages` it'll do the work to maintain the state
  * And update as we paginate with the `handleNextProp`
  * Since `Players` is never exported, we can write to expect props `withImages` will give

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 65%">
    <h2>Gotchas with HOCs</h2>

    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-javascript">class Example {
  render() {
    // use this.props
    // render UI
  }
}
withI18n(
  withAuth(
    withTheme(Example)
  )
)</code></pre>
      </div>
      <div style="flex:0 0 45%;">
        <ul>
          <li>Indirection</li>
          <li>Naming collisions</li>
          <li>Static composition</li>
        </ul>
      </div>
  </div>
</div>

NOTES:
- So while HOCs did play nicely with ES classes there were still similar problems from mixins
- Indirection was still a problem
  * With mixins we didn't know which mixin state was coming from
  * There was also communication between helper methods/properties
  * Now with HOCs the only communication is through props
  * But with multiple HOCs we now don't know where our props are coming from
  * Makes debugging...fun
- There are no method or state name collisions with HOCs
  * But there can be prop name collisions if 2 HOCs try to set the same prop
  * And there'll be nothing that will tell us this is happening either
- Lastly the composition that happens w/ HOC is **static**
  * Meaning it happens outside of the `render()`
  * So it cannot be configured based upon the component's props and/or state
  * When we render child components, that's **dynamic** composition
  * In fact, doing the enhancement within `render()` would be terrible for performance
  * Would be creating a new component class with each render!
  * This actually was the case with mixins as well passing in that array
  * This wasn't always a problem, but made complex situations challenging


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Render props</h1>
    <h2>(React &lt; 16.8)</h2>
  </div>
</div>

NOTES:
- Render props have always existed in React
  * And they still do now
  * But they became popular as an alternative to HOCs right around when React 16 was released

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->
<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">class Images extends React.Component {
  state = { images: [], curPage: 1 }

  // lifecycle methods + updateImages

  render() {
    return this.props.render({
      images: this.state.images,
      curPage: this.state.curPage,
      handleNextPage: (curPage) => {
        this.setState({ curPage })
      }
    })
  }
}</code></pre>
  </div>
</div>

NOTES:
- A render prop is a special prop of a component
  * It's a function
  * But instead of being your typical callback handler
  * It's a function that takes in data and returns JSX
- It was popularized by Michael Jackson from React Training
  * As a completely better alternative to HOCs
  * He even wrote the Render Props React docs if you've ever written those
- So instead of a special mixin or a function
  * We have a normal component
  * Calling it `Images` here
- It has all the same `state` & lifecycle methods as the HOC & mixins approaches
  * So on `componentDidMount` it'll make the `fetchImages` call
  * And update the `images` state
- The component also has a function prop called `render`
  * It can actually be called anything, but `render` is a common convention
  * Hence "render prop"
  * It's also common to use the `children` prop too
- So within the `render()` method we call the `render` prop
  * And we pass it all the data the consumer of `<Images />` will need
  * The `images` & `curPage` state properties
  * As well as the `handleNextPage` callback for updating the `curPage` state

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->
<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const Players = ({ teamId }) => (
  &lt;section>
    &lt;Images
      teamId={teamId}
      render={(data) => (
        &lt;Slideshow
          images={data.images}
          page={data.curPage}
          onNext={data.handleNextPage}
        />
      )}
    />
  &lt;/section>
)</code></pre>
  </div>
</div>

NOTES:
- The use feels like normal React
- The `<Images />` component basically exposes its state to `Players`
  * By calling the `render` prop function passed to it
- `Players` now can render whatever UI it likes
  * Based on the `data` it receives in the `render` prop!
  * And here, just like the other examples, it's rendering the `<SlideShow />`
  * And any other UI that relies on the `data` would go w/in `<Images />` as well
- And `<Images />` is just like any other component so I could conditionally render it
  * Based on props/state of `Players`
  * Because the composition is **dynamic**
  * So if I don't render `<Images />`, I never make the `fetchImages` request
  * There was no such option for HOCs nor mixins

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->
<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const withImages = (Component) => {
  return class WithImages extends React.Component {
    render() {
      return &lt;Images render={(data) => (
        &lt;Component
          {...this.props}
          images={data.images}
          curPage={data.curPage}
          handleNextPage={data.handleNextPage}
        />
      )} />
    }
  }
}</code></pre>
  </div>
</div>

NOTES:
- Render props can basically be a complete replacement of HOCs
- They do everything HOCs can do + more
- In fact, we can re-implement our `withImages` using our render prop!
- It renders the `<Images />` component
- Passes a function prop to the `render` prop
- And then passes all the data along to the passed-in `Component`

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay" style="width: 65%">
    <h2>Gotchas with Render props</h2>

    <div style="display:flex;align-items:center;justify-content:space-around;">
	    <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-javascript">&lt;I18n>
  {(translations) => (
    &lt;Auth>
      {(authData) => (
        &lt;Theme>
          {(theme) => (
            ...
          )}
        &lt;/Theme>
      )}
    &lt;/Auth>
  )}
&lt;/I18n></code></pre>
      </div>
      <div style="flex:0 0 45%;">
        <ul>
          <li><code>PropTypes.func</code></li>
          <li>Crazy nesting</li>
        </ul>
      </div>
  </div>
</div>

NOTES:
- The render prop pattern is a pretty great pattern
  * Because it piggybacks on regular ol' React
  * New React 16 APIs started adopting it (React 16 Context for instance)
- However, there are still a couple of gotchas
- React `PropTypes` only have `PropTypes.func`
  * There's no public definition of what parameters the function will pass
  * Is `theme` and object or a single value?
  * What properties are in `authData`?
  * What's the shape of `translations`?
  * It can be trick to know without something like TypeScript
- Also as we can see here... when there are multiple render props
  * Things can get a bit crazy
  * With render props the entire UI is nested w/in the function prop
  * So here we're 6 levels indented before we even begin the real UI
- The nice thing though is that the order in which the nesting needs to be is clearer
  * So if the `<Theme>` component somehow needed data from the `<Auth>` component
  * We'd manually pass it as a prop to `<Theme>`
  * With HOCs that would all handle behind the scenes
  * And it wouldn't be clear which order the enhancers needed to be in
- But overall render props worked well for sharing non-visual logic

=====
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Custom hooks</h1>
    <h2>(React &gt;= 16.8)
  </div>
</div>

NOTES:
- We talked about mixins, then HOCs, and just now render props
- Then with React 16.8 came custom hooks (dun! dun! dun!!! 😂)
- When mixins went away with React 15 & ES classes
  * We started molding React into patterns to try to solve our problem
  * Our problem of sharing non-visual logic
- Hooks, particularly custom hooks, are now the modern solution to the problem

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const useImages = (teamId) => {
  const [images, setImages] = useState([])
  const [curPage, setCurPage] = useState(1)

  useEffect(() => {
    fetchImages(teamId, curPage)
      .then((newImages) => {
        setImages(newImages)
      })
  }, [teamId, curPage])

  return { images, curPage, setCurPage }
}</code></pre>
  </div>
</div>

NOTES:
- Here's the custom hook that we saw from the very beginning
- Custom hooks are **functions** that have to start with `use`
  * So we're calling it `useImages`
  * Went from `ImagesMixins` to `withImages` HOC to `Images` render prop component
  * Now to `useImages` custom hook
- It maintains state for `images` & `curPage` just like the others
  * Now using the `useState` hook
- It fetches new images whenever the current page changes as well
  * Now using the `useEffect` hook which is a bit simpler
- Finally we're returning the data the consuming component needs
  * `images`, `curPage` & `setCurPage` (the function that updates the `curPage`)
- All the same things as before, but much clearer & more concise IMO
  * Actually able to fit it all on one screen!
  * Remember how gnarly our mixins code looked at the beginning?
  * AND we can use function components; no more class components

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const Players = ({ teamId }) => {
  const {
    images, curPage, setCurPage
  } = useImages(teamId)

  return (
    &lt;section>
      &lt;Slideshow
        images={images}
        page={curPage}
        onNext={setCurPage}
      />
    &lt;/section>
  )
}</code></pre>
  </div>
</div>

NOTES:
- So now our same `Players` component calls our `useImages` custom hook
  * And gets the `images` & `curPage` data + `setCurPage` function
- And passes them on to the `<Slideshow />` component
- This is pretty similar in spirit to the render prop
  * But the `useImages` custom hook looks like a normal function call
  * So it has a typical input & outputs that functions have to get data
  * All outside of the render
  * So we don't get that sometimes-hard-to-parse UI nesting from the render prop

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">const Teams = () => {
  const {
    images, curPage, setCurPage
  } = useImages()

  return (
    &lt;section>
      &lt;ImageList
        items={images}
        page={curPage}
        onPage={setCurPage}
      />
    &lt;/section>
  )
}</code></pre>
  </div>
</div>

NOTES:
- If you remember before way in the beginning, we also had a `Teams` component
- And before it was also rendering a `<Slideshow />` component
  * To show how component UIs can be used
- But now instead we can render an `<ImageList />`
  * And it uses the same data we get back from `useImages`
- So we call the `useImages` custom hook like before
- But this time pass the data to `<ImageList />`
- So we were able to share the same state management + API calls
  * Across 2 different components
  * And render 2 completely different UIs, a `<Slideshow />` & a `<ImageList />`

/////
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 80%">
    <h2>Gotchas with Custom hooks</h2>

    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	    <div style="flex:0 0 60%;">
        <pre class="large"><code class="lang-javascript">const Example = () => {
  const translations = useI18n()
  const authData = useAuth()
  const theme = useTheme()

  // render UI
}</code></pre>
      </div>
      <div style="flex:0 0 35%;">
        <ul>
          <li>Conditional hooks</li>
          <li>No markup</li>
        </ul>
      </div>
  </div>
</div>

NOTES:
- The main advantage of custom hooks over render props is there's no nesting
  * Call the custom hooks in sequence
  * Use the variables in the UI
  * Can even use the `translations` variable as the input of `useAuth` if I wanted
  * So there is some **dynamic composition**
- However it's only semi-dynamic composition
  * It's not full like render props
  * It's against the rules to conditionally render custom hooks
  * So even if data from a hook is not needed because of the value of a prop
  * We still **must** call the hook
  * Like I mentioned we can pass values **to** the custom hook so it could do nothing based on the value
- The other thing to note is that custom hooks don't render markup
  * I didn't show this as we discussed them, but...
  * An HOC can render markup before, after or around the `Component` you passed to it
  * A render prop component can do the same to the function prop passed to it
  * But custom hooks cannot do that
  * For the most part, they're purely data
- This is why custom hooks haven't "killed" render props
  * There's still a place for them
  * Particularly when you need something to abstract state, logic AND UI
  * That's when you would use a render prop
  * That in itself can be a whole separate talk 😄

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Recap</h1>
  </div>
</div>

NOTES:
- Well that was a fun walk through React history
- I hope you caught it all
  * But if you were distracted by Slack, Discord or text messages
  * Here's a recap for ya

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h2>Implementations</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;">
	    <div style="flex:0 0 45%;">
        <h3>Mixins</h3>
        <pre class="large"><code class="lang-javascript">const ImagesMixin = {
  getInitialState() { ... },
  componentDidMount() { ... }
  componentDidUpdate() { ... }
}</code></pre>

        <h3>Higher-order components</h3>
        <pre class="large"><code class="lang-javascript">const withImages = (Comp) => (
  class Images extends Component {
    render() { ... }
  }
)</code></pre>
      </div>
      <div style="flex:0 0 45%; margin-left: 20px;">
        <h3>Render props</h3>
        <pre class="large"><code class="lang-javascript">class Images extends Component {
  render() {
    return this.props.render({})
  }
}</code></pre>

        <h3>Custom hooks</h3>
        <pre class="large"><code class="lang-javascript">const useImages = (teamId) => {
  // useState + useEffect

  return { ... }
}</code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- Mixins are an object
  * Maintain state + helper methods to be shared w/ consuming component
- HOCs are a function
  * Accept a component and return a new enhanced component
  * The enhanced component maintains state & logic
  * Then renders the initial component w/ additional props
- Render props are components with a prop function
  * The component maintains state & logic
  * Passes data to the prop function and renders returned UI
- Custom hooks are functions that use React hooks to maintain state
  * Return the data
- All 4 approaches maintain state + logic in their own way
  * To share w/ components that consume them

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Consumptions</h2>

    <div style="display:flex;align-items:flex-end;justify-content:space-around;">
	    <div style="flex:0 0 45%;">
        <h3>Mixins</h3>
        <pre class="large"><code class="lang-javascript">const Players = createClass({
  mixins: [ImagesMixin],

  render() { ... },
})</code></pre>

        <h3>Higher-order components</h3>
        <pre class="large"><code class="lang-javascript">const Players = () => (
  // render UI
)

withImages(Players)</code></pre>
      </div>
      <div style="flex:0 0 45%; margin-left: 20px;">
        <h3>Render props</h3>
        <pre class="large"><code class="lang-javascript">const Players = () => (
  &lt;Images>
    {() => { ... }}
  &lt;/Images>
)</code></pre>

        <h3>Custom hooks</h3>
        <pre class="large"><code class="lang-javascript">const Players = () => {
  const { ... } = useImages()

  // render UI
}</code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- To use mixins...
  * Use old-school `createClass` and are mixed in using the `mixins` prop
  * The state is now magically available to use
- To use HOCs...
  * Pass a component to the enhancer function
  * The main component will receive the state as extra props
- To use render props
  * Pass a function to the `children` or `render` prop
  * The function accepts the state and renders the UI
- To use custom hooks
  * Call the custom hook like a utility function
  * Render the UI based upon the returned data

=====
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://medium.com/@dan_abramov/mixins-are-dead-long-live-higher-order-components-94a0d2f9e750" target="_blank"><em>Mixins Are Dead. Long Live Composition</em></a> (3/13/2015)</li>
      <li><a href="https://reactjs.org/blog/2016/07/13/mixins-considered-harmful.html" target="_blank"><em>Mixins Considered Harmful</em></a> (7/13/2016)</li>
      <li><a href="https://ui.dev/react-higher-order-components/" target="_blank"><em>React Higher-Order Components</em></a></li>
      <li><a href="https://cdb.reacttraining.com/use-a-render-prop-50de598f11ce" target="_blank"><em>Use a Render Prop!</em></a> (9/18/2017)</li>
      <li><a href="https://ui.dev/react-render-props/" target="_blank"><em>React Render Props</em></a></li>
      <li><a href="https://reactjs.org/blog/2019/02/06/react-v16.8.0.html" target="_blank"><em>React v16.8: The One With Hooks</em></a> (2/6/2019)</li>
      <li><a href="https://reactjs.org/docs/hooks-intro.html" target="_blank"><em>Introducing Hooks</em></a></li>
      <li><a href="https://ui.dev/why-react-hooks/" target="_blank"><em>Why React Hooks?</em></a></li>
    </ul>
  </div>
</div>

NOTES:
- There are several blog posts covering this history
- It's fun to watch the timeline of the "approved" method of solving this problem
- React is continuously evolving!


/////
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 100%">
    <div style="display:flex;flex-wrap:wrap;align-items:center;justify-content:space-around">
      <div style="flex: 0 0 60%;">
        <a href="https://www.benmvp.com/minishops/typescript-for-react-developers/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">
          <img src="../../img/ts-react/typescript-for-react-developers.png" alt="A Screenshot of the TypeScript for React Developers minishop page on benmvp.com" class="plain" style="width: 100%" />
        </a>
      </div>
      <div style="flex: 0 0 40%; text-align: left;">
       <ul>
        <li><a href="https://www.benmvp.com/minishops/typescript-for-react-developers/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">TypeScript for React Developers</a></li>
        <li><a href="https://www.benmvp.com/minishops/zero-to-react-with-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">Zero to React with Hooks</a></li>
        <li><a href="https://www.benmvp.com/minishops/migrating-to-react-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">Migrating to React Hooks</a></li>
        <li><a href="https://www.benmvp.com/minishops/sharing-react-component-logic/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">Sharing React Component Logic</a></li>
      </ul>
    </div>
  </div>
</div>

NOTES:
- Before I finish...
- I periodically host a series of short, 3-hour remote React workshops
  * I call them "minishops"
- One of them is called "Sharing React Component Logic"
  * So if you're interested in hands-on learning of when to use different patterns for sharing
  * Including render props and custom hooks, like I was mentioning
  * As well as the others listed
- I'm doing a free giveaway for conference attendees
  * Go to my site (benmvp.com) and check out the minishops page
  * Find **one** you like AND can attend
  * Send out a tweet w/ the link and tag me in
  * I'll pick one and give you a free ticket

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=qconplus-2020" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:
- So that's it!
- Hopefully you found this journey insightful
  * Hopefully it made you appreciate hooks a bit more
  * And you probably got a history lesson too!
- Again, the slides are already available online
- Would love to chat and hear what you think!
  * Reach out to me on Twitter (@benmvp)
- Thanks!
- Hope you enjoy the rest conference!
