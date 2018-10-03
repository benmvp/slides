<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
	<div style="width: 45%;" class="content-overlay">
  
  <h1>Let's web dev like it's 1999!</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [#nejsconf](https://twitter.com/hashtag/nejsconf)</p>

  <br />

  <p>July 27, 2018</p>
  
  
  </div>
</div>

NOTES:
- Good afternoon y'all!
- This talk is called "Let's web dev like it's 1999!"
- **QUESTION: So how many of you were developing in 1999?**
- Hoping to share a little about my dev story and walk down memory lane
  * Or take a history lesson for most of you
- Hopefully learn some new things along the way
  * Appreciate where we are
- Slides are available

=====
<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But first, would like everyone to stand up!
- Squats counting from 0
- Now turn to your neighbors, fist bump & say hi

/////
<!-- .slide: data-background="#000 url(../../img/family/family-naima-wedding.png) no-repeat center" data-background-size="contain" -->

NOTES:
- Christian, Husband, Father
- I'm a Principal Frontend Engineer at Eventbrite
- Work on our Frontend Platform team
  * Doing FE infra + design system work
- But I don't wanna talk about me now
  * Wanna talk about me 20 years ago


=====
<!-- .slide: data-background="url(../../img/webdev/aid109294-v4-900px-Find-the-Minimum-and-Maximum-Points-Using-a-Graphing-Calculator-Step-1.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- My first programming language I learned was `BASIC`
  * Summer program in '98
- Used that to build "apps" for my TI-83 calc in high school
  * Math apps to help check answers on algebra tests
- Wasn't a way to get code from comp to calc originally
  * Would type out code in this program
  * Print it out
  * Then type out by hand 
- I would've stuffed my own self in a locker

/////
<!-- .slide: data-background="url(../../img/webdev/win95help.png) no-repeat center" data-background-size="cover" -->

NOTES:
- Started sharing my apps online, and folks would ask how to write TI apps
- So I started writing TI calculator tutorials
- Initially I wrote them as Windows Help Applications
  * Kind of like a hypercard system where you can link screens
  * Generated a `.hlp` file
  * Hard to distribute
- Quickly realized the web was a better way to distribute...

/////

<a href="https://web.archive.org/web/20010405113755/http://www.geocities.com/basicguruonline/index.html" target="_blank">
  <img src="../../img/webdev/bgo-geocities-2001-screenshot-top.png" style="width: 100%" alt="Basic Guru Online Geocities circa 2001 Screenshot" />
</a>

<div class="code-highlight fragment current-visible" style="height: 200px; top: 57px; left: 550px; width: 800px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 307px; left: 790px; width: 330px"></div>
<div class="code-highlight fragment current-visible" style="height: 100px; top: 450px; left: 1400px; width: 490px"></div>
<div class="code-highlight fragment current-visible" style="height: 140px; top: 747px; left: 50px; width: 1320px"></div>


NOTES:
- Went into the Wayback Machine and found my first site
  * Isn't it a beauty
- Built "Basic Guru Online" as a Geocities website
  * (because apparently I was a "guru")
  * Geocities was like THE hosting service of the day
  * There was also Angelfire & Tripod
  * Talking early 2000
- BGO was like a full web application
  * Geocities handled all the backend
  * FTP'd individual files from computer to their servers
- **ONE:** Definitely created the logo in MS Paint using PowerPoint clip-art + Comic Sans
- **TWO:** Trusty-dusty hit counter (broken)
- **THREE:** Current date display still works
  * For some reason I thought that was necessary
  * Used `document.writeln`
  - This is why JS is backwards compatible so my 20yo site still works
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
- **TWO:** Overall page layout was frame-based using `<frameset>` (deprecated)
  * The bottom frame was fixed height
  * Main section filed rest of the window
  * Didn't get this functionality until recently with flexbox

/////
<!-- .slide: data-background="#000 url(../../img/webdev/yahoo-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- For fun...
- Here's what yahoo.com looked like at the time
- https://web.archive.org/web/20010601021654/http://www.yahoo.com:80/

/////
<!-- .slide: data-background="#000 url(../../img/webdev/amazon-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- And amazon.com
- https://web.archive.org/web/20010601111711/http://www.amazon.com:80/exec/obidos/subst/home/home.html

/////
<!-- .slide: data-background="#000 url(../../img/webdev/gatsby-blog-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- Fast forward nearly 2 decades
- Just updated my blog: benmvp.com
- Uses Gatsby for static site generation
  * Basically to generate the static HTML pages I did by hand way back when
- Written all in React
  * Uses Redux, GraphQL, JSS, Material-UI, Algolia, Webpack, Babel & more!
  * All to build a blog!

/////
<!-- .slide: data-background="url(../../img/webdev/uc-berkeley-coding-bootcamp.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Berkeley Coding Boot Camp</h1>

<div style="-webkit-columns:3;-moz-columns:3;columns:3;margin-bottom:1em;margin-top: 1em">
  HTML5   
  CSS3  
  JavaScript  
  jQuery  
  Python/Django  
  Bootstrap  
  Express.js  
  React.js  
  Node.js  
  AJAX/REST  
  Database Theory  
  Bookshelf.js  
  MongoDB  
  MySQL  
  Command Line  
  Git  
</div>

  </div>
</div>

NOTES:
- Friend of mine recently graduated from UC Berkely boot camp
- They learned all of this in the 12-week course!
- All for enough skills to get an entry-level job

/////
<!-- .slide: data-background="#000 url(../../img/webdev/justyn-warner-551353-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- The bar for "minimally-viable" skills to build a site is so high now
- We go to meetups/conferences like this to hear about all the things we **should** be doing
- I don't think a modern website could be created by one person from scratch
  - You would need multiple people
  - Or rely heavily on existing OSS tools


- But the bar wasn't always so high
  * In fact it was really, really low
  * Probably non-existent
- So I wanted to take a look at various aspects of how we built sites back in the day

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
- Talking about `<frameset>`
- Before I even try to explain the code, take in this HTML!
- It's in ALL-CAPS
- Attributes like `MARGINHEIGHT` & `FRAMEBORDER` aren't even quoting the values
- `<FRAME>` isn't even self-closing
  * Dunno how the browser figured out that one!
- Fun times!

/////
<!-- .slide: data-background="url(../../img/webdev/rawpixel-487103-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">
    <img src="../../img/webdev/frameset-borders-margins.jpg" style="width: 100%" />
  </div>
</div>

NOTES:
- This is the layout this contrived example is building
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
- Got visual styling mixed right in the markup
- **FIVE:** Frames by default had borders so they needed to be turned off
- If you left the borders on, they could be resized
  * **SIX:** So there was an attribute to turn those off
- **SEVEN:** So what about that `NAME` attribute? What's that for?

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
- Well in addition to providing grid layout, we also don't want to have to refresh the whole page
- The header, nav & ads are staying fixed
- So w/in `nav.html`, we just have our links target the `content` frame
  * You've probably always just done `target="_blank"` for a new window right?
  * It had a purpose!
- For some reason we liked to not close our `<LI>` tags either
- BTW, `<frameset>` was actually deprecated in HTML5, so...

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
  * This sounds awfully similar to CSS Grid that's becoming progressively more available in browsers
- Here's how we could implement the same thing now
- Notice how `<main>` actually comes before `<nav>` in the markup
  * For SEO
  * But Grid layout puts it where we want visually!

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
        <h3>June 22</h3>
        <p style="margin-left:40px">Low Earth Orbit (LEO)</p>
        <h3>July 1</h3>
        <p style="margin-left:40px">Medium Earth Orbit (MEO)</p>
        <h3>July 8</h3>
        <p style="margin-left:40px">High Earth Orbit (HEO)</p>
        <h3>July 10</h3>
        <p style="margin-left:40px">Decaying Orbit</p>
        <h3>July 27</h3>
        <p style="margin-left:40px">NEJS CONF!</p>
      </div>
      <div style="flex:0 0 55%">
        <pre class="large"><code class="lang-html"><style type="text/css">
<!--
p { margin-left: 40px; }
-->
</style>

<h3>June 22</h3>
<p>Low Earth Orbit (LEO)</p>

<h3>July 1</h3>
<p>Medium Earth Orbit (MEO)</p></code></pre>
      </div>
    </div>

  </div>
</div>
NOTES:
- So let's say we have these list of dates from the NEJS website
- We just want to indent those descriptions in by 40 pixels
- Naturally we'd just use some CSS selector to add `margin-left`
- Simple right?
- Or maybe use Bootstrap's grid system
- But what do you do if CSS doesn't exist?
  * Or at least it's not guaranteed to be in all of your user's browsers?

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 35%;text-align:left">
        <h3>June 22</h3>
        <p style="margin-left:40px">Low Earth Orbit (LEO)</p>
        <h3>July 1</h3>
        <p style="margin-left:40px">Medium Earth Orbit (MEO)</p>
        <h3>July 8</h3>
        <p style="margin-left:40px">High Earth Orbit (HEO)</p>
        <h3>July 10</h3>
        <p style="margin-left:40px">Decaying Orbit</p>
        <h3>July 27</h3>
        <p style="margin-left:40px">NEJS CONF!</p>
      </div>
      <div style="flex:0 0 60%">
        <pre class="large"><code class="lang-html"><H3>June 22</H3>
<P><IMG src="/1x1.gif" width="40">Low 
Earth Orbit (LEO)</P>

<H3>July 1</H3>
<P><IMG src="/1x1.gif" width="40">Medium 
Earth Orbit (MEO)</P></code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- Well you use a 1x1.gif!
- It's known as a "spacer gif"
- And yes I say "gif" not "jif" 😀
- It was 100% transparent, so it was see-thru
  * Used to do "pixel perfect" spacing before CSS
- Would work in both horizontal & vertical direction
- Used all over the place!

/////
<!-- .slide: data-background="url(../../img/webdev/celso-405219-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 85%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 40%;text-align:left">
        <h3>June 22</h3>
        <p style="margin-left:40px">Low Earth Orbit (LEO)</p>
        <h3>July 1</h3>
        <p style="margin-left:40px">Medium Earth Orbit (MEO)</p>
        <h3>July 8</h3>
        <p style="margin-left:40px">High Earth Orbit (HEO)</p>
        <h3>July 10</h3>
        <p style="margin-left:40px">Decaying Orbit</p>
        <h3>July 27</h3>
        <p style="margin-left:40px">NEJS CONF!</p>
      </div>
      <div style="flex:0 0 55%">
        <pre class="large"><code class="lang-html"><H3>June 22</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;Low 
Earth Orbit (LEO)</P>

<H3>July 1</H3>
<P>&NBSP;&NBSP;&NBSP;&NBSP;Medium 
Earth Orbit (MEO)</P></code></pre>
      </div>
    </div>
  </div>
</div>

NOTES:
- For this could use a whole bunch of `&nbsp;` entities
- But the spacing is dependent on the font
  * Wouldn't be exact if needed to line things up

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
- Still using `<table>` for layout, but no longer need all the styling in the markup

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
- You know how BE engineers are always saying JavaScript is a toy language
- And we get mad saying it's legit
  * Especially since ES6+
- We use JS to build:
  * Highly-concurrent / low-latency servers
  * Super-sophisticated web apps w/ service workers
- Well 2 decades ago it really was a toy language
  * We did silly things with it

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
- Soooo many things we wouldn't do today
- Including a `<script>` in the `<head>` is bad because it slows down render
- Using `document.writeln` to dynamically write content to the page
- Unobstrusive JS wasn't a thing yet
  * Instead of calling the function in `onload`, use `addEventListener`
  * But we didn't have jQuery (2006)
  * Had to check for both `attachEvent` (IE) & `addEventListener` (standard)


- Imagine debugging and having that `alert()` pop up every time!

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
- Speaking of debugging, we had no debugging tools!
- `alert()` debugging is all we had
  * Not even `console` debugging, because there was no console
  * And console debugging is considered sub-par
- And don't accidentally put an `alert()` in a loop or endless loop!
  * Had to just quit the browser

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <img src="../../img/webdev/internet-explorer-script-error.jpg" alt="IE script error" style="width: 100%" />
  </div>
</div>

NOTES:
- In IE, whenever an error would happen everyone get this cryptic message
- It'd show for **every** error

/////
<!-- .slide: data-background="url(../../img/webdev/rodolfo-mari-81201-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
	<div class="content-overlay" style="width: 70%;">
    <img src="../../img/webdev/firebug-shutdown-screenshot.png" alt="Screenshot of page officially shutting down Firebug" style="width: 100%" />
  </div>
</div>

NOTES:
- Then Firebug came along and it changed the game in 2006/2007
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
      <a href="https://eslint.org/" target="_blank">
        <img src="../../img/nav-react/eslint-logo.svg" alt="" class="plain" style="width: 250px" />
      </a>
      <a href="https://jestjs.io/" target="_blank">
        <img src="../../img/nav-react/jest-logo-dark.svg" alt="" class="plain" style="width: 250px" />
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
- **Travis:** Continuous integration env automatically kicked off w/ git commits!
  * Can run tests
  * Even automatically deploy
- **Gulp:** Run build scripts
  * Used to write terse JS/CSS to keep file sizes down
  * Friend at AOL wasn't allowed to write comments!
- **Netlify:** Allows previewing PRs before they even merge!

=====
<!-- .slide: data-background="url(../../img/webdev/sydney-rae-408416-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- Quick question before I finish:
- **How many people here have been in the industry less than 2 years?**
- Great that you're here
  * Great that you're wanting to learn
  * Early on, conferences like these were few and far between
- But most newbies have "imposter syndrome"
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
  * Some I've had the pleasure of mentoring/training
  * Others who I didn't even know they were bootcamp grads until they told me
- Even if you just graduated yesterday
  * You can be just as integral as those of us who were there near the beginning or w/ a traditional background
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
- I hope you enjoyed our ride in the wayback machine
  * Hopefully it gives us all appreciation for where we've come from
  * Next time we wanna complain about the current situation
- Ask questions on Twitter, via email or AMA!
- Wanna thank **conference** and **YOU!**
- Thanks!
