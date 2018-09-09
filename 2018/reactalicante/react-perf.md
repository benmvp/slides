<!-- .slide: data-background="url(../../img/react-perf/react-alicante-title-slide.jpg) no-repeat center" data-background-size="cover" -->

/////

<!-- .slide: data-background="url(../../img/react-perf/react-alicante-sponsor-slide.jpg) no-repeat center" data-background-size="cover" -->

/////

<!-- .slide: data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="content-overlay">
  
  <h1>Help!<br />My React app is slowwwww! 🐢</h1>

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
<!-- .slide: data-background="url(../../img/react-perf/george-brynzan-720804-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1 style="font-size: 4em">React<br />Reconciliation</h1>
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
<!-- .slide: data-background="#000 url(../../img/family-naima-wedding.png) no-repeat center" data-background-size="contain" -->

NOTES:
- Christian, Husband, Father
- I'm learning Español so would love to talk with you in Spanish

/////
<!-- .slide: data-background="#000" -->

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
<!-- .slide: data-background="#000" -->

# Avoiding unnecessary DOM updates
<!-- .element: class="statement" -->

NOTES:
- Touching the DOM is the most expensive thing we can do!

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 1. Impact of `key`

/////

<video data-autoplay loop style="width: 100%">
  <source data-src="../../img/react-perf/index-as-key.mp4" />
</video>

NOTES:
- Here's very simple example of a list
- And as we add something to the beginning of the list
- All of the elements are getting updated

/////

index as key 😢

```js
const List = ({items}) => {
  const listItems = items.map((item, index) => (
    <li key={index}>{item.name}</li>
  ))

  return (<ul>{listItems}</ul>)
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 247px;"></div>


NOTES:
- This is because it's using "index as key"
- React uses `key` to associate items between render
- When we add a new item to the list, what was previously index 0 is now index 1
- And since new 1 is different than old 1, it updates the DOM
- And continues down the list
- It ends up adding a new element **at the end**

/////

Unique value as key 😄

```js
const List = ({items}) => {
  const listItems = items.map((item) => (
    <li key={item.id}>{item.name}</li>
  ))

  return (<ul>{listItems}</ul>)
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 247px;"></div>

/////

<video data-autoplay loop style="width: 100%">
  <source data-src="../../img/react-perf/unique-value-as-key.mp4" />
</video>

NOTES:
- As a result, React can optimize better and _just_ add new item to the beginning
- Saves lot of unnecessary DOM manipulations which are slow
- Extrapolate this to a bigger list or bigger an app and it can get sluggish

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 2. Impact of HOCs in `render()`

NOTES:

/////

Definition:
```js
const withTitle = (Component) => (
  ({title, ...props}) => (
    <div>
      <h3>{title}</h3>
      <Component {...props} />
    </div>
  )
)
```
<!-- .element: class="large" -->

Creation:
```js
const ListWithTitle = withTitle(List)
```
<!-- .element: class="large" -->

NOTES:
- Let's say we had this made up HOC called `withTitle`
- It will enhance the component passed to it to take a `label` prop
  * Wrap the component in a `<div>`
  * Include a `<label>`
- What it does doesn't matter, but how it is used does...

/////

HOC created in `render()` 👎🏾

```js
class Emails extends React.Component {
  render() {
    const ListWithTitle = withTitle(List)
    const {emails} = this.props

    return (
      <section>
        <header> ... </header>
        <ListWithTitle items={emails} title="Your Emails" />
        <footer> ... </footer>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 247px;"></div>

NOTES:
- Initial thought may be to create the HOC w/in `render()`
- But this has big consequences!
- It's creating a new component time every time `Emails` is re-rendered
  * Even though the have the same name
- As a result, the previous `<ListWithTitle />` keeps completely unmounted
  * And the new one is mounted
- Even worse than index-as-key because the whole UI gets blown away and recreated

/////

Create HOC outside of `render()` 👍🏾

```js
const ListWithTitle = withTitle(List)

class Emails extends React.Component {
  render() {
    const {emails} = props

    return (
      <section>
        <header> ... </header>
        <ListWithTitle items={emails} title="Your Emails" />
        <footer> ... </footer>
      </section>
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 132px;"></div>

NOTES:
- Instead define the HOC **outside** of render
- There'll only be a single definition of the enhanced component
- Re-renders of `Emails` will work as normal with reconciliation

=====
<!-- .slide: data-background="#000" -->

# Avoiding unnecessary reconciliation
<!-- .element: class="statement" -->

NOTES:
- Reconciliation is React going down the component hierarchy calling `render()` and seeing if any rendered DOM has changed
- Even if nothing in the DOM changes, the reconciliation calculation itself can be costly for large apps
- So after we avoid actually updating the DOM unnecessarily
  * Work on avoiding unnecessary reconciliation
  * These are all super-micro optimizations
  * Don't have to do anything of them
  * But some of them are easy to implement if you're thinking ahead

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 3. Impact of `shouldComponentUpdate()`

/////

Default `shouldComponentUpdate()`

```js
class DataTable extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return true;
  }

  render() {
    // gets called every time props/state update
    // even if they have same values
  }
}
```
<!-- .element: class="large" -->

NOTES:
- `shouldComponentUpdate()` allows finer control over reconciliation
- By default it returns `true` which is what `React.Component` does
- And that means reconciliation will happen every time
  * even if the props/state are the exactly the same

/////

Shallow compare in `shouldComponentUpdate()`

```js
class DataTable extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    const {props, state} = this
    
    return !shallowEqual(props, nextProps)
      || !shallowEqual(state, nextState)
  }

  render() {
    // only gets called if next props OR state
    // don't shallow equal previous versions
  }
}
```
<!-- .element: class="large" -->

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

Use `PureComponent` instead!

```js
class DataTable extends React.PureComponent {
  render() {
    // only gets called if next props OR state
    // don't shallow equal previous versions
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 132px;"></div>

NOTES:
- But there's really no reason to write that
  * Because that's exactly what `React.PureComponent` does!

/////

🚨 Stateless functional components work like `React.Component` 🚨

```js
const DataTable = (props) => {
  // gets called every time props update
  // even if it has same values
}
```
<!-- .element: class="large" -->

NOTES:
- FYI - stateless functional components work like `React.Component`
  * Not like `PureComponent`
- There's always been this idea that they'll be optimized
  * But it hasn't happened yet

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 4. Impact of negating shallow comparison

/////

Array & object literals undo shallow compare

```js
class Page extends React.Component {
  render() {
    return (
      <DataTable
        pageSizes={[5, 10, 25, 50]}
        footerInfo={{label: 'Settings'}}
      />
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Creating array literals & object literals with every render is cheap
- But if `DataTable` is `PureComponent`...
  * `props.pageSizes` doesn't shallow compare to `nextProps.pageSizes`
  * Even though they do have the same values (deep comparison)

/////

Store in constants!

```js
const PAGE_SIZES = [5, 10, 25, 50]
const FOOTER_INFO = {label: 'Settings'}

class Page extends React.Component {
  render() {
    return (
      <DataTable
        pageSizes={PAGE_SIZES}
        footerInfo={FOOTER_INFO}
      />
    )
  }
}
```
<!-- .element: class="large" -->

NOTES:
- Instead put those literals in a `const` outside the class
- That way for every render of `Page`
  * passing the same values for `pageSizes` & `footerInfo`
- Now `props.footerInfo` does shallow compare to `nextProps.footerInfo`

/////

One-off functions undo shallow compare too

```js
class Page extends React.Component {
  _handleItemSelect() { ... }
  _handleItemDelete() { ... }

  render() {
    return (
      <DataTable
        onItemSelect={(id) => this._handleItemSelect(id)}
        onItemDelete={this._handleItemDelete.bind(this)}
      />
    )
  }
}
```
<!-- .element: class="large" -->

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

Pre-bind functions!

```js
class Page extends React.Component {
  constructor() {
    this._handleItemSelect = this._handleItemSelect.bind(this)
  }
  _handleItemSelect() { ... }
  _handleItemDelete = () => { ... }

  render() {
    return (
      <DataTable
        onItemSelect={this._handleItemSelect}
        onItemDelete={this._handleItemDelete}
      />
    )
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 246px;"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 420px;"></div>

NOTES:
- The fix is to just bind `this` only once
- There are two ways to do this
- **ONE:** Override the method with a bound function property in the `constructor`
- **TWO:** Using Stage 3 future JavaScript define a bound arrow function property
- In either case, the function we pass to the handlers will have the correct `this`
  * And we only had to bind one time

/////

Derived data in `render()` doesn't shallow compare

```js
class Page extends React.Component {
  render() {
    const {items} = this.props
    const {query} = this.state
    const newItems = items.filter((item) => item.contains(query))

    return (<List items={newItems} />)
  }
}
```
<!-- .element: class="large" -->

<div class="code-highlight" style="height: 70px; top: 363px;"></div>

NOTES:
- Derived arrays/objects in `render()` inherently are new each `render()`
- Here we're filtering the `items` in `props` by the `query` in `state`
- There's no simple fix for this
  * Just know that even if `List` was a `PureComponent`
  * And items had the same values
  * It would still `render()` every time because they don't shallow compare
- May be considering making `List` do a *deep*-comparison instead of shallow
  * That would work, and prevent reconciliation
  * But it's likely that the deep comparison would take longer than reconciliation itself

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 5. Impact of big `render()`

/////

Huge component renders cannot break reconciliation

```js
class Page extends React.Component {
  return (
    <main>
      <nav className="nav">
        { /* 300 lines of left nav markup */ }
      <nav>

      <SearchForm query={this.state.query} onChange={this._handleSearchChange} />

      <section className="data-table">
        { /* 200 lines of data-table markup */ }
      </section>

      <aside className="stuff">
        { /* 400 lines of more stuff! */ }
      </aside>
    </main>
  );
)
```

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

Leverage helper components to break things up

```js
import DataTable from './DataTable';

class Nav extends React.PureComponent { ... }
class Stuff extends React.PureComponent { ... }

class Page extends React.Component {
  return (
    <main>
      <Nav navItems={NAV_ITEMS} />

      <SearchForm query={this.state.query} onChange={this._handleSearchChange} />

      <DataTable rows={this.props.data} />

      <Stuff type="blue" />
    </main>
  );
)
```

NOTES:
- By componentizing the markup, create component boundaries
  * The can implement `PureComponent` to stop reconciliation when props don't change
- Also just makes sense to break things up logically
- And you can even put the helper components in the same file so things aren't spread out

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 6. Impact of multiple `dispatch()` calls

/////

Multiple `setState()` calls are ok

```js
_handleClick = (id) => {
  this.setState({selectedId: id});
  this.setState({color: 'blue'})
}
```
<!-- .element: class="large" -->

NOTES:
- Because `setState()` is asynchronous calling it multiple times sequentially is ok
  * The state will actually only get updated once
  * `render()` will only be called once

/////

Multiple `dispatch()` calls causes multiple `render()`

```js
const setSelected = (id) => ({type: 'SET_SELECTED', payload: id})
const setColor = (color) => {{type: 'SET_COLOR', payload: color})

export const markUnread = (id) => (
  (dispatch) => {
    dispatch(setSelected(id))
    dispatch(setColor('blue'))
  }
)
```
<!-- .element: class="large" -->

NOTES:
- However this isn't the case with multiple Redux `dispatch()` calls
- Let's say you're using `redux-thunk` and you have an action
  * Needs to update two parts of your Redux store
  * Maybe already have existing separate actions that do this
  * So you may make two `dispatch()` calls

/////

1-to-1 action-to-reducer

```js
const selectedId = (state = -1, action) => {
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
}
```
<!-- .element: class="large" -->

NOTES:
- Two actions for the two reducers responsible for that state
- The problem is that you'll cause two `render()` for every "connected" component!
- The first one generates new state with `selectedId` updated
- The next generates new state with `color` updated
  * The first one is wasted because eye will never see it
  * But will cause sluggishness
- If you connect at the top level app, the whole app renders doubly!

/////

Combine `dispatch()` calls using single action

```js
const setSelected = (id) => ({type: 'SET_SELECTED', payload: id})
const setColor = (color) => {{type: 'SET_COLOR', payload: color})

export const markUnread = (id) => ({
  type: 'MARK_UNREAD',
  payload: {id, color: 'blue'},
})
```
<!-- .element: class="large" -->

NOTES:
- Instead have a single action that passes all the data needed
- `MARK_UNREAD` action combines `payload` for `SET_SELECTED` & `SET_COLOR`

/////

1-to-many action-to-reducers

```js
const selectedId = (state = -1, action) => {
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
}
```
<!-- .element: class="large" -->

NOTES:
- The two reducers can listen to the single action
  * pull off the necessary data from the `payload`
- Only updating the state tree once
  * Both pieces of state get updated at the same time
- Only one re-render happens

=====
<!-- .slide: data-background="#000" -->

# Avoiding unnecessary calculations
<!-- .element: class="statement" -->

NOTES:
- At this point, getting to just normal JavaScript code
- Probably won't matter unless you're building a DNA design tool, a rich-text editor, full-feature spreadsheet app, etc
- These calculations could be the code to determine whether or not to prevent reconciliation
  * If you have really complex calculations to prevent reconciliation
  * It’s probably better to just let reconciliation happen
- Could also be code to calculate new state

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 7. Impact of copying objects/arrays

/////

Copying large objects/arrays can be expensive

```js
export const emails = (state = [], action) => {
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
}
```
<!-- .element: class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 248px;"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 361px;"></div>
<div class="code-highlight fragment current-visible" style="height: 240px; top: 481px;"></div>

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

Use immutable data structures

<div style="display:flex;align-items:center;justify-content:space-around;margin-top:5%">
	<div style="flex:0 0 45%;">
        <a href="https://facebook.github.io/immutable-js/"><img
            src="../../img/nav-react/immutable-logo.png"
            style="background:none;box-shadow:none;border:none;width:100%"
        /></a>
    </div>
    <div style="flex:0 0 45%;">
		<a href="https://github.com/rtfeldman/seamless-immutable"><code>seamless-immutable</code></a>
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

## `seamless-immutable`

```js
let array = Immutable(['totally', 'immutable', {hammer: 'no!'}])

array[1] = `I'm going to mutate you!`
console.log(array[1]) // "immutable"

array[2].hammer = 'hm, surely I can mutate this nested object...'
console.log(array[2].hammer) // "no!"

console.log(JSON.stringify(array))
// '["totally", "immutable", {"hammer":"no!"}]'
```
<!-- .element class="large" -->

NOTES:
- `seamless-immutable` is an alternative that has data structures that are backwards-compatible
  * They work just like Arrays or Objects except they don't mutate and have extra functionality
  * A lot lighter than Immutable
- Can pass to libraries like `lodash` or `underscore`

=====
<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

## 8. Impact of recomputing derived Redux state

/////

Recalculating derived data can be expensive

```js
const getVisibleTodos = (todos, filter) => {
  // filters `todos` array by `filter` string
}
const mapStateToProps = (state) => ({
  todos: getVisibleTodos(state.todos, state.visibilityFilter)
})

export default connect(mapStateToProps)(TodoList)
```
<!-- .element class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 533px;"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 361px;"></div>
<div class="code-highlight fragment current-visible" style="height: 195px; top: 131px;"></div>

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

Use a memoized selector

```js
import {createSelector} from 'reselect';

const getTodos = (state) => state.todos
const getVisibilityFilter = (state) => state.visibilityFilter

const getVisibleTodos = createSelector(
  [getTodos, getVisibilityFilter],
  (todos, filter) => {
    // filters `todos` array by `filter` string
  }
)
const mapStateToProps = (state) => ({
  todos: getVisibleTodos(state)
})
```
<!-- .element class="large" -->

<div class="code-highlight fragment current-visible" style="height: 70px; top: 421px;"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 480px;"></div>
<div class="code-highlight fragment current-visible" style="height: 131px; top: 247px;"></div>
<div class="code-highlight fragment current-visible" style="height: 191px; top: 529px;"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 820px;"></div>

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

# Quick Recap

1. Use unique value as `key`
1. Create HOCs outside of `render()`
1. Use `PureComponent` for shallow compare
1. Avoid undoing shallow compare
1. Break up component markup
1. Combine `dispatch()`
1. Use immutable data structures
1. Use memoized selectors

NOTES:
- All these can help your app run faster
- But don't prematurely optimize!
- Go and build things!!!

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
  </ul>
  
  
  </div>
</div>

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
- I hope you enjoyed our ride in the wayback machine
  * Hopefully it gives us all appreciation for where we've come from
  * Next time we wanna complain about the current situation
- Ask questions on Twitter, via email or AMA!
- Wanna thank **conference** and **YOU!**
- Thanks!
