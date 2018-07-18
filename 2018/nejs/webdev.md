<!-- .slide: data-state="title-page" -->

# Let's web dev like it's 1999!

<br />

## Ben Ilegbodu

<br />

[@benmvp](https://twitter.com/benmvp) | [benmvp.com](/) | [@nejsconf](https://twitter.com/nejsconf)

<br />

July 27, 2018

NOTES:
- Welcome!
- Before we get started, how many of you were developing in 1999?
- Hoping to share a little about my dev story and walk down memory lane
  * Or take a history lesson for most of you

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-kevin-durant.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="overlay-light">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:
- But first, would like everyone to stand up!
- Squats counting down from 10 to 1
- Now turn to your neighbors, fist bump & say hi

/////

## me.json

<div style="display:flex;align-items:center;justify-content:space-between">
	<div style="flex:0 0 35%;">
		<img src="../../img/family-tahoe-2018-selfie.jpg" style="width:100%;height:auto" alt="Ilegbodu family at Tahoe in 2018" />
	</div>
	<div style="flex:0 0 60%;">
		<pre class="large"><code class="lang-json">
{
  "name": "Ben Ilegbodu",
  "priorities": [
    "Jesus", "family", "work"
  ],
  "location": "Pittsburg, CA",
  "work": "Eventbrite",
  "role": "Principal Frontend Engineer",
  "hobbies": [
    "basketball", "DIY", "movies"
  ]
}
			</code></pre>
	</div>
</div>

NOTES:
- I'm a Principal Frontend Engineer at Eventbrite
- Been working on FE infra writing shell scripts in Node
- Been using some of these JS features I'm showing

=====
<!-- .slide: data-background="url(../../img/webdev/aid109294-v4-900px-Find-the-Minimum-and-Maximum-Points-Using-a-Graphing-Calculator-Step-1.jpg) no-repeat center" data-background-size="contain" -->

NOTES:
- My first programming language I learned was `BASIC`
  * Summer program in '98
- Used that to build "apps" for my TI-83 calc in high school
- Would type out code in Notepad
- Print it out
- Then type out by hand using T-9 keypad on calculator
  * Wasn't a way to get code from comp to calc originally
- I would've stuffed my ownself in a locker

/////
<!-- .slide: data-background="url(../../img/webdev/win95help.png) no-repeat center" data-background-size="contain" -->

NOTES:
- Started sharing my apps online, and folks would ask how to write TI apps
- So I started writing TI calculator tutorials
- Initially I wrote them as Windows Help Applications
  * Kind of like a hypercard system where you can link screens
  * Generated a `.hlp` file
  * Hard to distribute
- Quickly realized the web...

/////

[![Basic Guru Online Geocities circa 2001 Screenshot](../../img/webdev/bgo-geocities-2001-screenshot.png)](https://web.archive.org/web/20010405113755/http://www.geocities.com/basicguruonline/index.html)

NOTES:
- Built "Basic Guru Online" as a Geocities website
  * (because apparently I was a "guru")
  * Geocities was like THE hosting service of the day
  * There was also Angelfire
  * Talking early 2000
- BGO was like a full web application
  * Geocities handled all the backend
  * FTP'd individual files from computer to their server
- **FIRST:** Overall page layout was frame-based using `<frameset>`
  * The bottom frame was fixed height
  * Main section filed rest of the window
  * Didn't get this functionality until recently with flexbox
- **SECOND:** 2 column layout using `<table>`
  * Still "responsive" nearly 20 years later!
- **THIRD:** Definitely created the logo in MS Paint using PowerPoint clip-art + Comic Sans
- **FOURTH:** Trusty-dusty hit counter (broken)
- **FIFTH:** I suggest using AOL to view the page
  * "Should be okay" using Internet Explorer or Netscape Navigator
  * Best viewed on an 800x600 res monitor!
- **SIXTH:** Weekly poll asks about internet connect speed

/////
<!-- .slide: data-background="url(../../img/webdev/yahoo-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- For fun...
- Here's what yahoo.com looked like at the time
- https://web.archive.org/web/20010601021654/http://www.yahoo.com:80/

/////
<!-- .slide: data-background="url(../../img/webdev/amazon-2001-screenshot.png) no-repeat center" data-background-size="contain" -->

NOTES:
- And amazon.com
- https://web.archive.org/web/20010601111711/http://www.amazon.com:80/exec/obidos/subst/home/home.html

/////
<!-- .slide: data-background="url(../../img/webdev/gatsby-blog-screenshot.png) no-repeat center" data-background-size="contain" -->

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
  <div class="overlay-light">
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
- Friend of mine recently graduated from a boot camp
- They learned all of this in the 12-week course
- https://bootcamp.berkeley.edu/coding/

/////
<!-- .slide: data-background="url(../../img/webdev/justyn-warner-551353-unsplash.jpg) no-repeat center" data-background-size="cover" -->

NOTES:
- The bar for what's "minimally-viable" is so high now
- We go to conferences/meetups to hear from industry leaders about all the things we **should** be doing
- A true "full stack" developer would have to be an expert in everything to create a modern website

=====

# Page Layout

NOTES:
- Before CSS3, flexbox & grid we needed ways to lay out our pages
- And many times we had some navigation that we wanted fixed
  * Either a header menu on top
  * Left nav
  * Or in the case of my site I thought a fixed nav footer was a good idea
- Now you may think I'm talking about using `<table>`s, but no!
- I'm talking about page layouts that pre-dated `<table>`

/////

```html
<FRAMESET ROWS="150px,*">
  <FRAME NORESIZE SRC="header.html" MARGINHEIGHT=15>
  <FRAMESET COLS="20%,*,20%">
    <FRAME SRC="nav.html" FRAMEBORDER=0>
    <FRAME SRC="home.html" FRAMEBORDER=0 NAME=content>
    <FRAME SRC="ads.html" FRAMEBORDER=0>
  </FRAMESET>
</FRAMESET>
```
<!-- .element: class="large" -->


NOTES:
- Talking about `<frameset>`
- Before I even try to explain the code, take a look at this HTML!
- It's in ALL-CAPS
- Attributes like `MARGINHEIGHT` & `FRAMEBORDER` aren't even quoting the values
- Fun times!

/////
<!-- .slide: data-background="url(../../img/webdev/frameset-borders-margins.jpg) no-repeat center" data-background-size="contain" -->

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

```html
<FRAMESET ROWS="150px,*">
  <FRAME NORESIZE SRC="header.html" MARGINHEIGHT=15>
  <FRAMESET COLS="20%,*,20%">
    <FRAME SRC="nav.html" FRAMEBORDER=0>
    <FRAME SRC="home.html" FRAMEBORDER=0 NAME=content>
    <FRAME SRC="ads.html" FRAMEBORDER=0>
  </FRAMESET>
</FRAMESET>
```
<!-- .element: class="large" -->


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
- **SEVEN:** So what about that `NAME` attribute? What's that for

/////

nav.html
```html
<HTML>
  <BODY>
    <UL>
      <LI><A HREF="home.html" TARGET=content>Home</A></LI>
      <LI><A HREF="about.html" TARGET="content">About</A></LI>
      <LI><A HREF="help.html" TARGET="content">Help</A></LI>
    </UL>
  </BODY>
</HTML>
```
<!-- .element: class="large" -->

NOTES:
- Well in addition to having our grid layout, we also don't want to have to refresh the whole page
- The header, nav & ads are staying fixed
- So w/in `nav.html`, we just have our links target the `content` frame
  * You've probably always just done `target="_blank"` for a new window right?
  * It had a purpose!

/////

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

NOTES:
- If you've been keeping up with the latest in CSS-land
  * This sounds awfully similar to CSS Grid that's becoming progressively more avilable in browsers
- Here's how we could implement the same thing now
- Notice how `<main>` actually comes before `<nav>` in the markup
  * For SEO
  * But Grid layout puts it where we want visually!

=====

=====

# Shoutout to bootcamp grads

=====

# THANKS!

![Animated clay men bowing](../../img/giphy/animated-take-a-bow.gif)
<!-- .element: style="width: 35%" -->

## Ben Ilegbodu

[benmvp.com](/) | [@benmvp](https://twitter.com/benmvp) | [ben@benmvp.com](mailto:ben@benmvp.com)  
[github/benmvp](https://github.com/benmvp)
<br /><br />

Ask me anything! [benmvp.com/ama](http://www.benmvp.com/ama/)

NOTES:
- So that's it!
- Ask questions on Twitter, via email or AMA!
- Thanks!
