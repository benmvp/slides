<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="content-overlay">
  
  <h1>Let's web dev like it's 1999!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@CSSconfeu](https://twitter.com/CSSconfeu)</p>

  <br />

  <p>May 31, 2019</p>
  
  
  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- Good afternoon everyone!
  * Welcome back from lunch
- This talk is called "Let's web dev like it's 1999!"
- **QUESTION: So how many of you were developing in 1999?**
- Hoping to share a little about my dev story and walk down memory lane
  * Or take a history lesson for most of you
- Hopefully learn some new things along the way
  * Appreciate where we are based on where we've come from
- **Slides are available online**

=====
<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But first, would like everyone to stand up!

/////
<!-- .slide: data-background="#000 url(../../img/family/family-under-gazebo.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Christian, Husband, Father
  * Live in the San Francisco Bay Area
- I'm a Principal Frontend Engineer at Eventbrite
- Work on our new Data & Recommendations team
  * Focused on providing insights to event organizers to help them be more successful
- Also a huge basketball / NBA fan
  * Missed Game 1 overnight
  * Will miss Game 2 too
  * It's worth it, happy to be here!
- But I don't wanna talk about me now
  * Wanna talk about me 20 years ago


=====
<!-- .slide: data-background="url(../../img/webdev/aid109294-v4-900px-Find-the-Minimum-and-Maximum-Points-Using-a-Graphing-Calculator-Step-1.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- My first programming language I learned was `BASIC`
  * Summer program in '98
- Used that to build "apps" for my TI-83 calc in high school
  * Math apps to help check answers on math homework & tests
  * That's not cheating right?

/////

<a href="https://web.archive.org/web/20010405113755/http://www.geocities.com/basicguruonline/index.html" target="_blank">
  <img src="../../img/webdev/bgo-geocities-2001-screenshot-top.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
</a>

<div class="code-highlight fragment current-visible" style="height: 200px; top: 57px; left: 550px; width: 800px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 307px; left: 790px; width: 330px"></div>
<div class="code-highlight fragment current-visible" style="height: 100px; top: 450px; left: 1400px; width: 490px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 747px; left: 50px; width: 1320px"></div>


NOTES:
- Wanted a way to teach others how to program TI calculators
  * So naturally I created a website
- Went into the Wayback Machine and found my first site
  * Isn't it beautiful
- Built "Basic Guru Online" as a Geocities website
  * (because apparently I was a "guru")
  * Geocities was like THE hosting service of the day
  * There was also Angelfire & Tripod
  * Talking early 2000
- BGO was like a full web application
  * Geocities handled all the backend
  * Updated site by pushing new static files directly to their servers with FTP (File Transfer Protocol)
- **ONE:** Definitely created the logo in Microsoft Paint using PowerPoint clip-art + Comic Sans
- **TWO:** Trusty-dusty hit counter (broken)
- **THREE:** Current date display still works
  * For some reason I thought that was necessary
  - This is why JS is backwards compatible - so my 20yo site still works
- **FOUR:** I suggested using AOL to view the page
  * "Should be okay" using Internet Explorer or Netscape Navigator
  * Best viewed on an 800x600 res monitor!
  * Used `<table>` for 2-column layout
    * Still "responsive" nearly 20 years later!

/////

<a href="https://web.archive.org/web/20010405113755/http://www.geocities.com/basicguruonline/index.html" target="_blank" style="-20em">
  <img src="../../img/webdev/bgo-geocities-2001-screenshot-bottom.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
</a>

<div class="code-highlight fragment current-visible" style="height: 470px; top: 56px; left: 1390px; width: 474px"></div>
<div class="code-highlight fragment current-visible" style="height: 124px; top: 900px; left: 30px; width: 1859px"></div>


NOTES:
- **ONE:** Weekly poll asks about internet connect speed
  * Wish I had the results
- **TWO:** The bottom frame was fixed height
  * Main section filled rest of the window
  * More on this in a bit
- Surprisingly I didn't use `<marquee>` or `<blink>` tags

/////
<!-- .slide: data-background="#000 url(../../img/webdev/yahoo-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- For fun...
- Here's what yahoo.com looked like at the time
- "Powered by Compaq" at the bottom
- https://web.archive.org/web/20010601021654/http://www.yahoo.com:80/

/////
<!-- .slide: data-background="#000 url(../../img/webdev/amazon-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- And amazon.com
- "Microsoft XP is now shipping!" at the bottom
- https://web.archive.org/web/20010601111711/http://www.amazon.com:80/exec/obidos/subst/home/home.html

=====
<!-- .slide: data-background="#000 url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Before CSS3, flexbox & grid we needed ways to lay out our pages
- And many times we had some navigation that we wanted fixed
  * Either a header menu on top
  * Left nav
  * Or in the case of my site I thought a fixed nav footer was a good idea
- Now you may think I'm talking about using `<table>`s, but no!
- I'm talking about page layouts that pre-dated `<table>`

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">
    <pre class="large"><code class="lang-html">&lt;FRAMESET ROWS="150px,\*">
  &lt;FRAME NORESIZE SRC="header.html" MARGINHEIGHT=15>
  &lt;FRAMESET COLS="20%,\*,20%">
    &lt;FRAME SRC="nav.html" FRAMEBORDER=0>
    &lt;FRAME SRC="home.html" FRAMEBORDER=0 NAME=content>
    &lt;FRAME SRC="ads.html" FRAMEBORDER=0>
  &lt;/FRAMESET>
&lt;/FRAMESET></code></pre>
  </div>
</div>


NOTES:
- Talking about `<frameset>`!
- Before I even try to explain the code, take in this HTML!
- It's in ALL-CAPS
- Attributes like `MARGINHEIGHT` & `FRAMEBORDER` aren't even quoting the values
- `<FRAME>` isn't even self-closing
  * Dunno how the browser figured out that one!
- The web was wild!

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">
    <img src="../../img/webdev/frameset-borders-margins.jpg" style="width: 100%" />
  </div>
</div>

NOTES:
- This is the layout that this contrived example is building
- Got a "frame" that span the top
- Then 3 frames in a column
  * Outer ones are fixed and the middle one flexes
- So lets say "Frame 1" is your global header
- "Frame 2" would be a left nav
- "Frame 4" would be a right-side ads column maybe
- And "Frame 3" would actually be the main contents


/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">
    <p>site.html</p>
    <pre class="large"><code class="lang-html">&lt;FRAMESET ROWS="150px,\*">
  &lt;FRAME NORESIZE SRC="header.html" MARGINHEIGHT=15>
  &lt;FRAMESET COLS="20%,\*,20%">
    &lt;FRAME SRC="nav.html" FRAMEBORDER=0>
    &lt;FRAME SRC="home.html" FRAMEBORDER=0 NAME=content>
    &lt;FRAME SRC="ads.html" FRAMEBORDER=0>
  &lt;/FRAMESET>
&lt;/FRAMESET></code></pre>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 216px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 156px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 295px; top: 274px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 274px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 330px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 216px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 388px;"></div>

  </div>
</div>


NOTES:
- Back to the code
- **ONE:** Each `<FRAME>` pointed to a separate actual page
  * An HTML page with just the header, just the nav, etc.
- **TWO:** The `<FRAMESET>` can be aligned in either `ROWS` or `COLUMNS`
  * **THREE:** And they can be nested
  * **FOUR:** Notice the `*` syntax to signal that the column takes up remaining space
  * Pretty fancy for 20 years ago right?
- Got visual styling mixed right in the markup
- **FIVE:** Frames by default had borders so they needed to be turned off
- If you left the borders on, they could be resized
  * **SIX:** So there was an attribute to turn prevent resizing
- **SEVEN:** So what about that `NAME` attribute? What's that for?
  * Lemme explain

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 95%;">
    <p>nav.html</p>
    <pre class="large"><code class="lang-html">&lt;HTML>
  &lt;BODY>
    &lt;UL>
      &lt;LI>&lt;A HREF="home.html" TARGET=content>Home&lt;/A>
      &lt;LI>&lt;A HREF="about.html" TARGET="content">About&lt;/A>
      &lt;LI>&lt;A HREF="help.html" TARGET="content">Help&lt;/A>
    &lt;/UL>
  &lt;/BODY>
&lt;/HTML></code></pre>
  </div>
</div>

NOTES:
- Well in addition to providing a grid-like layout
  * We also don't want to have to refresh the whole page
- The header, nav & ads are staying fixed
- So w/in `nav.html`, we just have our links target the `content` frame
  * You've probably always just done `target="_blank"` for a new window right?
  * But `target` has other purposes!
- For some reason we liked to not close our `<LI>` tags either
  * Or maybe it was just me 😂
- BTW, `<frameset>` was actually deprecated in HTML5
  * Browsers still display it, but...

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 35%;">
        <pre class="large"><code class="lang-html">&lt;body>
  <header> ... </header>
  <main> ... </main>
  <nav> ... </nav>
  <aside> ... </aside>
&lt;/body></code></pre>
      </div>
      <div style="flex:0 0 60%;">
        <pre><code class="lang-css">header { grid-area: header; }
main { grid-area: main; }
nav { grid-area: nav; }
aside { grid-area: ads; }
body {
  display: grid;
  grid-template-areas: "header"
                       "nav" 
                       "main" 
                       "ads";
  grid-template-columns: 100%;
  grid-template-rows: 150px 50px 1fr 30px;
}
@media screen and (min-height: 600px) {
  body {
    grid-template-areas: "header header header"
                         "nav main ads";
    grid-template-columns: 20% 1fr 20%;
    grid-template-rows: 150px 1fr;

  }
}</code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- If you've been keeping up with the latest in CSS-land
  * This sounds awfully similar to CSS Grid that Rachel was talking about earlier
- Here's how we could implement the same thing now
- Notice how `<main>` actually comes before `<nav>` in the markup
  * For SEO
  * But Grid layout puts it where we want visually!
  * And has a responsive, mobile-first layout as well

=====
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- But CSS Grid is wayyy to modern for us
- Let's go back 2 decades again...

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 40%;text-align:left">
        <h3>12:35</h3>
        <p style="margin-left:40px">Gil Tayar</p>
        <h3>13:05</h3>
        <p style="margin-left:40px">🥗🍝 Lunch</p>
        <h3>14:20</h3>
        <p style="margin-left:40px">Ben Ilegbodu</p>
        <h3>14:55</h3>
        <p style="margin-left:40px">Manuel Rego</p>
      </div>
      <div style="flex:0 0 55%">
        <pre class="large"><code class="lang-html"><style type="text/css">
<!--
p { margin-left: 40px; }
-->
</style>

<h3>13:05</h3>
<p>🥗🍝 Lunch</p>

<h3>14:20</h3>
<p>Ben Ilegbodu</p></code></pre>
      </div>
    </div>

  </div>
</div>
NOTES:
- So let's say we have the schedule for CSSConf EU 2019
- We just want to indent the speakers in by 40 pixels
- Naturally we'd just use some CSS selector to add `margin-left`
- Simple enough right?
- Or maybe use Bootstrap's grid system
- But what do you do if CSS doesn't exist?
  * Or at least it's not guaranteed to be available in all browsers?

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 25%;text-align:left">
        <h3>12:35</h3>
        <p style="margin-left:40px">Gil Tayar</p>
        <h3>13:05</h3>
        <p style="margin-left:40px">🥗🍝 Lunch</p>
        <h3>14:20</h3>
        <p style="margin-left:40px">Ben Ilegbodu</p>
        <h3>14:55</h3>
        <p style="margin-left:40px">Manuel Rego</p>
      </div>
      <div style="flex:0 0 75%">
        <pre class="large"><code class="lang-html"><H3>13:05</H3>
<P><IMG src="/1x1.gif" width="40">🥗🍝
  Lunch</P>

<H3>14:20</H3>
<P><IMG src="/1x1.gif" width="40">Ben
  Ilegbodu</P></code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- Well you use `1x1.gif`!
- It's known as a "spacer gif"
- And yes I say "gif" not "jif" 😀
- It was 100% transparent, so it was see-thru
  * It was teeny tiny in size
  * Used to do "pixel perfect" spacing before CSS
- Would work in both horizontal & vertical direction
- Used all over the place!
- Again, responsive design & development wasn't a thing

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 25%;text-align:left">
        <h3>12:35</h3>
        <p style="margin-left:40px">Gil Tayar</p>
        <h3>13:05</h3>
        <p style="margin-left:40px">🥗🍝 Lunch</p>
        <h3>14:20</h3>
        <p style="margin-left:40px">Ben Ilegbodu</p>
        <h3>14:55</h3>
        <p style="margin-left:40px">Manuel Rego</p>
      </div>
      <div style="flex:0 0 65%">
        <pre class="large"><code class="lang-html"><H3>13:05</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;🥗🍝
  Lunch</P>

<H3>14:20</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;Ben
  Ilegbodu</P></code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- For this, we could use a whole bunch of `&nbsp;` entities
- But the spacing is dependent on the font
  * Wouldn't be exact if needed to line things up
- So the spacer gif was the solution

=====
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- And then CSS became a thing!
- We had HTML AND CSS!
- Awesome!

/////
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 50%;">
    <pre class="large"><code class="lang-html">&lt;BODY
  BGCOLOR="#DDDDDD"
  TEXT="#000000" 
  LINK="#0000FF"
  VLINK="#0000FF" 
  ALINK="#FF0000"
></code></pre>
  </div>
</div>


NOTES:
- No longer did we have to put text, link or background colors directly on `<body>`

/////
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">
    <pre class="large"><code class="lang-html">&lt;FONT FACE="COMIC SANS MS" COLOR="#FF0000" SIZE="-1">
  Weekly Poll
&lt;/FONT></code></pre>
  </div>
</div>

NOTES:
- No longer did we have to use the `<FONT>` tag (osbsolete) for styling everything
- Yep, that was definitely a thing I used **a lot**
  * No `<span>` just `<font>`, `<font>`, `<font>`

/////
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">
    <pre class="large"><code class="lang-html">&lt;TABLE RULES="NONE" WIDTH="95" BORDERCOLOR="#00008B" BORDER="1">
  &lt;TR ALIGN="CENTER" BGCOLOR="#00008B">
    ...
  &lt;/TR>
&lt;/TABLE></code></pre>
  </div>
</div>

NOTES:
- Still using `<table>` for layout then of course
  * But no longer need all the styling **in** the markup
  * Could put it in a separate file


- However...
- You know what we ended up using CSS most for in the beginning????

/////
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 90%;">
    <pre class="large"><code class="lang-css">a, a:visited { color: red;   text-decoration: none; }
a:hover      { color: black; text-decoration: underline; }</code></pre>
  </div>
</div>

NOTES:
- To screw with the default link styling
- Make default links a different color; no underline
- Visited links used to look different by default; undo that
- Change color/underline on hover
- Look how dynamic it is!
- CSS originally was just about taking styling out of HTML
  * It didn't really do anything _cool_ initially
  * So this was about the coolest thing we could do

=====
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- There's this camp of people who thing CSS is so easy
- And there's another camp that thinks it's so hard styling should be replaced with JS
- I don't want to get in the middle of _that_ war
  * But 20 years ago debugging styling was definitely a pain!

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <pre class="large"><code class="lang-css">.a {
  /\* layout styles \*/
  background: pink;
}
.b {
  /\* layout styles \*/
  border: 5px dashed yellow;
}</code></pre>
  </div>
</div>

NOTES:
- No way of easily knowing what the browser was rendering
  * Or even what classes were being applied
  * Compound that with sizing, layout or z-index issues
- Would throw dummy background or border colors
  * Just to see if a CSS class was being applied
  * Or a sense of bounding boxes
  * Kind of like the `console.log` of CSS
- And of course when testing or debugging had to...
  * Make change
  * Save
  * Reload browser
  * See result
  * Scratch my head
  * Wish StackOverlay existed
  * Repeat...

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <img src="../../img/webdev/firebug-shutdown-screenshot.png" alt="Screenshot of page officially shutting down Firebug" style="width: 100%" />
  </div>
</div>

NOTES:
- Then Firebug came along and it changed the game in 2006/2007
  * Right when I was starting full-time
- May never have even heard of it
- It was originally a Firefox extension
  * Got me to move from IE to FF at the time
  * And let you *see* the CSS and debug the JS!
  * Truly revolutionary!
  * Paved the way for our amazing web inspectors today
- I don't think "Web 2.0" with AJAX happens w/o the debugging from Firebug

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 75%;">
    <div style="display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap">
      <a href="https://code.visualstudio.com/" target="_blank">
        <img src="../../img/webdev/vscode-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://www.typescriptlang.org/" target="_blank">
        <img src="../../img/es6/typescript-logo-square.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://www.npmjs.com/" target="_blank">
        <img src="../../img/webdev/npm-cube-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://sass-lang.com/" target="_blank">
        <img src="../../img/why-react/sass-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://github.com/postcss/postcss" target="_blank">
        <img src="../../img/webdev/postcss-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://prettier.io/" target="_blank">
        <img src="../../img/webdev/prettier-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://github.com/" target="_blank">
        <img src="../../img/webdev/github-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://travis-ci.org/" target="_blank">
        <img src="../../img/webdev/travisci-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://gulpjs.com/" target="_blank">
        <img src="../../img/nav-react/gulp-logo.svg" alt="" class="plain" style="width: 200px" />
      </a>
      <a href="https://www.netlify.com/" target="_blank">
        <img src="../../img/webdev/netlify-logo.jpg" alt="" class="plain" style="width: 250px" />
      </a>
    </div>
  </div>
</div>



NOTES:
- And these days we have all this dev tooling to make our lives easier
  * To ensure we don't ship broken code
  * _Past:_ All we had was our desktop & FTP to transfer the files
  * Would work directly on the server and break all sorts of things on Production
  * _One dangling commas would break **everything**_
- Our code goes thru an incredible journey from idea to Production
- **VSCode:** Editors like VSCode that make writing code so much easier
  * Intellisense, unused code warning, extensions
- **Github:** Like table stakes now, but we didn't have version control
  * It existed but only w/in the biggest of companies
  * Imagine just 2 people working on the site at the same person
- **Gulp:** Run build scripts to transform SASS into minified/optimized CSS
  * Used to write terse CSS/JS to keep file sizes down
  * Friend at AOL wasn't allowed to write comments!
- **Travis:** Continuous integration env automatically kicked off w/ git commits!
  * Can run tests
  * Even automatically deploy
- **Netlify:** Allows previewing PRs before they even merge!

=====
<!-- .slide: data-background="url(../../img/webdev/sydney-rae-408416-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Quick question before I finish:
- **How many people here have been in the industry less than 2 years?**
- I was fortunate that I was exposed to software dev at 15
- Great that you're here
  * Great that you're wanting to learn
  * Early on, conferences like these were few and far between
- But most new devs have "imposter syndrome"
  * The bar for "minimally-viable" skills to build a site is so high now
  * Feel like you don't belong
  * Can come to a conference like this and it can grow _worse_!
  * So many things you _have_ to learn
  * So continuously feeling like you're behind
  * Especially if you only had a 3- or 6-month accelerated program to learn
- Futhermore there are  "thought leaders" today have been around a while
  * They feel you have to learn web dev the way they did
  * You have to learn the hard way so you can appreciate what you've got
- So I want to encourage you
  * Don't stress!
  * You're not less than / sub par
  * There are many ways to learn
  * I know many folks from bootcamps who are flat out killing it
- Even if you just graduated yesterday
  * You can be just as integral to the community as those of us who were there near the beginning or w/ a traditional background
- To sum it up: YOU GOT THIS!

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
- That's it!
- Wanted to thank the organizers
  * Inviting me to speak
  * Putting on such a welcoming & inclusive conference
  * Closed captioning & child care!
  * _Applause_
- I hope you enjoyed our ride in the wayback machine
  * Hopefully it gives us all appreciation for where we've come from
  * Next time we wanna complain about the current situation
- Ask questions on Twitter
- Thanks!
