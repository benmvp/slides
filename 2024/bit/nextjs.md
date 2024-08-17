<!-- markdownlint-disable MD034 -->

<!-- .slide: data-state="title-page" data-background="url(../../img/nextjs/sunglasses-dmitry-mishin-KE_xElQyQhQ-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 50%;" class="content-overlay">

  <h1>50 Shades of React Rendering with Next.js</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=bit-2024) | [#BlackIsTech](https://twitter.com/hashtag/blackistech)</p>

  <br />

  <p>August 19, 2024</p>

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

=====
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>React supports multiple renderers</h2>

        <pre class="large"><code class="lang-typescript">// src/client/index.js
const App = () => {
  // render app UI
}

const root = ReactDOM.createRoot(
  document.getElementById('root')
)

root.render(&lt;App />) // flush to DOM

React.renderToString(&lt;App />) // or to string

MyRenderer.render(&lt;App />) // etc</code></pre>

    <div class="code-highlight" style="height: 70px; top: 805px;"></div>

  </div>
</div>

NOTES:

- When React burst on the scene in early 2015, it was a game changer for many reasons
- Other UI libraries of the day attached their UI directly to the DOM
  - Think jQuery, Backbone and those flavors from way back when
  - Everything operated on the DOM
- React on the other hand **separated the UI** from the rendering
  - It figured out the changes in memory
  - And then flushed them to the DOM
- And because of this, the generated UI could be rendered in multiple different ways...
  - By using different renders
- **React Native** works because React can be rendered in a native mobile environment
- **Netflix** and other streaming providers can also use React...
  - because they've built their own renderers for TVs
- And here we have what was (and still is) the most common renderer...
  - The Web renderer that attaches the UI into a browser DOM element

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
  - but also before the server even started
- Ever since then, Next has been adding more functionality...
  - to provide us more and more ways to render the pages within our apps
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
  <div class="content-overlay" style="width: 65%">
    <img src="../../img/family/family-kalahari.jpg" alt="Photo of the Ilegbodu family at Kalahari" />
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
- Let's take a look at this product details page (aka PDP) within our made up e-commerce site
  - It's got the title & main product images
  - The price
  - The size selector (which may or may not be out-of-stock)
  - The add-to-cart button (which or may not be enabled)
  - The carousel of related products at the bottom
  - And the header & footer
- I want us to keep all of this in mind
  - Because we'll be using this PDP as our example for the code
- **ONE:** Oh and before we begin,
- Next.js uses what's called **file-system based routing** w/ the Pages Router
  - Meaning that if we want this PDP at the URL `/product/acme-hoodie`
  - We'll put the page React component within `src/pages/product/`
- It also supports **dynamic routes**
  - So if we want to support having multiple pages within `/product/`...
  - we can use `[id]` notation for the name
  - And `acme-hoodie` would be one of the ids, as well as any other product in our site
- Without further ado, let's dive in...

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
          <p>Fast server response times</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Poor SEO & UI cache</p>
          <p>Slow render times</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>Interactive dashboards</p>
          <p>3rd-party widgets</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px">
    <pre class="large"><code class="lang-typescript">// pages/posts/[slug].tsx

useEffect(() => {
  // browser fetch
}, [])</code></pre>
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

-----

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
          <p>Checkout pages</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px">
    <pre class="large"><code class="lang-typescript">// pages/posts/[slug].tsx

getServerSideProps() {
  // server fetch
}</code></pre>
        <p><a href="https://nextjs.org/docs/pages/building-your-application/data-fetching/get-server-side-props" target="_blank"><code>getServerSideProps</code></a> function</p>
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

-----

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
- SSG became super popular around 2019 thanks to Gatsby
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
    <pre class="large"><code class="lang-typescript">// pages/posts/[slug].tsx

getStaticPaths() {
  // build list of pages
}

getStaticProps() {
  // build time fetch
}</code></pre>
        <p><a href="https://nextjs.org/docs/pages/building-your-application/data-fetching/get-static-paths" target="_blank"><code>getStaticPaths</code></a> function</p>
        <p><a href="https://nextjs.org/docs/pages/building-your-application/data-fetching/get-static-props" target="_blank"><code>getStaticProps</code></a> function</p>
        <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-false" target="_blank"><code>fallback</code></a> property</p>
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

-----

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
- It brings the server back to the party 🎉

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
    <pre class="large"><code class="lang-typescript">// pages/posts/[slug].tsx

getStaticPaths() {
  // build list of pages
}

getStaticProps() {
  // build time fetch
  // + revalidate
}</code></pre>
        <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-props#revalidate" target="_blank"><code>revalidate</code></a> property</p>
        <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-blocking" target="_blank"><code>fallback</code></a> property</p>
      </div>
    </div>
  </div>
</div>

NOTES:

- ISR has all the same advantages and disadvantages as SSG
  - The huge difference is that the HTML can actually **update w/o requiring a rebuild**
- Maybe for the PDP we want the size availability to always be up-to-date...
  - so we still make that API call in the browser for every page request
- But if we're ok with the price or the related products to be stale for a bit...
  - We could pre-render those UI pieces without having to call the API in the browser
  - Then once the cache expired, we'd get the a **new pre-rendered page** w/ updated data
  - This provides a faster UX
- If the data or imagery changed, those would get updated too
- Like static-site generation, ISR works best for pages that should be the same for everyone...
  - but the difference is the data frequency needs
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

-----

- So for our one e-commerce site...
  - Maybe the **login, onboarding & blog pages** use SSG
  - ISR would be good for **product detail pages & landing pages** because they're static, but could change outside of the build cycle
  - **Search results pages, shopping cart, order history**,  and other user-tailored pages are likely good candidates for SSR
  - And finally CSR for **3rd-party checkout, the shipment tracking page**, and any secondary UI that can be loaded after the main page renders

=====
<!-- .slide: data-background="url(../../img/nextjs/complexity-timo-volz-9Psb5Q1TLD4-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h1>App Router</h1>
    <p>Optimally statically, dynamically or stream render</p>
  </div>
</div>

NOTES:



/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
  <div class="content-overlay" style="width: 80%">

    <div style="display:flex;align-items:center;justify-content:space-around;">
      <div style="flex:0 0 45%">

        <h3>Advantages</h3>
          <p>Data-driven &quot;auto&quot; rendering</p>
          <p>Sophisticated layouts/routing</p>

        <h3 style="margin-top: 5rem">Disadvantages</h3>
          <p>Component complexity</p>
          <p>Server setup complexity</p>

        <h3 style="margin-top: 5rem">Good candidates</h3>
          <p>All</p>
      </div>
      <div style="flex:0 0 45%; margin-right: 20px">
    <pre class="large"><code class="lang-typescript">// app/posts/[slug]/page.tsx
async function Page() {
  // async in component!
  await getPost(slug)
}

// components/RecPosts.tsx
function RecPosts() {
  return (
    &lt;Suspense>
      &lt;DeferedRecPosts />
    &lt;/Suspense>
  )
}</code></pre>
      </div>
    </div>
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
      <li><a href="https://www.benmvp.com/blog/50-shades-react-rendering-nextjs/?utm_source=benmvp&utm_medium=slides&utm_campaign=bit-2024" target="_blank"><em>50 shades of React rendering with Next.js</em></li>
      <li><a href="https://nextjs.org/docs/app/building-your-application/rendering/server-components" target="_blank">Client & server components</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/server-side-rendering" target="_blank">Server-side rendering with Next.js</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/static-site-generation" target="_blank">Static-site generation</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/incremental-static-regeneration" target="_blank">Incremental static regeneration</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/incremental-static-regeneration#on-demand-revalidation" target="_blank">On-demand Incremental static regeneration</li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-server-side-props" target="_blank"><code>getServerSideProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths" target="_blank"><code>getStaticPaths</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-props" target="_blank"><code>getStaticProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/use-router" target="_blank"><code>useRouter</code></li>
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

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=bit-2024" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  <br />

  <a href="https://benmvp.com/bit-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=bit-2024" target="_blank">
    <img src="../../img/qrcodes/bit-2024-nextjs.svg" style="width: 50%" alt="QR code for &quot;Next.js rendering&quot; talk at Black is Tech 2024" class="plain" />
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
