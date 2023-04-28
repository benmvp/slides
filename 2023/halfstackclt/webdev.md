<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 45%;" class="content-overlay">

  <h1>Let's web dev like it's 1999!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=halfstackclt-2023) | [@halfstackconf](https://twitter.com/halfstackconf/)</p>

  <br />

  <p>April 28, 2023</p>

  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

- **QUESTION: So how many of you were developing back in 1999?**
  - There may be someone who's like: "I wasn't even born in 1999!"
- So I'm hoping to share a little about my dev story and walk down memory lane
  - Or have a history lesson for most of you
- We'll hopefully learn some new things along the way
  - And appreciate where we are, based on where we've come from

/////

<a href="https://benmvp.com/hsclt-webdev?utm_source=benmvp&utm_medium=slides&utm_campaign=halfstackclt-2023" target="_blank">
  <img src="../../img/qrcodes/halfstackclt-2023-webdev.svg" style="width: 40%" alt="QR code for &quot;Let's web dev like it's 1999!&quot; talk" class="plain" />
</a>

<p>
  <a href="https://benmvp.com/hsclt-webdev?utm_source=benmvp&utm_medium=slides&utm_campaign=halfstackclt-2023" target="_blank">
    benmvp.com/hsclt-webdev
  </a>
</p>

NOTES:

- I want to let you know that these slides are already available online
  - So if you want to follow along or can't see well from the back, I've got you covered
- You can use this handy dandy QR code that'll take you to the slides
- You can go to my website, `benmvp.com`, and find them there too
- So you're covered with **three** different ways to access the slides!

=====
<!-- .slide: data-background="url(../../img/webdev/aid109294-v4-900px-Find-the-Minimum-and-Maximum-Points-Using-a-Graphing-Calculator-Step-1.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- My first programming language I learned was `BASIC`
  - Summer program in 1998
- Used that skill to build "apps" for my TI-83 calc in high school
  - **QUESTION:** Any users of any of the TI calculators?
- So I would manually type on the calculator using T9
  - And I built math apps to help check answers on math homework & tests
  - That's not cheating right?

/////
<!-- .slide: data-background="url(../../img/webdev/win95help.png) no-repeat center" data-background-size="cover" -->

NOTES:

- Started sharing my apps online
  - No Github, no App store
  - Just various sites where we could share apps
- And folks would ask how to write TI apps
- So I started writing TI calculator tutorials
- Initially I wrote them as Windows Help Applications
  - Kind of like a hypercard system where you can link screens together
  - Generated a `.hlp` file
  - Hard to distribute
- Quickly realized the web was a better way to distribute...

/////

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 75%">
    <a href="http://bgo.benmvp.com/" target="_blank">
      <img src="../../img/webdev/bgo-geocities-2001-screenshot-top.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
    </a>
  </div>
</div>

NOTES:

- So naturally I created a website
- I went into the Wayback Machine and found my very first site
  - Isn't it beautiful?
- I built "Basic Guru Online" as a Geocities website
  - (because apparently I was a "guru" at 16)
  - Geocities was like THE hosting service of the day
  - There was also Angelfire & Tripod
  - I'm talking early 2000
- BGO was like a full web application
  - Geocities handled all the backend with various plugins
- Now we have sophisticated deployment processes
  - But back then, I pushed new static files directly to their servers
  - Using FTP (File Transfer Protocol) - almost like SSH
  - No source control
  - I could pull up a File Explorer directly on the server and save files in Notepad

/////

<a href="http://bgo.benmvp.com/" target="_blank">
  <img src="../../img/webdev/bgo-geocities-2001-screenshot-top.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
</a>

<div class="code-highlight fragment current-visible" style="height: 200px; top: 57px; left: 550px; width: 800px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 307px; left: 790px; width: 330px"></div>
<div class="code-highlight fragment current-visible" style="height: 100px; top: 450px; left: 1400px; width: 490px"></div>
<div class="code-highlight fragment current-visible" style="height: 70px; top: 607px; left: 1400px; width: 490px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 747px; left: 50px; width: 1320px"></div>

NOTES:

- So I wanna just quickly walk through the interesting parts of the website
- **ONE:** I definitely created the logo in Microsoft Paint using PowerPoint clip-art + Comic Sans
  - Comic Sans was 🔥 back then
- **TWO:** I had a trusty-dusty hit counter (broken)
  - No need for Google Analytics! 😂
- **THREE:** Current date display still works
  - For some reason I thought that was necessary
  - This is why JS is backwards compatible - so my 20yo site still works
- **FOUR:** According to the Recent Updates
  - I had at least 70 members!
  - I wonder what Matt Hamlin is up to these days
- **FIVE:** I suggested using the AOL browser to view the page
  - It "should be okay" using Internet Explorer (probably v4) or Netscape Navigator
  - Best viewed on an 800x600 res monitor!
  - Used `<table>` for 2-column layout
  - Still "responsive" nearly 20 years later!

/////

<a href="http://bgo.benmvp.com/" target="_blank" style="-20em">
  <img src="../../img/webdev/bgo-geocities-2001-screenshot-bottom.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
</a>

<div class="code-highlight fragment current-visible" style="height: 470px; top: 56px; left: 1390px; width: 474px"></div>
<div class="code-highlight fragment current-visible" style="height: 124px; top: 900px; left: 30px; width: 1859px"></div>

NOTES:

- At the bottom of the page...
- **ONE:** There was a weekly poll
  - I guess at the time the Wayback Machine crawled the site...
  - I was asking about internet connection speed
  - I really wish I still had those results
- **TWO:** The bottom frame was fixed height
  - Main section filled rest of the window
  - More on this in a bit
- Surprisingly, I didn't use `<marquee>` or `<blink>` tags

/////

<a href="https://bgo.benmvp.com/" target="_blank">
  <img src="../../img/qrcodes/basic-guru-online.svg" style="width: 40%" alt="QR code for old Basic Guru Online website" class="plain" />
</a>

<p>
  <a href="https://bgo.benmvp.com/" target="_blank">
    bgo.benmvp.com
  </a>
  |
  <a href="https://github.com/benmvp/bgo" target="_blank">
    github.com/benmvp/bgo
  </a>
</p>

NOTES:

- I was going through my backup hard drive a couple of years ago...
- And I found a version of the old code from a little bit later than what I just showed
- So I put it on Github and hosted it on Vercel
  - No building necessary 😂
- It's at <https://bgo.benmvp.com/>
  - Feel free to follow this QR code to see it & seriously judge me
  - Heads up: it's gonna look terrible on your phone
- The code itself is at: <https://github.com/benmvp/bgo>

/////
<!-- .slide: data-background="#000 url(../../img/webdev/yahoo-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:

- Just for funsies...
- Here's what yahoo.com looked like at the time
  - Summer of 2001
  - Honestly, not too dissimilar from mine
- It's small, but notice "Powered by Compaq" at the bottom
- <https://web.archive.org/web/20010601021654/http://www.yahoo.com:80/>

/////
<!-- .slide: data-background="#000 url(../../img/webdev/amazon-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:

- And amazon.com
- "Microsoft XP is now shipping!" at the bottom
- <https://web.archive.org/web/20010601111711/http://www.amazon.com:80/exec/obidos/subst/home/home.html>

/////
<!-- .slide: data-background="#000 url(../../img/webdev/benmvp-site-2020.png) no-repeat center" data-background-size="contain" -->

NOTES:

- Fast forward nearly 2 decades
- I have my site: benmvp.com
- It uses Gatsby for static site generation
  - Written all in React
  - I'd Rather it be in Next.js, but that's another topic
- It generates the static HTML pages
  - Just like I did by hand way back when
- It uses TypeScript, GraphQL (unfortunately), Material UI, eslint & more!
- All to build a personal site!

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-steph-curry.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:

- But before we continue further can I get everyone to stand up?

/////
<!-- .slide: data-background="#000" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%">
    <img src="../../img/family/family-kemah-boardwalk.jpeg" alt="Photo of the Ilegbodu family at the Kemah Boardwalk" />
  </div>
</div>

NOTES:

- My name is Ben Ilegbodu
  - Christian, Husband, Father
- _Family introductions_
- We live in Manvel, TX (suburb of Houston)
  - Used to live in the Bay Area for 20 years
  - Moved back home

/////

<div style="display:flex;align-items:center;justify-content:space-around;">
  <div style="flex:0 0 45%">
    <img src="../../img/gde/experts-sticker-01.gif" alt="Google Developer Experts animation" class="plain" style=" background-color: #ddd; border-radius: 5px"/>
  </div>
  <div style="flex:0 0 45%; margin-left: 20px">
    <img src="../../img/stitchfix/lockup-solid-vert-gender-neutral-light.svg" alt="Stitch Fix Corporate logo (light)" class="plain" />
  </div>
</div>

NOTES:

- I'm a Google Developer Expert in Web Technologies
- Also currently a Frontend Architect at Stitch Fix
- Stitch Fix is an online personal styling service
  - Combines technology & data science
  - With an actual human stylist
  - Take the effort out of shopping by providing a selection of clothes picked just for you
  - And sent to your door on a frequency that you choose

=====
<!-- .slide: data-background="url(../../img/webdev/uc-berkeley-coding-bootcamp.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Berkeley Coding Boot Camp</h1>

      <div style="-webkit-columns:3;-moz-columns:3;columns:3;margin-bottom:1em;margin-top: 1em">
        <p>HTML5</p>
        <p>CSS3</p>
        <p>JavaScript</p>
        <p>jQuery</p>
        <p>Python/Django</p>
        <p>Bootstrap</p>
        <p>Express.js</p>
        <p>React.js</p>
        <p>Node.js</p>
        <p>AJAX/REST</p>
        <p>Database Theory</p>
        <p>Bookshelf.js</p>
        <p>MongoDB</p>
        <p>MySQL</p>
        <p>Command Line</p>
        <p>Git</p>
      </div>

  </div>
</div>

NOTES:

- Ok, let's switch gears away from me
- And talk about a friend of mine
- He graduated from UC Berkeley coding boot camp a few years back
- Look at all these skills they learned in just 12 weeks
  - Not just HTML, CSS & JavaScript
  - Command Line & Git (now table stakes)
  - jQuery, Bootstrap, React
  - Django, Express & MongoDB
- And it's _just_ enough to get an entry-level job

/////
<!-- .slide: data-background="#000 url(../../img/webdev/justyn-warner-551353-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- I mean, wow!
- The bar for the "minimally-viable" skills to build a site is so high now
- And we go to meetups & conferences like this to hear about all the things we **should** be doing
  - All to stay current

----

- But the bar wasn't always so high
  - In fact it was really, really low
  - To be honest, it probably non-existent
  - We were making things up as we went
- So I wanted to take a look at various aspects of how we built sites back in the day
  - And compare them to how things work now

=====
<!-- .slide: data-background="#000 url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- Before CSS3 flexbox & grid we needed ways to lay out our pages
- And many times we had some navigation that we wanted fixed
  - Either a header menu on top
  - Left nav
  - Or in the case of my site I thought a fixed nav footer was a good idea
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
  - **QUESTION: Anybody here use `<frameset>` before?**
- Before I even try to explain the code, take in this HTML!
- And it's in ALL-CAPS
- Attributes like `MARGINHEIGHT` & `FRAMEBORDER` aren't even quoting the values
- `<FRAME>` tags aren't even self-closings
  - Like how browsers even figure out how to handle that?
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
- We got a "frame" that spans the top
- Then 3 frames in a column
  - Outer ones are fixed and the middle one flexes
- So lets say "Frame 1" is your global header
- "Frame 2" would be a left page nav
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
- **ONE:** Each `<FRAME>` pointed to a separate actual HTML page
  - There was a page with just the header, just the nav, etc.
  - Kinda like today's `<iframe>`
- **TWO:** The `<FRAMESET>` can be aligned in either `ROWS` or `COLUMNS`
  - Sound familiar? 😉
  - **THREE:** And they can be nested
  - **FOUR:** Notice the `*` syntax to signal that the column takes up remaining space
  - This is pretty fancy for 20+ years ago, right?
- And we've got visual styling mixed right in the markup
- **FIVE:** Frames by default had ugly borders so they needed to be turned off
  - With `FRAMEBORDER=0`
- However, if we kept the borders on, they could be resized
  - **SIX:** So there was an attribute to turn prevent resizing
  - That's why the `<IFRAME>` became a thing
  - To not have to deal with the gnarliness of normal frames
- This whole setup was to allow us to avoid having to update the whole pages
  - The header, nav, and ads sections aren't changing
  - Just the main content
  - So clicking links in the header, shouldn't require a full page refresh?
  - Sound familiar?
  - We're trying to build in our fancy new technologies features that existed 20+ years ago!
- **SEVEN:** So that's what this `NAME=content` attribute is for
  - It lets allows us to make changes in one frame from another

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 95%;">
    <p>nav.html</p>
    <pre class="large"><code class="lang-html">&lt;HTML>
  &lt;BODY>
    &lt;UL>
      &lt;LI>&lt;A HREF="home.html" TARGET="content">Home&lt;/A>
      &lt;LI>&lt;A HREF="about.html" TARGET="content">About&lt;/A>
      &lt;LI>&lt;A HREF="help.html" TARGET="content">Help&lt;/A>
    &lt;/UL>
  &lt;/BODY>
&lt;/HTML></code></pre>
  </div>
</div>

NOTES:

- This is `nav.html`
  - Again it's a completely separate HTML file (like an `iframe`)
  - But for the links we set the `target` to point to that `content` frame
- You've probably always just done `target="_blank"` for a new window, right?
  - But `target` had other purposes!
- For some reason we liked to not close our `<LI>` tags either
  - Or maybe it was just me 😂
  - But it worked!
  - There weren't any linters to yell at us either
- BTW, `<frameset>` was technically deprecated in HTML5
  - Although browsers still display it, but...

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
  grid-template-areas: "header" "nav" "main" "ads";
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
  - This sounds awfully similar to CSS Grid
- Here's how we could implement the same thing now
- Notice how `<main>` actually comes before `<nav>` in the markup
  - For SEO purposes
  - But Grid layout puts it where we want visually!
  - And unlike my site this code provides responsive, mobile-first layout as well

=====
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- But CSS Grid is wayyy too modern for us
- Let's rewind 2 decades again...

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 40%;text-align:left">
        <h3>11:30</h3>
        <p style="margin-left:40px">Session #3</p>
        <h3>12:00</h3>
        <p style="margin-left:40px">Lunch</p>
        <h3>13:15</h3>
        <p style="margin-left:40px">Session #4</p>
        <h3>13:45</h3>
        <p style="margin-left:40px">Session #5</p>
      </div>
      <div style="flex:0 0 55%">
        <pre class="large"><code class="lang-html"><style type="text/css">
<!--
p { margin-left: 40px; }
-->
</style>

<h3>12:00</h3>
<p>Lunch</p>

<h3>13:15</h3>
<p>Sessopm #4</p></code></pre>
      </div>
    </div>

  </div>
</div>

NOTES:

- So let's say we have the schedule for HalfStack Charlotte here
- We just want to indent the session name by 40 pixels
- Naturally we'd just use some CSS selector to add `margin-left`
  - Simple enough right?
- Or maybe use a grid system like Bootstrap
  - Burn columns with offset
- But what do you do if CSS doesn't exist?
  - Or at least it's not guaranteed to be available in all browsers your customers might use?
  - Yeah there was a time when CSS didn't exist! 🤯

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 30%;text-align:left">
        <h3>11:30</h3>
        <p style="margin-left:40px">Session #3</p>
        <h3>12:00</h3>
        <p style="margin-left:40px">Lunch</p>
        <h3>13:15</h3>
        <p style="margin-left:40px">Session #4</p>
        <h3>13:45</h3>
        <p style="margin-left:40px">Session #5</p>
      </div>
      <div style="flex:0 0 70%">
        <pre class="large"><code class="lang-html"><H3>12:30/H3>
<P><IMG src="/1x1.gif" width="40">Lunch</P>

<H3>13:15</H3>
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
  - It was teeny tiny in size because its 1x1
  - We used it to do "pixel perfect" spacing before CSS
- It would work in both horizontal & vertical direction
  - Just add a `width` or add a `height`
- And we used all over the place!
  - Here we set the spacer gif to be `40px` in width to indent
- Again, responsive design & development wasn't a thing

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 30%;text-align:left">
        <h3>11:30</h3>
        <p style="margin-left:40px">Session #3</p>
        <h3>12:00</h3>
        <p style="margin-left:40px">Lunch</p>
        <h3>13:15</h3>
        <p style="margin-left:40px">Session #4/p>
        <h3>13:45</h3>
        <p style="margin-left:40px">Session #5</p>
      </div>
      <div style="flex:0 0 70%">
        <pre class="large"><code class="lang-html"><H3>12:00</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;Lunch</P>

<H3>13:15</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;Ben
  Ilegbodu</P></code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:

- For this problem
  - We could also use a whole bunch of `&nbsp;` entities
  - This was also used heavily
  - Because HTML ignores multiple whitespace characters
- But the spacing is dependent on the font
  - And it wouldn't be exact if needed to line things up
- So the spacer gif was the solution
- And then...

=====
<!-- .slide: data-background="url(../../img/webdev/greg-rakozy-129733-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- CSS became a thing!
- We had HTML **AND** CSS!
- So awesome!

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
- Yep we did that

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

- No longer did we have to use the `<FONT>` tag for styling everything
- Yep, that was definitely a thing I used **a lot**
  - No `<span>` just `<font>`, `<font>`, `<font>` everywhere!
  - Especialluy from tools like Dreamweaver
- The `<font>` tag is now _obsolete_
  - Like it shouldn't even work in browsers now!

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

- Of course we were still using `<table>` for layout back then
  - But we no longer needed all the styling **in** the markup
  - Yep we did that!
- Now... catch this...
  - We could put the styling... in a separate CSS file 🤯
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

- To change the default link styling
  - Finally!
- We could make default links a different color or remove the underline
- Visited links used to look different by default; let's undo that
- We changed the color or underline on hover
  - Look how dynamic it is!
- Really, CSS originally was just about taking styling out of HTML
  - It didn't really do anything _cool_ initially
  - No animations, transformations and all that stuff that came with CSS3
  - So this was about the coolest thing we could do

=====
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- So we've talked about...
  - `<FRAMESET>` - building optimized page layouts
  - spacer.gif - "pixel-perfect" spacing
  - And just now link styling - rudimentary CSS
- Now I wanna share something near & dear to my heart

/////
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

![Basic Guru Online table w/o rounded corners](../../img/webdev/bgo-internet-speed-poll-table.png)
<!-- .element: style="width:50%" -->

NOTES:

- If you remember...
  - This was the poll I had on the right-hand-side of my site
- It was asking about connection speed, remember?
- It had square corners

/////
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
  <aside style="border-radius:75px;width:50%;background:#ddd;overflow:hidden;border:10px solid #00008b">
    <header style="background:#00008b">
      <h3>Weekly Poll</h3>
    </header>
    <main style="height:750px">
    </main>
  </aside>
</div>

NOTES:

- But I really wanted to have rounded corners
  - But I didn't really know how to do that at the time
- These "pods" w/ rounded corners were starting to be a thing
  - I think Yahoo! popularized it
  - That Amazon screenshot from earlier had them
- But then rounded corners went out of fashion in the late 2000s with Material Design
  - Everything was flat again!
- But now they're coming back again?
  - You stay in the game long enough...
  - And you realized that it's all cyclical

/////
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-html">&lt;section>
  <header>
    <h1>Weekly Poll</h1>
  </header>
  <main> ... </main>
&lt;/section></code></pre>
      </div>
      <div style="flex:0 0 45%;">
        <pre class="large"><code class="lang-css">section {
  border-radius: 3px;
  border: 2px solid #00000b;
  background: #ddd;
  overflow: hidden;
}
header {
  background: #00000b;
}</code></pre>
      </div>
    </div>

<div class="code-highlight" style="height:70px;top:137px;left:850px;width:852px"></div>

  </div>
</div>

NOTES:

- Anyway, you would think we could just throw `border-radius` on it and be done with it
- But `border-radius` wasn't introduced into CSS until 2005
  - And wasn't widely supported 'til years later
  - Like a decade after I needed it
- So what did we do?

/////
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
  <aside style="border-radius:75px;width:50%;background:#ddd;overflow:hidden;border:10px solid #00008b;box-sizing:border-box">
    <header style="background:#00008b;">
      <h3>Weekly Poll</h3>
    </header>
    <main style="height:750px">
    </main>
  </aside>

  <table style="width:50%;height:860px;position:absolute;border-collapse:separate;border-spacing:2px;border-color:#000;border:5px dashed #fff">
    <tr>
      <td style="width:75px;height:75px;padding:0;border:5px dashed #fff;border-width:0 5px 5px 0"></td>
      <td style="width:calc(100% - 75px - 75px);height:75px;padding:0;border:5px dashed #fff;border-width:0 0 5px 0"></td>
      <td style="width:75px;height:75px;padding:0;border:5px dashed #fff;border-width:0 0 5px 5px"></td>
    </tr>
    <tr>
      <td style="width:75px;padding:0;border:5px dashed #000;border-width:0 5px 0 0"></td>
      <td style="width:calc(100% - 75px - 75px);padding:0;border:5px dashed #000;border-width:0 0 0 0"></td>
      <td style="width:75px;padding:0;border:5px dashed #000;border-width:0 0 0 5px"></td>
    </tr>
    <tr>
      <td style="width:75px;height:75px;padding:0;border:5px dashed #000;border-width:5px 5px 0 0"></td>
      <td style="width:calc(100% - 75px - 75px);height:75px;padding:0;border:5px dashed #000;border-width:5px 0 0 0"></td>
      <td style="width:75px;height:75px;padding:0;border:5px dashed #000;border-width:5px 0 0 5px"></td>
    </tr>
  </table>
</div>

NOTES:

- Well, back then, to make a "pod" with rounded corners...
  - I would cut it up into a 3x3 grid
- The corners would be the round corner images exported from Photoshop or equivalent
  - `blue-top-left-5px.gif`, `gray-bottom-right-5px.gif`, etc
  - The web didn't support rounded corners
  - So we had to resort to images
  - Yes, actual images to create rounded corners
- And what HTML element did we use to build this?

/////
<!-- .slide: data-background="url(../../img/webdev/valentin-gautier-bEbwgH6wP6Y-rounded-building-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 70%;">
    <pre class="large"><code class="lang-html">&lt;table>
  &lt;tr>
    &lt;td class="pod--top-left">&lt;/td>
    &lt;td class="pod--header">Weekly Poll&lt;/td>
    &lt;td class="pod--top-right">&lt;/td>
  &lt;/tr>
  &lt;tr>
    &lt;td class="pod--left">&lt;/td>
    &lt;td class="pod--content"> ... &lt;/td>
    &lt;td class="pod--right">&lt;/td>
  &lt;/tr>
  &lt;tr>
    &lt;td class="pod--bottom-left">&lt;/td>
    &lt;td class="pod--bottom">&lt;/td>
    &lt;td class="pod--bottom-right">&lt;/td>
  &lt;/tr>
&lt;/table></code></pre>
  </div>
</div>

NOTES:

- The HTML `<table>` of course
- The header could be styled all in HTML, but had to line up in height with the images
  - Same with the footer
- To create a "pod" took at least 4 images!
  - Imagine the web performance of the pages 😂
  - But also imagine... anytime the border radius or color changed
  - We had to export new images
  - Hardly any iterating was going on here
- If the designer wanted to change anything about the pod...
  - I would say "Well, you have to give me the corner images first!"
  - And that was the end of the conversation 😂
- There _was_ a small amount of time where `<table>`-based layouts were shunned
  - But `border-radius` couldn't reliably be used yet
  - We don't talk about those dark times 😭

=====
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:

- You know how some backend engineers look down on JS as a toy language?
- And we get mad saying it's legit
  - Especially since ES6+
- We use JS to build:
  - Highly-concurrent / low-latency servers in Node
  - Super-sophisticated web apps w/ service workers on the client
  - Powerful CLIs and build tooling as well
- But 2 decades ago JavaScript really was a toy language
  - And we did silly things with it

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 70%;">
    <pre class="large"><code class="lang-html">&lt;head>
  &lt;script language="javascript">
    function sayHello() {
      alert("Welcome to BASIC Guru Online!")
    }
  &lt;/script>
&lt;/head>
&lt;body onload="sayHello()"></code></pre>
  </div>
</div>

NOTES:

- Things like display an alert message whenever someone visited my site! 🤦🏾‍♂️
  - Kinda similar to those permission to send Notifications or read Location pop-ups
  - Like I said, it's all cyclical
- Soooo many things we wouldn't do today
- Like including a `<script>` in the `<head>`
  - Which we later learned is bad because it slows page render
- Using `document.writeln` to dynamically write content to the page
- Unobstrusive JS wasn't a thing yet
  - Instead of calling the function in `<body onload>` like I'm doing here
  - We should use `addEventListener`
  - But we didn't have jQuery yet (2006)
  - Back in the day we had to check for both `attachEvent` (IE) & `addEventListener` (standard)
- Going back to the code again...
  - Imagine debugging and having that `alert()` pop up every time! 🤣
  - What was I even doing?

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 80%;">
    <pre class="large"><code class="lang-javascript">alert('start');
var num = getNum(new Date());

alert(num);

if (num < 42) {
  alert('here?????');
  num = 42;
}

for (var i = 0; i < num; i++) {
  document.getElementById('val').innerHTML = num;
  alert(document.getElementById('val').innerHTML);
}</code></pre>
  </div>
</div>

NOTES:

- Speaking of debugging, we had no debugging tools either!
- `alert()` debugging is all we had
  - Not even `console` debugging, because there was no console!
  - And even console debugging is considered sub-par now
- And don't accidentally put an `alert()` in a loop or endless loop!
  - At that point, we had to just `Ctrl`+`Alt`+`Delete` to quit the browser

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 70%;">
    <img src="../../img/webdev/internet-explorer-script-error.jpg" alt="IE script error" style="width: 100%" />
  </div>
</div>

NOTES:

- In IE, whenever an error would happen, **everyone** would get this cryptic message
  - "An error has occurred in this script, do you want to continue running scripts?"
  - Our users would actually see this!
  - And this is before people were even somewhat web-savvy
- It'd show for **every** error
  - It was a usability nightmare
- Boy, if you ever needed motivation to write bug-free code

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 70%;">
    <img src="../../img/webdev/firebug-shutdown-screenshot.png" alt="Screenshot of page officially shutting down Firebug" style="width: 100%" />
  </div>
</div>

NOTES:

- Then Firebug came along and it changed the game around like 2006/2007
- It's possible you've never have even heard of it
- It was originally a extension to Firefox
  - Got me to move from IE to FF at the time
  - And it let us **see** the CSS and **debug** the JS!
  - I could change CSS values w/o refreshing the page!
  - It truly was revolutionary!
  - It paved the way for our amazing web inspectors today
  - And now it's table stakes for any modern web browser
- I don't think "Web 2.0" with the AJAX revolution happens w/o the debugging from Firebug

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
      <a href="https://github.com/" target="_blank">
        <img src="../../img/webdev/github-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://eslint.org/" target="_blank">
        <img src="../../img/nav-react/eslint-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://jestjs.io/" target="_blank">
        <img src="../../img/nav-react/jest-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://prettier.io/" target="_blank">
        <img src="../../img/webdev/prettier-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://swc.rs/" target="_blank">
        <img src="../../img/webdev/swc-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://www.npmjs.com/" target="_blank">
        <img src="../../img/webdev/npm-cube-logo.png" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://www.vercel.com/" target="_blank">
        <img src="../../img/webdev/vercel-icon-light.png" alt="" class="plain" style="width: 250px" />
      </a>
    </div>
  </div>
</div>

NOTES:

- And these days we have all this dev tooling to make our lives easier...
  - to ensure we don't ship broken code
  - _Past:_ All we had was our desktop & FTP to transfer the files
  - We would work directly on the server and break all sorts of things on "Production"
  - _One dangling comma would break **everything** in IE_
- Now, our code goes thru an incredible journey from idea to Production
- **Question:** How many of you can name all **9** of the icons up here?
  - Go ahead and shout them out
- **VSCode:** Editors like VSCode that make writing code so much easier
  - Intellisense, unused code warnings, integrations with TypeScript, **Co-pilot**, and many other extensions
- **Github:** Is like table stakes now, but we didn't even have version control back then
  - Well it existed but only w/in the biggest of companies
  - Imagine just 2 people working on the site at the same time w/o VC
- **SWC:** Run build scripts (like compiling/minification)
  - At Yahoo: Intentionally used to write terse JS/CSS to keep file sizes down
  - I had a friend at AOL who wasn't allowed to write any comments!
- **Github actions:** A continuous integration env automatically kicked off w/ git commits!
  - Can run tests (written in Jest)
  - And even continuously deploy
- **Vercel:** Is a deployment platform
  - It allows previewing PRs before they even merge!
- And this doesn't even get into all of the CSS & JS frameworks out there
  - Like Tailwind, React, Next.js, etc.

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=halfstackclt-2023" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:

- And that's it!
- As the conference slowly wraps up
  - I wanted to take a moment to thank our organizer (Dylan)...
  - for inviting me to speak
  - But more importantly for continuing to put HalfStack conferences together
  - _Applause_
- You can ask me questions on Twitter (@benmvp) or find me afterwards
- I hope you enjoyed our ride in the wayback machine
  - Hopefully it gives us all an appreciation for where we've come from
- Next time we wanna complain about missing CSS features we wish would exist...
  - Remember the spacer gif
- Thanks!
