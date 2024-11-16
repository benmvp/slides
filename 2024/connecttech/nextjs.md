<!-- markdownlint-disable MD034 -->

<!-- .slide: data-state="title-page" data-background="url(../../img/nextjs/sunglasses-dmitry-mishin-KE_xElQyQhQ-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 50%;" class="content-overlay">

  <h1>50 Shades of React Rendering with Next.js</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=ct-2024) | [#@connect_js](https://twitter.com/connect_js)</p>

  <br />

  <p>November 19, 2024</p>

  </div>
</div>

NOTES:

- Let's start with a show of hands
  - ✋🏾 Who here uses React currently?
  - ✋🏾 Of y'all, who here uses Next.js?
- I've been using Next for several years now
  - And got really into understanding how it all worked
  - So this talk is basically a distillation of a lot of what I learned

**RESTART THE TIMER!!!!**

/////

<!-- .slide: data-background="#222" data-background-size="cover" -->

<a href="https://benmvp.com/ato-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=ato-2023" target="_blank">
  <img src="../../img/qrcodes/ct-2024-nextjs.svg" style="width: 40%" alt="QR code for &quot;50 shades of React rendering with Next.js&quot; talk @ Connect.Tech 2024" class="plain" />
</a>

<p>
  <a href="https://benmvp.com/ct-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=ct-2024" target="_blank">
    benmvp.com/ct-nextjs
  </a>
</p>

NOTES:

- I want to let you know that these slides are already available online
  - So if you want to follow along or can't see well from the back, I've got you covered
- You can use this handy dandy QR code that'll take you to the slides
- You can go to my website, `benmvp.com`, and find them there too
- AND I've already tweeted a link to my slides, **@benmvp**
- So you're covered with **four** different ways to access the slides!

=====

<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>React supports multiple renderers</h2>

    <pre class="large"><code class="lang-typescript">// src/client/index.js

import React from 'react'

const App = () => {
  // render app UI
}

React.render(
  document.getElementById('root'),
  &lt;App />
)</code></pre>

    <div class="code-highlight" style="height: 240px; top: 629px;"></div>

  </div>
</div>

NOTES:

- When React burst on the scene in early 2015, it was a game changer for many reasons
- Other UI libraries of the day attached their UI directly to the DOM
  - Think jQuery, Backbone and those flavors from way back when
  - Everything operated on the DOM
- React on the other hand **separated the UI** from the rendering
- And because of this, the generated UI could be rendered in multiple different ways...
  - By using different renders
- **React Native** works because React can be rendered in a mobile environment
- **Netflix** and other streaming providers can also use React...
  - because they've built proprietary renderers for TVs
- And here we have what was (and still is) the most common renderer...
  - The Web renderer that attaches the UI into a browser DOM element

/////

<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>React can even render to a string</h2>

    <pre class="large"><code class="lang-typescript">// src/server/index.js

import React from 'react'

const App = () => {
  // render app UI
}

const html = React.renderToString(&lt;App />)</code></pre>

    <div class="code-highlight" style="height: 70px; top: 629px;"></div>

  </div>
</div>

NOTES:

- **Next.js** capitalized on another one of React's renderers
  - The ability to **render** to a string, allowing for server-side rendering
  - This was the "isomorphic React" revolution
  - The ability to render the same UI on the server as well as in the browser
- Next actually started way back in 2016, focusing mainly on server-side rendering
  - It was created by Vercel's founder, Guillermo Rauch
  - Although back then Vercel was still called ZEIT
- The simplified version of how it works is...
  - The UI is rendered to a string on the server & returned in the response
  - And then **"hydrated"** in the browser by attaching event handlers and such

/////

<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%;">
    <img src="../../img/nextjs/nextjs-logo-light.svg" alt="Logo for Next.js" class="plain" />
  </div>
</div>

NOTES:

- Around Next 9 (2019), Next started emphasizing pre-rendering at build time
- So not only could we render server-side...
  - but now before the server even started
- Ever since then, Next has been adding more functionality...
  - with the page-based router
  - to provide us more and more ways to render the pages within our apps

/////

<!-- .slide: data-background="url(../../img/nextjs/pages-vs-app-router.png) no-repeat center" data-background-size="cover" -->


NOTES:

- But then with Next 13 (October 2022) Next introduced the App Router
- It ultimately generates the same types of pages
  - But it improves the Developer Experience for sophisticated layouts & routes
- With Next 14 (October 2023) it became ready for primetime
- So I want to take our remaining time to showcase a few of the more popular rendering strategies

=====

<!-- .slide: data-background="url(../../img/giphy/stand-up-steph-curry.gif) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1 style="font-size: 5em">Stand Up!</h1>
  </div>
</div>

NOTES:

- But before we continue any further can I get everyone to stand up?

/////

<!-- .slide: data-background="#222" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 45%">
    <img src="../../img/family/family-house-selfie-imani.jpg" alt="Photo of the Ilegbodu family at home" />
  </div>
</div>

NOTES:

- My name is Ben Ilegbodu
  - Christian, Husband, Father
- _Family introductions_
- We live in Manvel, TX (suburb of Houston)

/////

<!-- .slide: data-background="#222" -->

<div style="display:flex;align-items:center;justify-content:space-around;">
  <div style="flex:0 0 45%; margin-right: 20px">
    <img src="../../img/netflix/netflix-logo.png" alt="Stitch Fix Corporate logo (light)" class="plain" />
  </div>
  <div style="flex:0 0 45%">
    <img src="../../img/gde/experts-sticker-01.gif" alt="Google Developer Experts animation" class="plain" style=" background-color: #ddd; border-radius: 5px"/>
  </div>
</div>

NOTES:

- I'm a Google Developer Expert in Web Technologies
- Also currently a Senior Software Engineer at Netflix

=====

<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%">
    <img src="../../img/nextjs/sample-blog-post.png" alt="Screenshot of a blog post example" style="width: 60%" />

    <p><a href="https://nextjs-rendering.benmvp.com/" target="_blank">https://nextjs-rendering.benmvp.com/</a></p>

  </div>
</div>

NOTES:

- OK, enough about me...

=====

<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Client-side rendering (CSR)</h1>
    <p>Page HTML is rendered in the <em>browser</em> for <u>every request</u></p>
  </div>
</div>

NOTES:

- First let's start with CSR better known as **client-side rendering**
- Client-side rendering is how single-page apps (SPAs) started out
  - It's probably the most common rendering strategy
  - In fact, Create React App is like this still

/////

<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
  <div class="content-overlay" style="width: 80%">
    <div style="display:flex;align-items:center;justify-content:space-around;">
      <div style="flex:0 0 45%">

        <h3>Advantages</h3>
          <p>Dynamic content (user-specific)</p>
          <p>Fast initial response times</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Poor SEO & UI cache</p>
          <p>Slow render times</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>Interactive dashboards</p>
          <p>3rd-party widgets</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20p; position: relative">
    <pre class="large"><code class="lang-typescript">// app/posts/[slug]/page.tsx

'use client'

function Page() {
  useEffect(() => {
    // browser fetch
    // browser APIs
    // update state
  }, [])
}</code></pre>

    <div class="code-highlight" style="height: 70px; top: 144px; width: 100%; left: 0"></div>

<p><a href="https://github.com/benmvp/nextjs-rendering/blob/main/src/app/posts-csr/%5Bslug%5D/page.tsx" target="_blank">CSR Example</a></p>
<p><a href="https://nextjs.org/docs/app/building-your-application/rendering/client-components" target="_blank">Client Components</a></p>

</div>
</div>

  </div>
</div>

NOTES:

- So CSR is great for **dynamic content**
  - And since the page is mostly blank initially, the **server response is fast**
- However, because everything is rendered in the browser...
  - **render times are slow** especially since they wait on the API response
  - This is further magnified on lower-end mobile devices
  - **SEO is generally worse** too because there's no HTML markup for the search engine
  - Similarly there's no real markup to **cache in a CDN**

---

- So while CSR will totally work for this blog post...
  - I ideally wouldn't use it for this
  - SEO is too important & the client needs to see _something_ quickly
- Instead, full CSR is great for UIs like highly-interactive, user-specific dashboards
  - Think Figma or task managers like Asana
- It's also good for pages that rely heavily on browser-based 3rd-party widgets
  - Like embedding a Stripe checkout widget
- But we'll see in a bit that we can sprinkle CSR within our other rendering strategies

=====

<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: start">
  <div class="content-overlay">
    <h1>Server-side rendering (SSR)</h1>
    <p>Page HTML is generated on the <em>server</em> for <u>every request</u></p>
  </div>
</div>

NOTES:

- Ok, let's move to what's likely the most prevalent form of rendering
  - **Server-side rendering**
- You may have also heard terms like "SSR" or "Dynamic rendering"

/////

<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-start">
  <div class="content-overlay" style="width: 80%">

    <div style="display:flex;align-items:center;justify-content:space-around;">
      <div style="flex:0 0 45%">

        <h3>Advantages</h3>
          <p>Dynamic content (user-specific)</p>
          <p>Fast browser render times</p>
          <p>SEO-friendly</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Slow server response times</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>Dynamic product listings & pages</p>
          <p>Search results pages</p>
          <p>Cart & checkout pages</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px; position: relative;">
    <pre class="large"><code class="lang-typescript">// app/posts/[slug]/page.tsx

async function Page() {
  // auto-SSR when using
  // headers/cookies/etc
  const h = await headers()

 // SSR fetch
  await fetch(...)
}</code></pre>


    <div class="code-highlight" style="height: 70px; top: 314px; width: 100%; left: 0"></div>

<p><a href="https://github.com/benmvp/nextjs-rendering/blob/main/src/app/posts-ssr/%5Bslug%5D/page.tsx" target="_blank">SSR Example</a></p>
<p><a href="https://nextjs.org/docs/app/building-your-application/rendering/server-components#dynamic-rendering" target="_blank">Dynamic Server Components</a></p>
</div>
</div>

  </div>
</div>

NOTES:

- Similar to client-side rendering, SSR is also great for **dynamic content**
  - Because its data is retrieved on the server for **every request**
- And because the full UI is in the HTML response...
  - It's very **SEO-friendly** - crawlers have everything they need
  - **In-browser render times** are also fast because of all the HTML is there
- But... it comes as the cost of **slow response times**
  - While the server is likely fast at rendering HTML
  - It's got to wait on the API response
  - So the user doesn't see _anything_ until the full response is complete

---

- So if this blog post had frequently changing content
  - Then SSR could be a good fit
  - But if the data was mostly static, it'd be overkill & a sub-optimal render experience
- In general SSR is good for pages that either...
  - 1/ Have data that could change with every render
  - 2/ Or the page is mostly user-specific content
  - So think search results, checkout flows, etc

=====

<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Static-site generation (SSG)</h1>
    <p>Page HTML is <b>pre-rendered</b> at <u>build time</u></p>
  </div>
</div>

NOTES:

- Now let's talk about **static-site generation**
- SSG became super popular in React around 2019 thanks to Gatsby
  - And Next.js later joined the party, electing to make **all pages static by default**
- Technically SSG started with Jekyll back in the day
  - But it's in Ruby so we don't care 😆

/////

<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
  <div class="content-overlay" style="width: 80%">

    <div style="display:flex;align-items:center;justify-content:space-around;">
      <div style="flex:0 0 45%">

        <h3>Advantages</h3>
          <p>SEO-friendly</p>
          <p>Highly cacheable</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Dynamic content (user-specific)</p>
          <p>Slow build times</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>Marketing pages</p>
          <p>Blog posts</p>
          <p>Static product listings & pages</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px">
    <pre class="large"><code class="lang-typescript">// app/posts/[slug]/page.tsx

generateStaticParams() {
  // build list of pages
}

async function Page() {
  // SSG fetch
  await fetch(...)
}</code></pre>

<p><a href="https://github.com/benmvp/nextjs-rendering/blob/main/src/app/posts-ssg/%5Bslug%5D/page.tsx" target="_blank">SSG Example</a></p>
<p><a href="https://nextjs.org/docs/app/building-your-application/rendering/server-components#static-rendering-default" target="_blank">Static Server Components</a></p>
<p><a href="https://nextjs.org/docs/app/api-reference/functions/generate-static-params" target="_blank"><code>generateStaticParams</code></a> function</p>
<p><a href="https://nextjs.org/docs/app/api-reference/functions/not-found" target="_blank"><code>notFound</code></a> function</p>
</div>
</div>

  </div>
</div>

NOTES:

- The appeal of static rendering is that it's **super fast**
  - The HTML is already ready when the user requests it
  - In fact it can be **cacheable by CDNs** because it's the same for everybody
  - But the flip side of the coin is that it results in **slower build times**...
  - because all of these pages have to built before the server even runs
- However like SSR it's also **SEO-friendly** because all of the HTML is there
- The idea with SSG is that there's a single page file for everyone...
  - So **dynamic or user-specific data** can be tricky
  - We can of course make API requests in the browser for the dynamic content...
  - but then we may miss out on SSG's cacheability goodness
- It takes planning and forethought to get a hybrid page rendered with the right mix of static & dynamic using SSG

---

- So if we wanted to use SSG for our blog post...
  - We can render all the UI at build time
  - Then in the browser we can retrieve the recommended posts
- So for this dynamic stuff...
  - we pre-render statically w/ default data or loading states
  - And sync w/ up-to-date data in the browser
- We've created a hybrid page
- But in general, SSG is best & simplest for logged out pages...
  - Where the page is typically the same for everyone
- Things like marketing landing pages, blog posts, etc
  - Or even product listings or product details page if they rarely changed

=====

<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Incremental static regeneration (ISR)</h1>
    <p>Page HTML is <u>regenerated</u> on the <b?>server</b> after cache timeout</p>
  </div>
</div>

NOTES:

- So we've talked about CSR, SSR & just now SSG
  - Lemme confuse you by adding one more acronym 😆
- As I mentioned, the trouble with SSG is that it's built once
- We like that it's super fast because it's cacheable...
  - But the rendered HTML never changes until we trigger a rebuild
- Here's where **incremental static regeneration** aims to improve SSG
- It brings the server back to the static party 🎉

/////

<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-start">
  <div class="content-overlay" style="width: 80%">

    <div style="display:flex;align-items:center;justify-content:space-around;">
      <div style="flex:0 0 45%">

        <h3>Advantages</h3>
          <p>SEO-friendly</p>
          <p>Fast initial load times</p>
          <p>Allows for periodic data updates</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Dynamic, user-specific content</p>
          <p>Slow build times</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>Headless CMS pages</p>
          <p>Periodically-updating product listings & pages</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px">
    <pre class="large"><code class="lang-typescript">// app/posts/[slug]/page.tsx

generateStaticParams() {
  // build list of pages
}

// refresh after 15
export const revalidate = 15

async function Page() {
  // SSG fetch
  await fetch(...)
}</code></pre>

<p><a href="https://github.com/benmvp/nextjs-rendering/blob/main/src/app/posts-isr/%5Bslug%5D/page.tsx" target="_blank">ISR Example</a></p>
<p><a href="https://nextjs.org/docs/app/building-your-application/data-fetching/incremental-static-regeneration" target="_blank">Incremental Static Regeneration</p>
<p><a href="https://nextjs.org/docs/app/api-reference/file-conventions/route-segment-config#dynamicparams" target="_blank"><code>dynamicParams</code></a> property</p>

</div>

  </div>
</div>

NOTES:

- ISR has all the same advantages and disadvantages as SSG
  - The huge difference is that the pre-rendered HTML can actually **update w/o requiring a rebuild**

---

- ISR would work great for our blog posts
- Everyone is still getting the same blog post
- But if we're adding/updating content w/ a CMS
  - We don't want to have to rebuild each time the content changes
  - That was the drawback of the static site builders
- ISR is best for pages that are the same for everyone but need to update regularly
  - I'm thinking of headless CMS pages where UI changes can be hands-off by Engineering
  - Or semi-static product listings & pages
  - They need to be able to update, but they aren't different on every request either

=====

<!-- .slide: data-background="url(../../img/nextjs/mockups-hal-gatewood-weRQAu9TA-A-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>One site, many render modes</h2>

    <div style="columns:2;-webkit-columns:2;-moz-columns:2;margin-top: 1em">
      <h3>Static Site Generation</h3>
        <p>Blog</p>
        <p>Login</p>
        <p>Onboarding</p>

      <h3 style="margin-top: 5rem">Incremental Static Regeneration</h3>
        <p>Product details</p>
        <p>CMS-driven pages</p>

      <h3>Server-side Rendering</h3>
        <p>Shopping cart</p>
        <p>Order history</p>
        <p>Search results</p>

      <h3 style="margin-top: 5rem">Client-side Rendering</h3>
        <p>Deferred UI</p>
        <p>Shipment tracking</p>
        <p>3rd-party checkout</p>
    </div>

  </div>
</div>

NOTES:

- Next.js isn't _just_ a client-side renderer like CRA
- It's not _just_ a static-site generator like Gatsby
- It's not even _just_ a server-side renderer like... OG Next
- It's all of them!
  - And the beauty is that any given page can use a different render mode
- I just went through the 4 most popular modes
  - But we can configure pages to be various combinations too
  - The combinations are endless!
- Honestly, we probably could build every page with any of these render modes...
  - But some lend themselves better to certain types of pages

---

- So for our one e-commerce site...
  - Maybe the **login, onboarding & blog pages** use SSG
  - ISR would be good for **product detail pages & landing pages** because they're static, but could change outside of the build cycle
  - **Search results pages, shopping cart, order history**, and other user-tailored pages are likely good candidates for SSR
  - And finally CSR for **3rd-party checkout, the shipment tracking page**, and any secondary UI that can be loaded after the main page renders

=====

<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Layouts &amp; Templates</h1>

    <p>Create UI that is shared between multiple routes</p>
  </div>
</div>

NOTES:

/////

<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Component Composition</h1>

    <p>Maximize how much UI is rendered server-side</p>
  </div>
</div>

NOTES:

/////

<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Loading UI &amp; Streaming</h1>

    <p>Automatically show a loading state while a route segment loads</p>
  </div>
</div>

NOTES:

/////

<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Partial Pre-rendering</h1>

    <p>(Experimental) Combine static and dynamic components together in the same route</p>
  </div>
</div>

NOTES:

/////

<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>Server Actions</h1>

    <p>Handle form submissions with server-side async functions</p>
  </div>
</div>

NOTES:

=====

<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://github.com/benmvp/nextjs-rendering" target="_blank"><code>nextjs-rendering</code></a> Github repo</li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/routing/layouts-and-templates" target="_blank">Layouts &amp; Templates</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/rendering/composition-patterns" target="_blank">Component composition</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/rendering/partial-prerendering" target="_blank">Partial Pre-rendering (PPR)</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/routing/loading-ui-and-streaming" target="_blank">Loading &amp; Streaming</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations" target="_blank">Server Actions</a></li>

      <li><a href="https://nextjs.org/docs/app/building-your-application/rendering/server-components" target="_blank">Server components</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/rendering/client-components" target="_blank">Client components</a></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/data-fetching/incremental-static-regeneration" target="_blank">Incremental Static Regeneration</a></li>
      <li><a href="https://nextjs.org/docs/app/api-reference/functions/generate-static-params" target="_blank"><code>generateStaticParams</code></a></li>
    </ul>

  </div>
</div>

NOTES:

- So I know I just hit you with a bunch of information
- Get these slides so you can click through to all of these resources
- The first is actually a blog I wrote about this topic a few years ago now
- The rest are guides and docs from the official Next.js site
  - "On-demand incremental static rengeration" is like ISR, but with a sort of webhook

=====

<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=ct-2024" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  <br />

  <a href="https://benmvp.com/bit-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=ct-2024" target="_blank">
    <img src="../../img/qrcodes/ct-2024-nextjs.svg" style="width: 50%" alt="QR code for &quot;Next.js rendering&quot; talk at Connect.Tech 2024" class="plain" />
  </a>

  </div>
</div>

NOTES:

- So as I wrap up...
  - I encourage you to give Next.js a try
- Or if you already have...
  - Evaluate whether the pages you have are using the best rendering strategy
- I should be around for the remainder of the conference...
  - So find me later or you can ask me questions on Twitter (@benmvp)
- Thanks!
