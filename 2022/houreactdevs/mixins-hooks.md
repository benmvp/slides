<!-- .slide: data-state="title-page" data-background="url(../../img/mixins-hooks/road-nighttime-ricardo-rocha-nj1bqRzClq8-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 80%;" class="content-overlay">

  <h1>From Mixins to Custom Hooks</h1>
  <h3>A history of sharing in React</h3>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=hrd-2022) | [@HoustonReactDev](https://twitter.com/HoustonReactDev)</p>

  <br />

  <p>September 22, 2022</p>

  </div>
</div>

NOTES:

- Hi everyone!
- **RESTART THE TIMER!!!!**
- I'm excited to be a part of Houston React Developers
  - Sharing about sharing in React 😂
- We're basically gonna go on a 8-year journey with React
  - Starting w/ mixins in the beginning to Hooks right now
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
  - No doubt it has lots of markup, styling & UI logic
- And we can easily use it in two components
  - `Players` component to have a slideshow of team player photos
  - `Teams` component to have a slideshow of team logos

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
  - Sharing helper functions is great too
  - Can call API utilities, data transformation helpers, etc
  - All from within the component code
- Here we have a `fetchImages` that when given an optional `teamId`
  - Will retrieve images of the players for the team
  - Or retrieve team logs when `teamId` is `undefined`
- Keep this `fetchImages` utility in mind because we'll be referencing it throughout

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

- But the tricky part is what I call the stateful, non-visual logic
  - What do I mean by that?
- We've got the `Players` & `Teams` components again
  - But this time they are rendering different UI
  - A `<SlideShow />` for `Players`, an `<ImageList />` for `Teams`
  - But `Players` & `Teams` both can call the same data `fetchImages` API
  - They both need to maintain state of images/logos
  - And both of them need to call the `fetchImages` API again when the page changes
- So they have similar state + logic but different UI
- Ideally we'd be able to render the paginated player images or team logos as...
  - A slideshow
  - A list view
  - A grid view
  0 Or whatever
  - But not have to repeat the stateful non-visual logic
- So I wanna take us on a journey of how we've tried to solve this problem over React's lifetime
  - To hopefully help us understand React a bit better

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

- My name is Ben Ilegbodu
- Christian, Husband, Father
- _Family introductions_
- We live in Pittsburg, CA (SF Bay Area)
  - I'm actually originally from Houston
  - Moved to the Bay Area 20 years ago
  - And now we're moving back in December!

/////

![Stitch Fix Corporate logo (dark)](../../img/stitchfix/lockup-solid-vert-gender-neutral-dark.svg)
<!-- .element: class="plain" style="width: 75%" -->

NOTES:

- I'm a Microsoft MVP & currently a Frontend Architect Engineer at Stitch Fix
- Stitch Fix is an online personal styling service
  - Combines technology & data science
  - With an actual human stylist
  - Take the effort out of shopping by providing a selection of clothes picked just for you
  - And sent to your door on a frequency that you choose
- We're hiring!
  - Headquarters is in SF
  - But we have remote engineers all over the country
  - I mentioned our job openings at the last conf I spoke at back in April
  - Someone reached out to me
  - And now we're coworkers!

=====
<!-- .slide: data-background="url(../../img/perfect-lib/annie-spratt-rx1iJ59jRyU-gift-box-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Custom hooks</h1>
    <h2>(React &gt;= 16.8)
  </div>
</div>

NOTES:

- Alright enough about me. Let's just right in
- I know typically histories start from the past to the present
  - But I want to try going backwards in history
  - So we can start with what we're probably most familiar with
  - **custom hooks**
- Hooks were designed specifically to solve this problem of sharing stateful, non-visual logic
  - Came out with React 16.8 (in early 2019)
- If you've developed any React recently, you should be using custom hooks
  - Let's take a look...

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

- **ONE:** Here's that `Players` component we were talking about
  - Remember we needed a way to retrieve the player images?
  - Well now we've got a way with this special function
- **TWO:** It's called `useImages`
  - It's a called a "Hook"
  - And in this case, it's a "custom Hook" because we've defined it ourselves
  - And we'll take a peek at it next
  - `Players` calls our `useImages` custom Hook, passing it the `teamId`
  - **THREE:** And gets the `images` & `curPage` data + a `setCurPage` function
- **FOUR:** It passes them on to that `<Slideshow />` component
- This all seems pretty "magical" to be honest
  - And in a sense, it is
  - **FIVE:** The `useImages` custom Hook looks like a normal function call
  - So it has the typical inputs & outputs that functions have to get data
  - And it's separate from the UI
  - Let's take a look at how it's implemented

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
  - **ONE:** So we're calling it `useImages`
- **TWO:** It maintains state for `images` & `curPage`
  - Using the built-in `useState` Hook
- **THREE:** It fetches new images whenever the current page changes
  - We're using the built-in `useEffect` Hook which takes a bit of getting used to to be honest
- **FOUR:** Finally it returns the data the consuming component needs
  - `images`, `curPage` & `setCurPage` (the function that updates the `curPage`)
- It's pretty nice that the entire functionality fits on one screen
  - You'll see in a bit how gnarly things will get

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

- **ONE:** If you remember, we also have a `Teams` component
- **TWO:** And instead of rendering a `<Slideshow />` we wanna render an `<ImageList />`
  - Well now we can use the same _type_ of data we get back from `useImages`
- **THREE:** So we call the `useImages` custom Hook like before
- **FOUR:** But this time pass the data to `<ImageList />`
- So we were able to share the same state management + API calls
  - Across 2 different components
  - And render 2 completely different UIs, a `<Slideshow />` & a `<ImageList />`
  - That's the power & ease of custom Hooks

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

- The nice thing about custom Hooks the other patterns we'll see is that we can call them in sequence
- However we still have some issues
- 1/ React Hooks cannot be called conditionally
  - Because it's against the rules to conditionally render custom Hooks
  - So even if we know we don't need to call a Hook because of the value of a prop
  - We still **must** call the hook
  - Buuut there are ways around this and I'll share a blog post about it
- 2/ The other thing to note is that custom hooks don't render markup
  - For the most part, they deal purely data
- This is why custom hooks haven't "killed" another pattern called Render Props
  - What are Render props?
  - Well... let's talk about them


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Render props</h1>
    <h2>(React &lt; 16.8)</h2>
  </div>
</div>

NOTES:

- Technically Render Props have always existed in React
  - And they still do now, actually
  - But they were popularized by Michael Jackson from React Training
  - As a superior replacement of HOCs (we'll talk about those next)
  - This was right around when React 16 was released (mid-2017)
- Let's see how render props compare to Hooks...

/////
<!-- .slide: data-background="url(../../img/mixins-hooks/basketball-hoop-brandi-redd-z_UJ6FhVJZI-unsplash.jpg) no-repeat center" data-background-size="cover" -->
<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">class Images extends React.Component {
  state = { images: [], curPage: 1 }
  componentDidMount() { this.updateImages() }
  componentDidUpdate(prevProps, prevState) {
    if (prevState.curPage !== this.state.curPage
      || prevProps.teamId !== this.props.teamId) {
      this.updateImages()
    }
  }
  updateImages() {
    fetchImages(this.props.teamId, this.state.curPage)
      .then((images) => { this.setState({ images }) })
  }
  // render...
}</code></pre>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 415px; top: 195px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 240px; top: 594px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 821px;"></div>
  </div>
</div>

NOTES:

- This is already a lot of code and it isn't even all of it
  - But let me try to break it down
- So instead of a special function for our shareable code
  - **ONE:** We have a class component
  - Anyone still using class components?
  - Chime in in the chat
  - We're calling it `Images` here
  - This compares with our `useImages` Hook
- **TWO:** It has the same `state` as the Hook
  - but it's defined in the class component way
- **THREE:** We use the `componentDidMount` & `componentDidUpdate` lifecycle methods
  - To retrieve the images initially and...
  - When either the `curPage` state or the `teamId` prop change...
  - By calling `updateImages()`
  - We'll see how the `teamId` prop is used in a couple of slides
- **FOUR:** The `updateImages()` method is where we make the actual `fetchImages()` call
  - And set the `images` state w/ returned data
  - It's intended to be "private" but back then we didn't yet have private methods
- And if class components aren't familiar to you
  - Don't get too hung up on the code either way
- **FIVE:** But let's take a look at the last piece I couldn't fit on the screen
  - The `render()` method of this class component

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 423px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 480px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 594px;"></div>
  </div>
</div>

NOTES:

- **ONE:** The key piece of a render prop pattern is the function prop called `render`
  - It's a special component prop that is a function
  - Typically function props are callback functions like `onClick` or `onChange`
  - They respond to an event & do something, but don't return anything
- This `render` prop is a function that takes in data and will return JSX
  - It can actually be named anything, but `render` is a common convention
  - Hence the term "render prop"
  - It's also common to use the `children` prop as well
- So within the `render()` method we call the `render` prop
  - And we pass it all the data the caller of `<Images />` will need
- **TWO:** First we have the `images` & `curPage` state properties
- **THREE:** As well as a `handleNextPage` callback
  - It's for updating the `curPage` state when paginating
  - And based on the previous slide, updating the `curPage` will ultimately fetch new images
  - Which will in turn calls the render prop with new `images` state
- For the render prop, the stateful, non-visual logic is...
  - `state` + the lifecycle methods + `render` prop
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

- It looks kind of like a normal React component
- The `<Images />` render prop component we just defined...
  - Basically exposes its underlying state to its parent component
  - Which is now `Players` in this case
- **ONE:** By calling the `render` prop function passed to it...
  - `Players` can now render whatever UI it likes based on the `data` it receives in the `render` prop!
- **TWO:** And here, just like the preview example, it's rendering the `<Slideshow />`
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
  - There's no public definition of what parameters the function will pass
  - What's the shape of `translations`?
  - What properties are in `authData`?
  - Is `theme` and object or a single value?
  - It can be tricky to know without something like TypeScript
- 2/ Also as we can see here... when there are multiple render props
  - Things can get a bit crazy with the nesting
  - With render props the entire UI is nested w/in the function prop
  - So here we're 6 levels indented before we even begin the real UI
- But overall render props worked well for sharing stateful, non-visual logic
  - But Hooks kind took over as a tailor-made solution
- However render props are still useful when a component wants to...
  - 1/ share stateful, non-visual logic
  - 2/ also needs to offload rendering UI to the parent
- I wish I could spend more time explaining render props
  - But I still have 2 more to cover


=====
<!-- .slide: data-background="url(../../img/mixins-hooks/russian-nesting-dolls-julia-kadel-YmULswIbc3I-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Higher-order components (HOCs)</h1>
    <h2>(React 15)</h2>
  </div>
</div>

NOTES:

- Let's talk about the pattern that was popular before render props
  - Higher-order components aka HOCs
- You may never have even seen HOCs depending on when you started working in React
  - Just like w/ render props, HOCs technically always existed
  - But the pattern was first "created" way back in React 0.13 (early 2015)
  - It was later popularized by Dan Abramov before he even started working at Facebook
- Render props can do everything an HOC can do
  - And arguably in a better developer experience
  - Render props kinda made the HOC patter obsolete
- But let's take a look at them anyway
  - Because before render props they were a way to solve the problem...
  - Of how to share stateful, non-visual logic

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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 480px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 594px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 536px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 656px;"></div>
  </div>
</div>

NOTES:

- An HOC was (technically still is) a function that takes an existing component
  - And returns another component that wraps the original one
- **ONE:** So `withImages` is the HOC & it takes the `Component` reference as a parameter
  - Prefixing the HOC with `with*` was a common convention
  - It's not a requirement like `use*` is with Hooks, but was a convention
- Our Hook was named `useImages`
  - Our render prop component was called `Images`
  - And now our HOC is called `withImages`
  - **TWO:** And it returns a new class component called `Images`
  - It's a component class that wraps our actual `Component` we've passed in
- **THREE:** `Images` has all the same `state` & lifecycle methods as the previous approaches
- **FOUR:** The big difference is that the HOC **renders** the component passed in
- **FIVE:** It passes along all the existing `props`
- **SIX:** But then adds to the props those state properties it's maintaining
  - **SEVEN:** The `curPage` state that gets updated as we paginate the images
  - **EIGHT:** The `images` state that comes back from fetching new images based on the `curPage`
- **NINE:** We also pass the same `handleNextPage` callback function prop
  - Which updates the `curPage` state
- There's a lot more to the HOC code
  - I'm just trying to showcase the highlights
  - Again the HOC is a function that takes a component class and returns a wrapped one

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
const EnhancedPlayers = withImages(Players)

export default EnhancedPlayers</code></pre>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 594px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 252px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 365px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 707px;"></div>
  </div>
</div>

NOTES:

- The HOC is used very differently than the render prop
- **ONE:** The way we use `withImages` is completely outside of the component definition
  - We pass it a reference to our `Players` component to `withImages`...
  - And it gives us back an "enhanced" or wrapped version
  - `withImages` will be what actually renders `<Players>`
- **TWO:** And if you remember...
  - `withImages` passed the state it was keeping as props to the `Component` we passed in
  - So now our `Players` component can magically assume that it'll now have those props
- By wrapping `Players` with `withImages`...
  - The HOC will do the work to maintain the state & lifecycle methods
  - **THREE:** As the `Slideshow` paginates we update the UI by calling the `handleNextPage` prop
- **FOUR:** And lastly the exported `EnhancedPlayers` is the actual component that'll be used in UIs
- IMO it's all a bit weird & difficult to wrap your head around at first
  - And at second, and third and forth 😂
  - I always found HOCs to be a very strange concept
  - But it was the pattern we had at the time...

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

- So HOCs worked _okay_, but there were several gotchas with them
- 1/ HOCs inherently relied on indirection & agreements to work
  - With **HOCs** the only communication is through props
  - But with multiple HOCs we now don't know which HOC is providing which props
- 2/ There can be prop name collisions if 2 HOCs try to set the same prop
  - Like multiple HOCs wanting to set a `value` prop
- 3/ Lastly there's no way to alter or configure how the HOCs are composed based on the component's props or state
  - Let's look at this code snippet
  - Maybe we only want to add `withAuth` if a `needsAuth` prop is set to `true`
  - The composition of the HOCs is happening outside of the `render()` method
  - So the prop values can't impact which HOCs are used
  - This wasn't always a problem, but it did make complex situations challenging
- But again don't worry if you don't understand HOCs immediately
  - I'd be more surprised if you did 😂
  - It's based on Higher-order functions found in mathematics
  - Many blog posts were written to explain the concept
  - Plus you'll never need to write one in modern React anyway thanks to Hooks & render props 😃

=====

<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Mixins</h1>
    <h2>(React &lt;= 0.14)</h2>
  </div>
</div>

NOTES:

- So we've talked about custom Hooks, render props, and just now HOCs
- Let's talk about the OG way of handling this problem of stateful, non-visual logic: **mixins**
  - This is React 0.14 before
  - We're talking early 2016 and before
  - This was the original way of sharing stateful, non-visual logic
- I'm assuming most, if not all, of you have never seen this code before
  - But feel free to give a shout-out in the chat if you developed during these days

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">var ImagesMixin = {
  getInitialState: function() {
    return { images: [], curPage: 1 }
  },

  // componentDidMount & componentDidUpdate

  updateImages: function() {
    // fetch images
  },

  handleNextPage: function(curPage) {
    this.setState({ curPage })
  },
}</code></pre>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 365px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 480px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 185px; top: 707px;"></div>
  </div>
</div>

NOTES:

- **ONE:** Here's the implementation of `ImagesMixin`
  - It's just a simple object with property definitions
- **TWO:** the same `images` & `curPage` state are defined in the `getInitialState`
  - Similar to a class constructor
- **THREE:** We have the same `componentDidMount` & `componentDidUpdate` lifecycle methods
  - I didn't bother writing them out again
  - They're the same ones from the render prop...
  - That retrieve the images initially and when the `curPage` state or `teamId` prop change
- **FOUR:** The lifecycle methods also call `updateImages`
  - And again that's where we make the actual `fetchImages` call
  - Which sets the `images` state w/ returned data
  - All the innards are the same as the previous patterns
  - Oh `updateImages` is technically "private" and only supposed to be called w/in the mixin
  - But we'll see shortly that anything could call it outside of the mixin
- **FIVE:** And finally we provide the `handleNextPage` helper method
  - It's **exclusively for the components** to update the current page
  - It's not actually called from within the mixin
- At a high level, it seems simple enough
  - Like Hooks, mixins were created primarily for solving this problem...
  - Of stateful, non-visual logic

/////
<!-- .slide: data-background="url(../../img/ts-react/mixing-console-abigail-keenan-QdEn9s5Q_4w-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">var Players = React.createClass({
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
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 81px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 137px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 130px; top: 423px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 536px;"></div>
  </div>
</div>

NOTES:

- And here's how we'd use the mixin
- **ONE:** We used `React.createClass` to create our `Players` component
  - This is before ES6 classes & the React class component existed
- And it took an optional `mixins` property to define 1 or more mixins
  - **TWO:** Here we're using the `ImagesMixin` object which we just defined
- `ImagesMixin` defines the `images` & `curPage` the state variables
  - **THREE:** that we now can use to pass to the `<SlideShow />`
- **FOUR:** And finally that `this.handleNextPage` helper is called when the slideshow changes
  - Remember: this helper method was also defined in the `ImagesMixin`
- As you can see there appears some magic happening
  - Kind of similar to the HOCs in a sense
  - It feels like the state is magically available
  - And we have to know that `handleNextPage` is also provided
  - And that we should not use `updateImages`

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

- Mixins kinda had the same problems as the HOCs that came after, but different flavors
- 1/ ES Classes didn't support mixins
  - This was a biggie
  - The React team wanted to move to using ES classes instead of maintaining their own class system
- 2/ Mixins had the same indirection problem as HOCs
  - A mixin might need the component to define a helper method/property or vice versa
  - The `handleNextPage` method in `ImageMixins` provided is an example of this
  - Our `Players` component relied on its existence
  - Furthermore, when there were multiple mixins it was hard to know where the state came from
- 3/ Also there could be helper method name collisions
  - What if 2 mixins wanted to name a method `handleNextPage` or even `updateValue`?
  - So we would have to namespace the method names to ensure they were unique
- These problems were so bad...
  - That eventually there was even an official React blog post entitled _Mixins Considered Harmful_
  - I've got a link at the end of the slides

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">

    <pre class="large"><code class="lang-javascript">var ImagesMixin = {
  getInitialState() { return { images: [], curPage: 1 } },
  componentDidMount: function() { this.updateImages() },
  componentDidUpdate: function(prevProps, prevState) {
    if (prevState.curPage !== this.state.curPage
      || prevProps.teamId !== this.props.teamId) {
      this.updateImages()
    }
  },
  updateImages: function() {
    fetchImages(this.props.teamId, this.state.curPage)
      .then((images) => { this.setState({ images }) })
  },
  handleNextPage(curPage) { this.setState({ curPage }) },
}</code></pre>
  </div>
</div>

NOTES:

- So let's do a quick comparison of Mixins vs. Hooks
- Here's the full implementation of the `ImagesMixin`
- This was the way to go in 2015

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
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

- Contrast that with the `useImages` Hook implementation
- Which became the new way in 2019
- There was quite a bit of churn in between in those 4 years
  - For those of us who were developing during that time
- But I'll certainly take Hooks over Mixins
  - Makes me wonder where we'll be 4 years from now!

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
      <li><a href="https://www.benmvp.com/blog/conditional-react-hooks/?utm_source=benmvp&utm_medium=slides&utm_campaign=hrd-2022" target="_blank"><em>Conditional React Hooks</em></a></li>
    </ul>
  </div>
</div>

NOTES:

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

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=hrd-2022" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:

- So that's it!
- Hopefully you found this reverse journey insightful
  - And hopefully it made you appreciate Hooks a bit more 😄
  - And you probably got a bit history lesson too!
- Again, these slides are already available online
- If you've got questions
  - Drop them in the Q&A and I'll do my best to answer
  - And if you've got other questions about React, I'll do my best to answer those too
- But if you think of something later
  - Reach out to me on Twitter (@benmvp)
- Thanks!
