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
**RESTART THE TIMER!!!!**

-

- **Slides are available online**

**RESTART THE TIMER!!!!**

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
  // ...
  return (
    &lt;section>
      &lt;h1>All Players&lt;/h1>
      &lt;Slideshow
        images={playerImages}
        page={2}
        onNextPage={ ... }
      />
    &lt;/section>
  )
}</code></pre>
      </div>
      <div style="flex:0 0 45%; margin-left: 20px;">
        <pre class="large"><code class="lang-javascript">const Teams = () => {
  // ...
  return (
    &lt;section>
      &lt;h1>All Teams&lt;/h1>
      &lt;Slideshow
        images={teamLogos}
        page={5}
        onNextPage={ ... }
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
- React is great at sharing UI
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

    <pre class="large"><code class="lang-javascript">const Players = ({ teamId }) => {
  // maintain state of paginated player images

  useEffect(() => {
    const getPlayersAsync = async () => {
      const data = getPlayers(teamId, curPage)
      const images = getImages(data)

      // update state of paginated player images
    }
    getPlayersAsync()
  }, [teamId, curPage])

  // render UI of paginated player images
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

    <pre class="large"><code class="lang-javascript">const useImages = ({ teamId }) => {
  // maintain state of paginated images

  useEffect(() => {
    const getPlayersAsync = async () => {
      const data = getPlayers(teamId, curPage)
      const images = getImages(data)

      // update state of paginated images
    }
    getPlayersAsync()
  }, [teamId, curPage])

  // return paginated images & page updater
}</code></pre>
  </div>
</div>

NOTES:
- But the tricky part is the non-visual logic
  * More or less the combination of state + logic
- Want to be able to re-use the code around
  * Maintaining the current page
  * Calling the API when the current page changes
  * Getting the images from response
  * Maintaining the list of those images
- That way I could render the paginated player images as...
  * A slideshow like before
  * A grid view
  * A list view
- I've kinda given away the answer by showing you the custom hooks way
  * But wanna take us on a journey of how we've tried to solve this problem
  * Before hooks came to save us

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
  * Take the effort out of shopping by providing a selection of clothes picked just for you
  * And sent to your door on a frequency that you choose
- We're hiring!
  * Headquarters is in SF
  * But we have remote engineers all over the country

=====

# Mixins

=====

# Higher-order components (HOCs)

=====

# Render props

=====

# Custom Hooks

=====
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
    </ul>
  </div>
</div>

NOTES:


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
- One of them is called "TypeScript for React Developers"
  * So if you're interested in hands-on learning of using TS + React you should check it out
  * As well as the others listed
- I'm doing a free giveaway for conference attendees
  * Go to my site (benmvp.com) and check out the minishops page
  * Find **one** you like AND can attend
  * Send out a tweet w/ the link and tag me in
  * I'll pick one and give you a free ticket
  * Bonus points if you include a selfie of you watching this talk or during Q&A 😄

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
- I know I just flooded you with a whole bunch of information
- Hopefully you found it all insightful
  * And it's motivated you to use TS in your next (or current) React project
- Again, the slides are already available online
- Ask questions on Twitter (@benmvp)
- Thanks!
- Hope you enjoy the rest conference!
