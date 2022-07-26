<!-- .slide: data-state="title-page" data-background="url(../../img/mixins-hooks/road-nighttime-ricardo-rocha-nj1bqRzClq8-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 80%;" class="content-overlay">

  <h1>From Mixins to Custom Hooks</h1>
  <h3>A history of sharing in React</h3>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=hackbuddy-2022) | [@hackbuddyorg](https://twitter.com/hackbuddyorg)</p>

  <br />

  <p>July 26, 2022</p>

  </div>
</div>

NOTES:

- Hi everyone!
- **RESTART THE TIMER!!!!**
- I'm excited to be a part of HackBuddy
  * Hopefully I can help you **level up your software engineering**
  * Sharing about sharing in React 😂
- We're basically gonna go on a 8-year journey with React
  * Starting w/ mixins in the beginning to hooks right now
- **Slides are available online**
- I'm gonna be paying attention to the chat a bit, so join in!
- **RESTART THE TIMER!!!!**

=====
<!-- .slide: data-background="url(../../img/ts-react/electric-cables-john-barkiple-l090uFWoPaI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: center">
	<div style="width: 60%;" class="content-overlay">
    <a href="https://reactjs.org/" target="_blank"><img src="../../img/react/react-logo.svg" class="plain" /></a>
  </div>
</div>

NOTES:
_[1 minute]_

- React's approach to building user interfaces makes sharing & reuse great!

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
      <div class="code-highlight" style="height: 295px; top: 480px;"></div>
    </div>
  </div>

  </div>
</div>

NOTES:

- React is especially great at sharing UI
- Here we have a `<Slideshow>` component
  * No doubt it has lots of markup, styling & UI logic
- And we can easily use it in two components
  * `Players` component to have a slideshow of team player photos
  * `Teams` component to have a slideshow of team logos

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
    .then(/\* retrieve \`page\` subset \*/)
}</code></pre>
  </div>
</div>


NOTES:

- And because React is basically "Just JavaScript™"
  * Sharing helper functions is great too
  * Can call API utilities, data transformation helpers, etc
  * All from within the component code
- Here we have a `fetchImages` that when given an optional `teamId`
  * Will retrieve images of the players for the team
  * Or retrieve team logs when `teamId` is `undefined`

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
    <div class="code-highlight" style="height: 295px; top: 480px;"></div>
  </div>
</div>

NOTES:
_[2 minutes]_

- But the tricky part is what I call the stateful, non-visual logic
  * What do I mean by that?
- We've got the `Players` & `Teams` components again
  * But this time they are rendering different UI
  * A `<SlideShow />` for `Players`, an `<ImageList />` for `Teams`
  * But `Players` & `Teams` both can call the same data `fetchImages` API
  * They both need to maintain state of images/logos
  * And both of them need to call the `fetchImages` API again when the page changes
- So they have similar state + logic but different UI
- Ideally we'd be able to render the paginated player images or team logos as...
  * A slideshow
  * A list view
  * A grid view
  * Or whatever
  * But not have to repeat the stateful non-visual logic
- So I wanna take us on a journey of how we've tried to solve this problem over React's lifetime
  * To hopefully help us understand React a bit better

=====

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
    <img src="../../img/family/ilegbodu-family-photo-2022.jpg" alt="Ilegbodu family photo in 2022" />
  </div>
</div>

NOTES:
_[3 minutes]_

- My name is Ben Ilegbodu
- Christian, Husband, Father
- _Family introductions_
- We live in Pittsburg, CA (SF Bay Area)

/////

![Stitch Fix Corporate logo (dark)](../../img/stitchfix/lockup-solid-vert-gender-neutral-dark.svg)
<!-- .element: class="plain" style="width: 75%" -->

NOTES:

- I'm a Frontend Architect Engineer at Stitch Fix
- Stitch Fix is an online personal styling service
  * Combines technology & data science
  * With an actual human stylist
  * Take the effort out of shopping by providing a selection of clothes picked just for you
  * And sent to your door on a frequency that you choose
- We're hiring!
  * Headquarters is in SF
  * But we have remote engineers all over the country
  * I mentioned our job openings at the last conf I spoke at in March
  * Someone reached out to me
  * And now we're coworkers!
- I'm also a Microsoft MVP

=====

<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Mixins</h1>
    <h2>(React &lt;= 0.14)</h2>
  </div>
</div>

NOTES:
_[4 minutes]_

- Alright enough about me. Let's just right in
- The first approach to solve this problem of stateful, non-visual logic was via **mixins**
  * React 0.14 before
  * We're talking early 2016 and before
- I'm assuming most, if not all, of you have never seen this code before
  * But feel free to give a shout-out in the chat if you developed during these days

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 423px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 536px;"></div>
  </div>
</div>

NOTES:

- We used `React.createClass` to create a component
  * This is before ES6 classes
- And it took an optional `mixins` property to define 1 or more mixins
  - **ONE:** Here we're using an `ImagesMixin` which I'll show in a sec
- In this case `ImagesMixin` defines the `images` & `curPage` state variables
  * **TWO:** That are passed to the `<SlideShow />`
- **THREE:** And finally `this.handleNextPage` is called when the slideshow changes
  * This helper method is also defined in the mixin
- As you can see there's some magic happening
  * The state is magically available
  * And we have to know that `handleNextPage` is also provided

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 415px; top: 195px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 240px; top: 594px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 821px;"></div>
  </div>
</div>

NOTES:

- And here's the implementation of `ImagesMixin`
  * Kinda gnarly to look at
  * But let's try walk through it
- **ONE:** the `images` & `curPage` state are defined in the `getInitialState`
  * Similar to a class constructor
- **TWO:** We use `componentDidMount` & `componentDidUpdate`
  * To retrieve the images initially and...
  * When either the `curPage` state or the `teamId` prop change
  * ...By calling `updateImages`
- **THREE:** `updateImages` is where we make the actual `fetchImages` call
  * It's technically "private" and only called w/in the mixins (but it's leaky)
  * And set `images` state w/ returned data
- **FOUR:** And finally we provide the `handleNextPage` helper method **exclusively for the components**
  * To update the current page
  * It's not actually called from within the mixin
- _This_ is the stateful, non-visual logic that we're trying to share
  * State + lifecycle methods + event handler

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

- Mixins worked _okay_, but there were several gotchas with them
- 1/ ES Classes didn't support mixins
  * React team wanted to move to using ES classes instead of maintaining their own class system
- 2/ Mixins inherently relied on indirection & agreements to work
  * A mixin might need the component to define a helper method/property or vice versa
  * The `handleNextPage` method that `ImageMixins` provided is an example of this
  * Furthermore, when there were multiple mixins it was hard to know where the state came from
- 3/ Also there could be helper method name collisions
  * What if 2 mixins wanted to name a method `handleNextPage` or even `updateValue`?
  * So we would have to namespace the method names to ensure they were unique


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Higher-order components (HOCs)</h1>
    <h2>(React 15)</h2>
  </div>
</div>

NOTES:
_[9 minutes]_

- So because of all of those issues
  * React 15 migrated to ES classes (in mid-2016) & ditched mixins support
  * And it was kind of a big deal
  * There was even an official blog post entitled _Mixins Considered Harmful_
- So w/o mixins we needed a new strategy for solving this problem...
  * Of sharing stateful, non-visual logic
- The next pattern that became popular was higher-order components (HOCs)
  * The pattern was first created way back in React 0.13 (early 2015)
  * But it was later popularized by Dan Abramov before he even started working at Facebook
- While I did touch old mixins code
  - React 15 with class components is really when I started developing in React

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 700px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 195px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 350px; top: 365px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 423px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 480px;"></div>
  </div>
</div>

NOTES:

- An HOC was (technically still is) a function that takes an existing component
  * And returns another component that wraps the original one
- **ONE:** So `withImages` is the HOC & it takes the `Component` reference as a parameter
  * Prefixing the HOC with `with*` was a common convention
  * Our mixin was named `ImagesMixin`, now our HOC is called `withImages`
  * **TWO:** And it returns a new class component called `Images`
  * It's a wrapper class
- **THREE:** `Images` has all the same `state` & lifecycle methods as the mixins approach
- **FOUR:** The big difference is that the HOC **renders** the component passed in
  * **FIVE:** It passes along all the existing `props`
  * **SIX:** But then adds to the props the state properties
  * As well as the `handleNextPage` callback function prop

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
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 252px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 594px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 365px;"></div>
  </div>
</div>

NOTES:

- The HOC is used similar to the mixin
- **ONE:** Except the component is receiving props passed to it instead of state
  * The `Players` component we write pretends it is a simple component just retrieving props
- **TWO:** But the exported component is the actual component that'll be used in UIs
  * The `Players` component reference is what is passed as the parameter to `withImages`
  * And `withImages` will be what renders `<Players>`...
  * Passing `images`, `curPage` & `handleNextPage`
- By wrapping `Players` with `withImages`, the HOC will do the work to maintain the state & lifecycles
  * **THREE:** As we paginate we update the UI bay calling the `handleNextPage` prop

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

- HOCs kinda inherited the same problems as mixins but different flavors
- 1/ Indirection was still a problem
  * With **HOCs** the only communication is through props
  * But with multiple HOCs we now don't know which HOC is providing which props
- 2/ There can be prop name collisions if 2 HOCs try to set the same prop
  * Like multiple HOCs wanting to set a `value` prop
- 3/ Lastly there's no way to alter or configure how the HOCs are composed based on the component's props or state
  * Like maybe we only want to add `withAuth` if the `needsAuth` prop is set to `true`
  * We can see that the composition of the HOCs is happening outside of the `render()` method
  * So the prop values can't impact which HOCs are used
  * This wasn't always a problem, but it did make complex situations challenging
- Don't worry if you don't understand HOCs immediately
  * It's based on Higher-order functions in mathematics
  * Many blog posts were written to explain the concept
  * Plus you'll never need to write one in modern React anyway 😃


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Render props</h1>
    <h2>(React &lt; 16.8)</h2>
  </div>
</div>

NOTES:
_[13 minutes]_

- Render props have actually always existed in React
  * And they still do now, actually
  * But they were popularized by Michael Jackson from React Training
  * As a superior replacement of HOCs
  * This was right around when React 16 was released (mid-2017)

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 423px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 480px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 594px;"></div>
  </div>
</div>

NOTES:

- So instead of a special mixin or a function
  * **ONE:** We have a normal class component
  * Calling it `Images` here
  * Remember we had the `withImages` HOC and `ImagesMixin`
- **TWO:** It has all the same `state` & lifecycle methods as the HOC & mixins approaches
  * That's our stateful, non-visual logic
- **THREE:** The key piece here is the function prop called `render`
  * It's a special component prop that is a function
  * Typically function props are callback functions like `onClick` or `onChange`
  * They respond to an event & do something, but don't return anything
- This `render` prop is a function that takes in data and will return JSX
  * It can actually be named anything, but `render` is a common convention
  * Hence the term "render prop"
  * It's also common to use the `children` prop as well
- So within the `render()` method we call the `render` prop
  * And we pass it all the data the caller of `<Images />` will need
  * **FOUR:** The `images` & `curPage` state properties
  * **FIVE:** As well as the `handleNextPage` callback for updating the `curPage` state when paginating
- So how do we use this render prop?

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
    <div class="code-highlight fragment current-visible" style="height: 415px; top: 308px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 295px; top: 365px;"></div>
  </div>
</div>

NOTES:

- Kind of like a normal React component
- The `<Images />` component basically exposes its underlying state to its parent component
  * Which is `Players` in this case
- **ONE:** By calling the `render` prop function passed to it...
  * `Players` can now render whatever UI it likes based on the `data` it receives in the `render` prop!
- **TWO:** And here, just like the other examples, it's rendering the `<Slideshow />`
  * And any other UI that relies on the `data` would go w/in `<Images />` as well

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

- However, there are still a couple of pain points
- 1/ React `PropTypes` only have `PropTypes.func`
  * There's no public definition of what parameters the function will pass
  * What's the shape of `translations`?
  * What properties are in `authData`?
  * Is `theme` and object or a single value?
  * It can be tricky to know without something like TypeScript
- 2/ Also as we can see here... when there are multiple render props
  * Things can get a bit crazy with the nesting
  * With render props the entire UI is nested w/in the function prop
  * So here we're 6 levels indented before we even begin the real UI
- But overall render props worked well for sharing stateful, non-visual logic
- I wish I could spend more time explaining render props
  * Because they are still useful in certain cases
  * But I need to get to the last pattern

=====
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Custom hooks</h1>
    <h2>(React &gt;= 16.8)
  </div>
</div>

NOTES:
_[17 minutes]_

- So we've talked about mixins, then HOCs, and just now render props
- Then with React 16.8 (in early 2019) finally came custom hooks (dun! dun! dun!!! 😂)
- They were designed specifically to solve this problem of sharing stateful, non-visual logic

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 350px; top: 308px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 707px;"></div>
  </div>
</div>

NOTES:

- Custom Hooks are **functions** that _must_ start with `use`
  * **ONE:** So we're calling it `useImages`
- **TWO:** It maintains state for `images` & `curPage` just like the others
  * Now using the `useState` Hook
- **THREE:** It fetches new images whenever the current page changes as well
  * We're now using the `useEffect` hook which is a bit simpler
- **FOUR:** Finally we're returning the data the consuming component needs
  * `images`, `curPage` & `setCurPage` (the function that updates the `curPage`)
- It's all the same things as before, but much clearer & more concise IMO
  * I could actually fit it all on one screen!
  * And do you remember how gnarly our mixins code looked at the beginning?

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 195px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 536px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 137px;"></div>
  </div>
</div>

NOTES:

- **ONE:** We have our same `Players` component
  * Except now it's a function component...
  * Because only function components can call Hooks
- **TWO:** And `Players` calls our `useImages` custom Hook
  * Passing in the `teamId`
  * **THREE:** And gets the `images` & `curPage` data + `setCurPage` function
- **FOUR:** And passes them on to the `<Slideshow />` component
- This is pretty similar in spirit to the render prop
  * **FIVE:** But the `useImages` custom hook looks like a normal function call
  * So it has the typical inputs & outputs that functions have to get data
  * And it's separate from the UI
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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 295px; top: 480px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 536px;"></div>
  </div>
</div>

NOTES:

- **ONE:** If you remember before way in the beginning, we also had a `Teams` component
  * It's also a function component now
- **TWO:** And instead of rendering a `<Slideshow />` we wanna render an `<ImageList />`
  * Well now we can use the same _type_ of data we get back from `useImages`
- **THREE:** So we call the `useImages` custom hook like before
- **FOUR:** But this time pass the data to `<ImageList />`
- So we were able to share the same state management + API calls
  * Across 2 different components
  * And render 2 completely different UIs, a `<Slideshow />` & a `<ImageList />`
  * That's the power & ease of custom Hooks

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

- The main advantage of custom Hooks over render props is there's no nesting
  * We can call the custom Hooks in sequence
- However we still have some issues
- 1/ With render props I could conditionally render the render prop component
  * Because it's against the rules to conditionally render custom Hooks
  * So even if data from a Hook is not needed because of the value of a prop
  * We still **must** call the hook
  * Buuut there are ways around this and I'll share a blog post about it
- 2/ The other thing to note is that custom hooks don't render markup
  * I didn't show this as we discussed them, but...
  * An HOC can render markup before, after or around the `Component` we pass to it
  * A render prop component can do the same to the function prop passed to it
  * But custom hooks cannot do that
  * For the most part, they deal purely data
- This is why custom hooks haven't "killed" render props
  * Render props may have removed the need for HOCs
  * But there's still a place for render props
  * Particularly when you need something to abstract state, logic **AND** UI
  * But that in itself can be a whole separate talk 😄

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
      <li><a href="https://www.benmvp.com/blog/conditional-react-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=hackbuddy-2022" target="_blank"><em>Conditional React Hooks</em></a></li>
    </ul>
  </div>
</div>

NOTES:
_[22 minutes]_

- As we wrap...
- There are several blog posts you can read that cover this history we went over
- It's fun to watch the timeline of the "approved" method of solving this problem
- React is continuously evolving!

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=hackbuddy-2022" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:
_[25 minutes]_

- So that's it!
- Hopefully you found this journey insightful
  * And hopefully it made you appreciate hooks a bit more 😄
  * And you probably got a bit history lesson too!
- Again, these slides are already available online
- If you've got questions
  * Drop them in the Q&A and I'll do my best to answer
  * And if you've got other questions about React, I'll do my best to answer those too
- But if you think of something later
  * Reach out to me on Twitter (@benmvp)
- Thanks!
