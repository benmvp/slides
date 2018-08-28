<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="overlay-light">
  
  <h1>Help! My React app is slowwwww! 🐢</h1>

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

# React Reconciliation

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
  <div class="overlay-light">
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

/////
<!-- .slide: data-background="#000" -->

![Eventbrite logo](../../img/eventbrite/wordmark-white.png)
<!-- .element: class="plain" -->

![Eventbrite logo](../../img/eventbrite/orange-ticketea.png)
<!-- .element: class="plain fragment" style="width: 40%" -->

NOTES: 
- I'm a Principal Frontend Engineer at Eventbrite
- Work on our Frontend Platform team
  * Doing FE infra + design system work
- **ONE:** Recently added Ticketea to the family

/////
<!-- .slide: data-background="#000 url(../../img/bball/gasol-brothers.jpg) no-repeat center" data-background-size="contain" -->

NOTES:
- I love basketball; playing and watching
- My favorite team is the Houston Rockets
- But since I'm in Spain, giving love to the hometown guys

=====

# Use production builds

## Size before:
## Size after:

NOTES:
- Let's just get this one out of the way
- Use `NODE_ENV=production` + uglify
- Because `PropType` & other helpful warnings in DEV
- Also decreases the bundle size

/////

React dev tools icon

NOTES:
- Can tell whether your app is running in Production mode with React Dev Tools icon

=====

# Avoiding unnecessary DOM updates

NOTES:
- Touching the DOM is the most expensive thing we can do!

=====

## 1. Impact of `key`

=====

## 2. Impact of HOCs in `render()`

=====

## 3. Impact of lots of data

=====

# Avoiding unnecessary reconciliation

NOTES:
- Reconciliation is React going down the component hierarchy calling `render()` and seeing if any rendered DOM has changed
- Even if nothing in the DOM changes, the reconciliation calculation itself can be costly for large apps

=====

## 4. Impact of `shouldComponentUpdate()`

=====

## 5. Impacts of negating shallow comparison

=====

## 6. Impact of big `render()`

=====

## 7. Impact of multiple `setState()` calls

=====

# Avoid unnecessary calculations

NOTES:
- At this point, getting to just normal JavaScript code
- Probably won't matter unless you're building a DNA design tool, a rich-text editor, full-feature spreadsheet app, etc
- These calculations Could be the code to determine whether or not to prevent reconciliation
  * It’s just better to just let reconciliation happen
- Could just be code to calculate new state

=====

## 8. Impact of copying objects/arrays via spread

=====

## 9. Impact of recomputing derived state

=====

# Debugging tools

=====

# Recap

NOTES:
- All these can help your app run faster
- But don't prematurely optimize!
- Go and build things!

=====

# Resources

- [Optimizing Performance](https://reactjs.org/docs/optimizing-performance.html)
- [Performance Tools](https://reactjs.org/docs/perf.html)
- [Debugging React Performance with React 16 and Chrome Devtools](https://building.calibreapp.com/debugging-react-performance-with-react-16-and-chrome-devtools-c90698a522ad)
- [Optimizing React: Virtual DOM explained](https://evilmartians.com/chronicles/optimizing-react-virtual-dom-explained)

=====
<!-- .slide: data-background="url(../../img/webdev/matt-jones-42954-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-start">
	<div style="width: 40%" class="overlay-light">
  
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
