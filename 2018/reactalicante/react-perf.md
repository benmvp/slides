<!-- .slide: data-background="url(../../img/react-perf/react-alicante-title-slide.jpg) no-repeat center" data-background-size="cover" -->

/////

<!-- .slide: data-background="url(../../img/react-perf/react-alicante-sponsor-slide.jpg) no-repeat center" data-background-size="cover" -->

/////

<!-- .slide: data-background="url(../../img/react-perf/jeremy-bishop-136488-unsplash-turtle-on-beach.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="content-overlay">
  
  <h1>Help!<br />My React app is slowwwww!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#ReactAlicante](https://twitter.com/hashtag/reactalicante)</p>

  <br />

  <p>14 September 2018</p>
  
  
  </div>
</div>

NOTES:
- Buenas tardes!
- Excited to be here at React Alicante
- Excited to be in Spain; it's my first time!
- Had a fun React/Redux testing workshop yesterday
- But talking about something totally different now


- Was speaking at Chain React in Portland, Oregon last year
- Spoke about React Native + ES.next
- But an attendee came up to me asking me to help diagnose a slow app
- Then 2 days later, Trey Huffine talked about React performance at SF React meetup
- Those plus experience reviewing code were the motivation for this talk

/////
<!-- .slide: data-background="url(../../img/react/react-logo.png) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 4em">Reconciliation</h1>
  </div>
</div>


NOTES:
- Internally, React uses several clever techniques to minimize the number of costly DOM operations required to update the UI
  * The `reconciler` makes this possible
  * Keeps a copy of the render tree and compares with new render
- For most apps, using React will lead to a fast user interface
- Don't have to optimize for performance
- But not a silver bullet
  * Number of ways to speed up your React app
  * If you’re noticing a slowdown, might wanna fix these
  * OR in a situation where you need to squeeze every ounce of performance

=====
<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But first, would like everyone to stand up!
- Squats counting from in español
- Now turn to your neighbors, fist bump & say hi

/////
<!-- .slide: data-background="url(../../img/family-selfie-madrid.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Christian, Husband, Father
- I'm learning Español so would love to talk with you in Spanish

/////
<!-- .slide: data-background="#222" -->

![Eventbrite logo](../../img/eventbrite/wordmark-orange.png)
<!-- .element: class="plain" -->

![Ticketea logo](../../img/eventbrite/ticketea-by-eventbrite-white.svg)
<!-- .element: class="plain fragment" style="width: 60%" -->

NOTES: 
- I'm a Principal Frontend Engineer at Eventbrite
- Work on our Frontend Platform team
  * Doing FE infra + design system work
- **ONE:** Recently added Ticketea to the family

=====
<!-- .slide: data-background="url(../../img/react-perf/jeremy-bishop-136488-unsplash-turtle-on-beach.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
**_[6 minutes]_**

- Enough about me, let's talk about React performance
- Broken it down into 3 main sections of things to avoid
- Ordered by most hurtful to least
- And I'll try to provide alternatives to make your apps faster

=====
<!-- .slide: data-background="#222" -->

# Avoiding unnecessary DOM updates
<!-- .element: class="statement" -->

NOTES:
- Touching the DOM is the most expensive thing we can do!

=====
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash-race-car.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>1. `key`</h1>
  </div>
</div>

NOTES:
**_[7 minutes]_**

- Impact of `key`

/////
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash-race-car.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <video data-autoplay loop style="width: 100%">
      <source data-src="../../img/react-perf/index-as-key.mp4" />
    </video>
  </div>
</div>


NOTES:
- Here's very simple example of a list
- And as we add something to the beginning of the list
- All of the elements are getting updated

/////
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash-race-car.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const List = ({items}) => {
  const listItems = items.map((item, index) => (
    &lt;li key={index}>{item.name}&lt;/li>
  ))

  return (<ul>{listItems}</ul>)
}</code></pre>

    <p>Index as `key` 😢</p>

    <div class="code-highlight" style="height: 70px; top: 190px;"></div>
  </div>
</div>


NOTES:
- This is because it's using "index as key"
- React uses `key` to associate items between render
- When we add a new item to the list, what was previously index 0 is now index 1
- And since new 1 is different than old 1, it updates the DOM
- And continues down the list
- It ends up adding a new element **at the end**

/////
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash-race-car.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const List = ({items}) => {
  const listItems = items.map((item) => (
    &lt;li key={item.id}>{item.name}&lt;/li>
  ))

  return (<ul>{listItems}</ul>)
}</code></pre>

    <p>Unique value as `key` 😄</p>

    <div class="code-highlight" style="height: 70px; top: 190px;"></div>
  </div>
</div>

/////
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash-race-car.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <video data-autoplay loop style="width: 100%">
      <source data-src="../../img/react-perf/unique-value-as-key.mp4" />
    </video>
  </div>
</div>

NOTES:
- As a result, React can optimize better and _just_ add new item to the beginning
- Saves lot of unnecessary DOM manipulations which are slow
- Extrapolate this to a bigger list or bigger an app and it can get sluggish

=====
<!-- .slide: data-background="url(../../img/react-perf/jonathan-chng-751342-unsplash-track-and-field.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>2. HOCs</h1>
  </div>
</div>

NOTES:
**_[11 minutes]_**

- Impact of HOCs in `render()`

/////
<!-- .slide: data-background="url(../../img/react-perf/jonathan-chng-751342-unsplash-track-and-field.jpg) no-repeat center" data-background-size="cover" -->


<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Declaration:</h2>
    <pre class="large"><code class="lang-javascript">const withTitle = (Component) => (
  ({title, ...props}) => (
    <div>
      <h3>{title}</h3>
      &lt;Component {...props} />
    </div>
  )
)</code></pre>

    <h2>Creation:</h2>
    <pre class="large"><code class="lang-javascript">const ListWithTitle = withTitle(List)</code></pre>
  </div>
</div>

NOTES:
- Let's say we had this made up HOC called `withTitle`
- It will enhance the component passed to it to take a `label` prop
  * Wrap the component in a `<div>`
  * Include a `<label>`
- What it does doesn't matter, but how it is used does...

/////
<!-- .slide: data-background="url(../../img/react-perf/jonathan-chng-751342-unsplash-track-and-field.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class Emails extends React.Component {
  render() {
    const ListWithTitle = withTitle(List)
    const {emails} = this.props

    return (
      &lt;section>
        &lt;header> ... &lt;/header>
        &lt;ListWithTitle items={emails} title="Emails" />
        &lt;footer> ... &lt;/footer>
      &lt;/section>
    )
  }
}</code></pre>

    <p>HOC created in `render()` 👎🏾</p>

    <div class="code-highlight" style="height: 70px; top: 195px;"></div>
  </div>
</div>


NOTES:
- Initial thought may be to create the HOC w/in `render()`
- But this has big consequences!
- It's creating a new component time every time `Emails` is re-rendered
  * Even though the have the same name
- As a result, the previous `<ListWithTitle />` keeps completely unmounted
  * And the new one is mounted
- Even worse than index-as-key because the whole UI gets blown away and recreated

/////
<!-- .slide: data-background="url(../../img/react-perf/jonathan-chng-751342-unsplash-track-and-field.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const ListWithTitle = withTitle(List)

class Emails extends React.Component {
  render() {
    const {emails} = props

    return (
      &lt;section>
        &lt;header> ... &lt;/header>
        &lt;ListWithTitle items={emails} title="Emails" />
        &lt;footer> ... &lt;/footer>
      &lt;/section>
    )
  }
}</code></pre>

    <p>Create HOC outside of `render()` 👍🏾</p>

    <div class="code-highlight" style="height: 70px; top: 78px;"></div>
  </div>
</div>

NOTES:
- Instead define the HOC **outside** of render
- There'll only be a single definition of the enhanced component
- Re-renders of `Emails` will work as normal with reconciliation

=====
<!-- .slide: data-background="#222" -->

# Avoiding unnecessary reconciliation
<!-- .element: class="statement" -->

NOTES:
**_[14 minutes]_**

- Reconciliation is React going down the component hierarchy calling `render()` and seeing if any rendered DOM has changed
- Even if nothing in the DOM changes, the reconciliation calculation itself can be costly for large apps
- So after we avoid actually updating the DOM unnecessarily
  * Work on avoiding unnecessary reconciliation
  * These are all super-micro optimizations
  * Don't have to do anything of them
  * But some of them are easy to implement if you're thinking ahead

=====
<!-- .slide: data-background="url(../../img/react-perf/gentrit-sylejmani-723365-unsplash-butterfly-stroke.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>3. `shouldComponentUpdate()`</h1>
  </div>
</div>

NOTES:
**_[15 minutes]_**

- Impact of `shouldComponentUpdate()`

/////
<!-- .slide: data-background="url(../../img/react-perf/gentrit-sylejmani-723365-unsplash-butterfly-stroke.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Default `shouldComponentUpdate()`</h2>
    <pre class="large"><code class="lang-javascript">class DataTable extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return true
  }

  render() {
    // gets called every time props/state update
    // even if they have same values
  }
}</code></pre>
  </div>
</div>

NOTES:
- `shouldComponentUpdate()` allows finer control over reconciliation
- By default it returns `true` which is what `React.Component` does
- And that means reconciliation will happen every time
  * even if the props/state are the exactly the same

/////
<!-- .slide: data-background="url(../../img/react-perf/gentrit-sylejmani-723365-unsplash-butterfly-stroke.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>Shallow compare</h2>
    <pre class="large"><code class="lang-javascript">class DataTable extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    const {props, state} = this
    
    return !shallowEqual(props, nextProps)
      || !shallowEqual(state, nextState)
  }

  render() {
    // only gets called if next props OR state
    // don't shallow equal previous versions
  }
}</code></pre>
  </div>
</div>

NOTES:
- However, if you know that in some situations your component doesn’t need to update
  * you can return `false` to skip `render()`
- In this case we'll `render()` if:
  * next `props` doesn't shallow equal previous props **OR**
  * next `state` doesn't shallow equal previous state
  * Basically when anything changes
- This works as long as you don't mutate objects in `props` or `state`
  * Because the only way to change the data is to create a new version
  * And that won't shallow equal

/////
<!-- .slide: data-background="url(../../img/react-perf/gentrit-sylejmani-723365-unsplash-butterfly-stroke.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class DataTable extends React.PureComponent {
  render() {
    // only gets called if next props OR state
    // don't shallow equal previous versions
  }
}</code></pre>

    <p>Just use `PureComponent` instead!</p>

    <div class="code-highlight" style="height: 70px; top: 82px;"></div>
  </div>
</div>


NOTES:
- But there's really no reason to write that
  * Because that's exactly what `React.PureComponent` does!

/////
<!-- .slide: data-background="url(../../img/react-perf/gentrit-sylejmani-723365-unsplash-butterfly-stroke.jpg) no-repeat center" data-background-size="cover" -->


<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const DataTable = (props) => {
  // gets called every time props update
  // even if it has same values
}</code></pre>

    <p>🚨 Stateless component functions work like<br />`React.Component` 🚨</p>

  </div>
</div>

NOTES:
- FYI - stateless functional components work like `React.Component`
  * Not like `PureComponent`
- There's always been this idea that they'll be optimized
  * But it hasn't happened yet

=====
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>4. Shallow compare</h1>
  </div>
</div>

NOTES:
**_[19 minutes]_**

- Speaking of shallow comparison...
- Impact of negating shallow compare

/////
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class Page extends React.Component {
  render() {
    return (
      &lt;DataTable
        pageSizes={[5, 10, 25, 50]}
        footerInfo={{label: 'Settings'}}
      />
    )
  }
}</code></pre>

    <p>Array & object literals undo shallow compare</p>

  </div>
</div>

NOTES:
- Creating array literals & object literals with every render is cheap
- But if `DataTable` is `PureComponent`...
  * `props.pageSizes` doesn't shallow compare to `nextProps.pageSizes`
  * Even though they do have the same values (deep comparison)

/////
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const PAGE_SIZES = [5, 10, 25, 50]
const FOOTER_INFO = {label: 'Settings'}

class Page extends React.Component {
  render() {
    return (
      &lt;DataTable
        pageSizes={PAGE_SIZES}
        footerInfo={FOOTER_INFO}
      />
    )
  }
}</code></pre>

    <p>Store in constants!</p>

  </div>
</div>


NOTES:
- Instead put those literals in a `const` outside the class
- That way for every render of `Page`
  * passing the same values for `pageSizes` & `footerInfo`
- Now `props.footerInfo` does shallow compare to `nextProps.footerInfo`

/////
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class Page extends React.Component {
  _handleSelect() { ... }
  _handleDelete() { ... }

  render() {
    return (
      &lt;DataTable
        onSelect={(id) => this._handleSelect(id)}
        onDelete={this._handleDelete.bind(this)}
      />
    )
  }
}</code></pre>

    <p>One-off functions undo shallow compare too</p>

  </div>
</div>


NOTES:
- Arrow functions or calling `.bind()` also undoes shallow comparison
  * They create a new function on each `render()`
  * This is so that when the function is called it has the right `this` scope
  * Which will not match the previous value too
- People say that creating these functions every `render()` is poor-performing
  * I think the bigger issue is undoing `PureComponent`
  * Because now the code is...
  * doing the shallow comparison (fails)
  * doing the reconciliation (nothing changes)
  * all unnecessary

/////
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class Page extends React.Component {
  constructor() {
    this._handleSelect = this._handleSelect.bind(this)
  }
  _handleSelect() { ... }
  _handleDelete = () => { ... }
  render() {
    return (
      &lt;DataTable
        onSelect={this._handleSelect}
        onDelete={this._handleDelete}
      />
    )
  }
}</code></pre>

    <p>Pre-bind functions!</p>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 195px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 366px;"></div>
  </div>
</div>


NOTES:
- The fix is to just bind `this` only once
- There are two ways to do this
- **ONE:** Override the method with a bound function property in the `constructor`
  * Not a fan
- **TWO:** Using Stage 3 future JavaScript define a bound arrow function property
- In either case, the function we pass to the handlers will have the correct `this`
  * And we only had to bind one time

/////
<!-- .slide: data-background="url(../../img/react-perf/emma-paillex-543169-unsplash-skiing-downhill.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">class Page extends React.Component {
  render() {
    const {items} = this.props
    const {query} = this.state
    const newItems = items.filter(
      (item) => item.contains(query)
    )

    return (&lt;List items={newItems} />)
  }
}</code></pre>

    <p>Derived data in `render()` doesn't shallow compare</p>

    <div class="code-highlight" style="height: 187px; top: 311px;"></div>
  </div>
</div>

NOTES:
- Derived arrays/objects in `render()` inherently are new each `render()`
- Here we're filtering the `items` in `props` by the `query` in `state`
- There's no simple fix for this
  * Just know that even if `List` was a `PureComponent`
  * And items had the same values
  * It would still `render()` every time because they don't shallow compare
- _May_ be considering making `List` do a *deep*-comparison instead of shallow
  * That would work, and prevent reconciliation
  * But it's likely that the deep comparison would take longer than reconciliation itself

=====
<!-- .slide: data-background="url(../../img/react-perf/markus-spiske-544020-unsplash-cyclists.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>5. `render()`</h1>
  </div>
</div>

NOTES:
**_[24 minutes]_**

- Impact of large `render()`

/////
<!-- .slide: data-background="url(../../img/react-perf/markus-spiske-544020-unsplash-cyclists.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre><code class="lang-javascript">class Page extends React.Component {
  return (
    &lt;main>
      &lt;nav className="nav">
        { /\* 300 lines of left nav markup \*/ }
      &lt;/nav>

      &lt;SearchForm query={this.state.query} onChange={this._handleChange} />

      &lt;section className="data-table">
        { /\* 200 lines of data-table markup \*/ }
      &lt;/section>

      &lt;aside className="pagination">
        { /\* 400 lines of more pagination! \*/ }
      &lt;/aside>
    &lt;/main>
  )
)</code></pre>
    <p>Huge component renders cannot halt reconciliation</p>
  </div>
</div>

NOTES:
- Let's say you have a big component with hundreds of lines in `render()`
  * This is already bad for readability, but let's go with it 😄
- If the `<SearchQuery />` triggers a change which updates `this.state.query`
  * All of `render()` will happen
  * We'll render the hundreds of lines of markup
- Reconciliation will of course figure out nothing has changed and not touched DOM
  * But it's unnecessary reconciliation
- There are no component boundaries to even have a `PureComponent`

/////
<!-- .slide: data-background="url(../../img/react-perf/markus-spiske-544020-unsplash-cyclists.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre><code class="lang-javascript">import DataTable from './DataTable';

class Nav extends React.PureComponent { ... }
class Pagination extends React.PureComponent { ... }

class Page extends React.Component {
  return (
    &lt;main>
      &lt;Nav navItems={NAV_ITEMS} />

      &lt;SearchForm query={this.state.query} onChange={this._handleChange} />

      &lt;DataTable rows={this.props.data} />

      &lt;Pagination theme="blue" />
    &lt;/main>
  )
}</code></pre>
    <p>Leverage helper components to break things up</p>
  </div>
</div>

NOTES:
- By componentizing the markup, create component boundaries
  * The can implement `PureComponent` to stop reconciliation when props don't change
- Also just makes sense to break things up logically
- And you can even put the helper components in the same file so things aren't spread out

=====
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>6. Redux `dispatch()`</h1>
  </div>
</div>

NOTES:
**_[26 minutes]_**

- Impact of multiple `dispatch()` calls
- Leaving the React world

/////
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">_handleMarkUnreadClick = (id) => {
  this.setState({selectedId: id})
  this.setState({color: 'blue'})
}</code></pre>

    <p>Multiple `setState()` calls are ok</p>
  </div>
</div>


NOTES:
- Because `setState()` is asynchronous calling it multiple times sequentially is ok
  * The state will actually only get updated once
  * `render()` will only be called once

/////
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const setSelected = (id) => ({type: 'SET_SELECTED', payload: id})
const setColor = (color) => ({type: 'SET_COLOR', payload: color})

export const markUnread = (id) => (
  (dispatch) => {
    dispatch(setSelected(id))
    dispatch(setColor('blue'))
  }
)</code></pre>

    <p>Multiple `dispatch()` calls cause multiple `render()`!</p>
  </div>
</div>


NOTES:
- However this isn't the case with multiple Redux `dispatch()` calls
- Let's say you're using `redux-thunk` and you have an action
  * Needs to update two parts of your Redux store
  * Maybe already have existing separate actions that do this
  * So you may make two `dispatch()` calls

/////
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const selectedId = (state = -1, action) => {
  if (action.type === 'SET_SELECTED') {
    state = action.payload
  }
  return state
}

const color = (state = null, action) => {
  if (action.type === 'SET_COLOR') {
    state = action.payload
  }
  return state
}</code></pre>

    <p>1-to-1 action-to-reducer</p>
  </div>
</div>

NOTES:
- Two actions for the two reducers responsible for that state
- The problem is that you'll cause two `render()` for every "connected" component!
- The first one generates new state with `selectedId` updated
- The next generates new state with `color` updated
  * The first one is wasted because eye will never see it
  * But will cause sluggishness
- If you connect at the top level app, the whole app renders doubly!

/////
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const setSelected = (id) => ({type: 'SET_SELECTED', payload: id})
const setColor = (color) => ({type: 'SET_COLOR', payload: color})

export const markUnread = (id) => ({
  type: 'MARK_UNREAD',
  payload: {id, color: 'blue'},
})</code></pre>

    <p>Combine `dispatch()` calls using single action</p>
  </div>
</div>


NOTES:
- Instead have a single action that passes all the data needed
- `MARK_UNREAD` action combines `payload` for `SET_SELECTED` & `SET_COLOR`

/////
<!-- .slide: data-background="url(../../img/react-perf/san-fermin-pamplona-navarra-768233-unsplash-running-of-the-bulls.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const selectedId = (state = -1, action) => {
  if (action.type === 'MARK_UNREAD') {
    state = action.payload.id
  }
  return state
}

const color = (state = null, action) => {
  if (action.type === 'MARK_UNREAD') {
    state = action.payload.color
  }
  return state
}</code></pre>

    <p>1-to-many action-to-reducers</p>
  </div>
</div>


NOTES:
- The two reducers can listen to the single action
  * pull off the necessary data from the `payload`
- Only updating the state tree once
  * Both pieces of state get updated at the same time
- Only one re-render happens

=====
<!-- .slide: data-background="#222" -->

# Avoiding unnecessary calculations
<!-- .element: class="statement" -->

NOTES:
**_[31 minutes]_**

- At this point, getting to just normal JavaScript code
- Probably won't matter unless you're building a DNA design tool, a rich-text editor, full-feature spreadsheet app, etc
- These calculations could be the code to determine whether or not to prevent reconciliation
  * If you have really complex calculations to prevent reconciliation
  * It’s probably better to just let reconciliation happen
- Could also be code to calculate new state

=====
<!-- .slide: data-background="url(../../img/react-perf/gene-devine-430971-unsplash-horse-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>7. Copying objects</h1>
  </div>
</div>

NOTES:
**_[32 minutes]_**

- Impact of copying objects/arrays

/////
<!-- .slide: data-background="url(../../img/react-perf/gene-devine-430971-unsplash-horse-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">export const emails = (state = [], action) => {
  if (action.type === 'DELETE_EMAIL') {
    state = state.filter(email => email.id !== action.payload);
  } else if (action.type === 'ADD_EMAIL') {
    state = [action.payload, ...state]
  } else if (action.type === 'UPDATE_EMAIL') {
    state = state.map(email => email.id === action.payload.id ? 
      {...email, ...action.payload.email} : 
      email
    )
  }

  return state;
}</code></pre>

    <p>Copying large objects/arrays can be expensive</p>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 196px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 309px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 240px; top: 429px;"></div>
  </div>
</div>

NOTES:
- Even if you optimize the DOM with "windowing"
- Copying the underlying large array or object data can be expsensive
  * We copy instead of mutating objects in order to keep things immutable
  * This is how `PureComponent` is able to work 
  * If data changes it's a new object
  * But it comes at a cost
- **ONE:** To delete an email we use `.filter()`
  * Keep email as long as it does **not** match ID of payload
  * As we learned earlier this makes a brand new shallow copy of array
  * If the array is huge, this takes time
- **TWO:** To add an email to the beginning use spread operator
  * This also makes a copy adding new to the beginning
  * Again if array is huge, this takes time
- **THREE** to update an email we use `.map()`
  * This also makes a copy
  * But for the matching email we use spread operator for objects
  * This makes a copy of the object as well to add in new data
  * If email has a lot of data or array is huge, takes time

/////
<!-- .slide: data-background="url(../../img/react-perf/gene-devine-430971-unsplash-horse-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay" style="width: 70%">
    <div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
      <div style="flex:0 0 45%;">
          <a href="https://facebook.github.io/immutable-js/"><img
              src="../../img/nav-react/immutable-logo.png"
              style="background:none;box-shadow:none;border:none;width:100%"
          /></a>
        </div>
        <div style="flex:0 0 45%;">
          <a href="https://github.com/rtfeldman/seamless-immutable">`seamless-immutable`</a>
        </div>
    </div>
    <p>Use immutable data structures</p>
  </div>
</div>


NOTES:
- Again, copying arrays and objects usually isn't a big deal
- But for large amounts of data it can be expensive
- So you can leverage some immutable data structures
  * Make maintaining immutability more efficient
- You can use a library like `Immutable` or `seamless-immutable` to have true immutable objects
- `Immutable` is the big player, yet another library from Facebook
  * Only used it a bit
  * Found the API a bit cumbersome
  * Constantly going to and from Immutable and native objects
  * Don't _really_ want my React components to have to care, just Redux


/////
<!-- .slide: data-background="url(../../img/react-perf/gene-devine-430971-unsplash-horse-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h2>`seamless-immutable`</h2>
    <pre class="large"><code class="lang-javascript">const array = Immutable(['one', 'two', {count: 3}])

array[1] = 'I will mutate you!'
console.log(array[1]) // 'two'

array[2].count = 'Mutate an object mwahaha!!!'
console.log(array[2].count) // 3

console.log(JSON.stringify(array))
// '["one","two",{"count":3}]'</code></pre>
  </div>
</div>


NOTES:
- `seamless-immutable` is an alternative that has data structures that are backwards-compatible
  * They work just like Arrays or Objects except they don't mutate and have extra functionality
  * A lot lighter than Immutable
- Can pass to libraries like `lodash` or `underscore`

=====
<!-- .slide: data-background="url(../../img/react-perf/joe-neric-223562-unsplash-motorcycle-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>8. Derived Redux state</h1>
  </div>
</div>

NOTES:
**_[35 minutes]_**

- Impact of recomputing Redux derived state

/////
<!-- .slide: data-background="url(../../img/react-perf/joe-neric-223562-unsplash-motorcycle-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">const getVisibleTodos = (todos, filter) => {
  // filters \`todos\` array by \`filter\` string
}
const mapStateToProps = (state) => ({
  todos: getVisibleTodos(state.todos, state.filter)
})

export default connect(mapStateToProps)(TodoList)</code></pre>

    <p>Recalculating derived data can be expensive</p>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 485px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 307px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 195px; top: 77px;"></div>
  </div>
</div>


NOTES:
- **ONE:** Here's a traditional `connect()` from `react-redux`
- **TWO:** It's got a `mapStateToProps` which calls `getVisibleTodos`
  * Derives a visible set of todos based on the full list and a filter
- This is works great, but one thing to know is that this gets called **anytime** the state tree updates
  * So even if some other piece of state updates, this code will get called
  * The bigger the state tree, the more likely this will get unnecessarily called
- **THREE:** Futhermore, if the calculation of `getVisibleTodos` is expensive
  * Because we're copying arrays like we just talked about
  * We're making unnecessary + expensive calls
- And to make matters _even_ worse
  * Because we're copying, shallow compare will fail even though the data's the same
  * So reconciliation will happen down the component tree even though nothing's changed
- It's like THREE compounding errors

/////
<!-- .slide: data-background="url(../../img/react-perf/joe-neric-223562-unsplash-motorcycle-racing.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <pre class="large"><code class="lang-javascript">import {createSelector} from 'reselect';

const getTodos = (state) => state.todos
const getVisibilityFilter = (state) => state.filter

const getVisibleTodos = createSelector(
  [getTodos, getVisibilityFilter],
  (todos, filter) => {
    // filters \`todos\` array by \`filter\` string
  }
)
const mapStateToProps = (state) => ({
  todos: getVisibleTodos(state)
})</code></pre>

    <p>Use a "memoized" selector</p>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 367px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 426px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 131px; top: 193px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 191px; top: 475px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 766px;"></div>
  </div>
</div>

NOTES:
- What we need is what's called a "memoized selector"
  * Cache the results,
  * If the inputs don't change, nothing is recalculated
- **ONE:** Use a function from `reselect` called `createSelector` to create memoized selector
- **TWO:** It takes an array of "input-selectors" as first param
- **THREE:** `getTodos` & `getVisibilityFilter`
  * They are simple functions that retrieve properties off of `state`
- **FOUR:** Then the second parameter is the transformation function that generates derived data
- **FIVE:** And `getVisibleTodos` is called passing in `state`
  * Will return the derived visible todos
  * But will be cached if calculated before
- Benefit of the cache is:
  - Save on unnecessary calculation
  - Save on unnecessary data copying
  - Save on unnecessary reconciliation cuz object is the same

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Quick Recap</h1>
  </div>
</div>

NOTES:
**_[37 minutes]_**

- All these can help your app run faster
- But don't prematurely optimize!
- React is already super fast
- Go and build things!!!

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    1. Use unique value as `key`
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">const listItems = items.map((item) => (
  &lt;li key={item.id}>{item.name}&lt;/li>
))</code></pre>

    2. Create HOCs outside of `render()`
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">const ListWithTitle = withTitle(List)

class Emails extends React.Component { ... }</code></pre>

    3. Use `PureComponent` for shallow compare
    <pre class="large"><code class="lang-javascript">class DataTable extends React.PureComponent { ... }</code></pre>
  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    4. Avoid undoing shallow compare
    <pre class="large"><code class="lang-javascript">const PAGE_SIZES = [5, 10, 25, 50]

class Page extends React.Component {
  _handleSelect = () => { ... }
  render() {
    return (
      &lt;DataTable
        pageSizes={PAGE_SIZES}
        onSelect={this._handleSelect}
      />
    )
  }
}</code></pre>
  </div>
</div>

NOTES:
- Avoid undoing shallow compare by storing object constants outside and pre-binding functions

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    5. Break up component markup
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">const Page = (props) => (
  &lt;main>
    &lt;Nav navItems={NAV_ITEMS} />
    &lt;DataTable rows={props.data} />
    &lt;Pagination theme="blue" />
  &lt;/main>
)</code></pre>

    6. Combine Redux `dispatch()` calls
    <pre class="large"><code class="lang-javascript">export const markUnread = (id) => ({
  type: 'MARK_UNREAD',
  payload: {id, color: 'blue'},
})</code></pre>
  </div>
</div>

NOTES:
- Break up component markup into helper components so that reconciliation can be prematurely halted
- Combine multiple `dispatch()` calls into one to prevent multiple state updates

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    7. Use immutable data structures
    <pre class="large" style="margin-bottom: 1em"><code class="lang-javascript">const array = Immutable(['one', 'two', {count: 3}])

array[1] = 'I will mutate you!'
console.log(array[1]) // 'two'</code></pre>

    8. Use memoized Redux selectors
    <pre class="large"><code class="lang-javascript">const getVisibleTodos = createSelector(
  [getTodos, getVisibilityFilter],
  (todos, filter) => { ... }
)</code></pre>
  </div>
</div>

NOTES:
- Immutable data structures will reduce the copying of data structures
- Using memoized selectors will help reduce unnecessary recomputation of derived data

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 50%">
    <h2>tl;dr</h2>
    <ol>
      <li>Use unique value as `key`</li>
      <li>Create HOCs outside of `render()`</li>
      <li>Use `PureComponent` for shallow compare</li>
      <li>Avoid undoing shallow compare</li>
      <li>Break up component markup</li>
      <li>Combine Redux `dispatch()` calls</li>
      <li>Use immutable data structures</li>
      <li>Use memoized Redux selectors</li>
    </ol>

  </div>
</div>

=====
<!-- .slide: data-background="url(../../img/esnext/anna-demianenko-12400-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 52%" class="content-overlay">
  
    <h1>Resources</h1>

    <ul style="margin-top: 1em">
      <li><a href="https://bvaughn.github.io/react-virtualized/" target="_blank">"Windowing" with <code>react-virtualized</code></a></li>
      <li><a href="https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad" target="_blank">Debugging React Performance with React 16...</a></li>
      <li><a href="https://reactjs.org/docs/optimizing-performance.html" target="_blank">Optimizing Performance</a></li>
      <li><a href="https://evilmartians.com/chronicles/optimizing-react-virtual-dom-explained" target="_blank">Optimizing React: Virtual DOM explained</a></li>
      <li><a href="https://egghead.io/lessons/react-use-the-new-profiler-in-react-developer-tools-to-generate-flame-charts-and-interactions" target="_blank">Use New Profiler in React Dev Tools</a> 📺</li>
    </ul>
  
  </div>
</div>

NOTES:
**_[40 minutes]_**

- Lots of resources for you
- The first one is a library for "windowing"
  * Only displaying a subset of a list to limit DOM nodes
- Didn't have time to discuss how to debug performance issues
  * These articles discuss this in details
- My favorite one is running Chrome 4x slower to expose issues

/////
<!-- .slide: data-background="url(../../img/esnext/anna-demianenko-12400-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div class="content-overlay">
    <video data-autoplay loop style="width: 100%">
      <source data-src="../../img/react-perf/elijah-manor-using-new-profiler.mp4" />
    </video>

    <p>
      <a href="https://egghead.io/lessons/react-use-the-new-profiler-in-react-developer-tools-to-generate-flame-charts-and-interactions" target="_blank">Use the New Profiler in React Developer Tools</a><br />
      by <a href="https://twitter.com/elijahmanor/status/1038057481057050624" target="_blank">Elijah Manor</a>
    </p>
  </div>
</div>

NOTES:
- Elijah Manor has an Egghead lesson on using the new profiler enabled with React 16.5.0
  * Can generate flame charts
  * Brian Vaughn has been doing a lot of work in this area
  * This just landed last week!

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
- Hopefully 1, 2 or all 8 of these suggestions will prove useful to you
  * But again, do not prematurely optimize
  * Some suggestions you can just do while building
  * But most of them make sense to build first, optimize later
- Ask questions on Twitter, via email or AMA!
- Wanna thank **conference** and **YOU!**
- Thanks!
