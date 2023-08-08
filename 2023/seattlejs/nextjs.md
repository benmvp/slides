<!-- markdownlint-disable MD034 -->

<!-- .slide: data-state="title-page" data-background="url(../../img/nextjs/sunglasses-dmitry-mishin-KE_xElQyQhQ-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 45%;" class="content-overlay">

  <h1>50 shades of React rendering with Next.js</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023) | [#SeattleJSConf](https://twitter.com/hashtag/SeattleJSConf)</p>

  <br />

  <p>August 8, 2023</p>

  </div>
</div>

NOTES:

- ✋🏾 Who here uses React?
  - ✋🏾 Of y'all, who here uses Next.js?
- I've been using Next for several years now
  - And got really into understanding how it all worked
  - So this talk is basically a distillation of a lot of what I learned

**RESTART THE TIMER!!!!**

/////
<!-- .slide: data-background="#222" data-background-size="cover" -->

<a href="https://benmvp.com/seattlejs-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023" target="_blank">
  <img src="../../img/qrcodes/seattlejs-2023-nextjs.svg" style="width: 40%" alt="QR code for &quot;50 shades of React rendering with Next.js&quot; talk" class="plain" />
</a>

<p>
  <a href="https://benmvp.com/seattlejs-nextjs?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023" target="_blank">
    benmvp.com/seattlejs-nextjs
  </a>
</p>

NOTES:

- I want to let you know that these slides are already available online
  - So if you want to follow along or can't see well from the back, I've got you covered
- You can use this handy dandy QR code that'll take you to the slides
- You can go to my website, `benmvp.com`, and find them there too
- So you're covered with **three** different ways to access the slides!

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

    <div class="code-highlight" style="height: 240px; top: 577px;"></div>
  </div>
</div>

NOTES:

- When React burst on the scene in 2015, it was a game changer for many reasons
- Other UI libraries of the day attached their UI directly to the DOM
  - Think jQuery or Backbone if you were around back then
  - Everything operated on the DOM
- React on the other hand **separated the UI** from the rendering
- And because of this, the generated UI could be rendered in multiple different ways...
  - Using different renders
- **React Native** works because React can be rendered in a mobile environment
- **Netflix** and other streaming providers can also use React...
  - because they've built renders for TVs
- And here we have what was and still is the most common render...
  - The Web render that attaches the UI into a browser DOM element

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

    <div class="code-highlight" style="height: 70px; top: 577px;"></div>
  </div>
</div>

NOTES:

- **Next.js** capitalized on another one of React's renderers
  - The ability to **render** to a string allowing for server-side rendering
  - This was the "isomorphic React" revolution
  - The ability to render the same UI on the server as well as in the browser
- Next actually started way back in 2016, focusing mainly on server-side rendering
  - It was created by Vercel's founder, Guillermo Rauch
  - Although back then Vercel was called ZEIT
- The simplified version of how it works is...
  - The UI is rendered to a string on the server
  - And then **"hydrated"** in the browser by attaching event handlers and such

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%;">
    <img src="../../img/nextjs/nextjs-logo-dark.svg" alt="Logo for Next.js" class="plain" />
  </div>
</div>

NOTES:

- Around Next 9 (2019), Next started emphasizing pre-rendering at build time
- So not only could we render server-side...
  - but before the server even started
- Ever since then, Next has been adding more functionality...
  - To provide us more and more ways to render the pages within our apps
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
    <img src="../../img/family/family-fathers-day.jpeg" alt="Photo of the Ilegbodu family on Father's Day" />
  </div>
</div>

NOTES:

- My name is Ben Ilegbodu
  - Christian, Husband, Father
- _Family introductions_
- We live in Manvel, TX (suburb of Houston)
- My wife is actually here with me
  - She tagged along for us to celebrate our 13th wedding anniversary

/////
<!-- .slide: data-background="#222" -->

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
<!-- .slide: data-background="#222 url(../../img/nextjs/sample-product-page.png) no-repeat top right 5%" data-background-size="contain" -->

<div style="display:flex; justify-content: flex-start" class="fragment current-visible">
  <div class="content-overlay">
    <p>https://acme.store/product/acme-hoodie</p>

    <pre class="large"><code class="lang-typescript">
// src/pages/product/[id].tsx

</code></pre>
  </div>
</div>

NOTES:

- OK, enough about me...
- Let's take a look at this product details page (aka PDP) within our made up e-commerce site
  - It's got the title & main product images
  - The price
  - The sizes (which may or may not be out-of-stock)
  - The add-to-cart button (which or may not be enabled)
  - The carousel of related products at the bottom
  - And the header & footer
- I want us to keep all of this in mind
  - Because we'll be using this PDP as our example for the code
- **ONE:** Oh and before we begin,
- Next.js uses what's called **path-based routing**
  - Meaning that if we want this product details page at `/product/acme-hoodie`
  - We'll put the page React component within `src/pages/product/`
- It also supports **dynamic path-based routing**
  - So if we want to support having multiple pages within `/product`...
  - we can use `[id]` for the name
  - And `acme-hoodie` would be one of the ids as well as any other product in our site
- Without further ado, let's dive in

=====
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Client-side rendering (CSR)</h1>
  </div>
</div>

NOTES:

- First let's start with CSR better know as **client-side rendering**

/////
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <p>Page HTML is rendered in the <u>browser</u></p>

    <pre class="large"><code class="lang-typescript">const ProductPage = () => {
  const [data, setData] = useState(undefined);
  const { query } = useRouter()

  useEffect(() => {
    fetch(\`api.acme.com/products/${query.id}/\`)
      .then(res => res.json())
      .then(data => setData(data))
  }, [])

  return <p>{data ? \`The data ${data}\` : 'Loading...'}</p>
}
export default ProductPage</code></pre>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 855px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 740px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 279px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 298px; top: 394px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 740px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 451px;"></div>
  </div>
</div>

NOTES:

- So within that component file (`src/pages/product/[id].tsx`)...
  - **ONE:** The default export is the page component
- Client-side rendering (aka CSR) is how single-page apps (SPAs) started out
  - It's probably the most common rendering strategy
  - Create React App is like this still
- **TWO:** For our product details page, Next will pre-render a minimal HTML file at build time
  - In this case, it'll have our loading state
- **THREE:** It grabs the `id` from the URL (based on `[id]`)...
  - and puts in the `query` object returned by Next's built-in router
- **FOUR:** Then the after the product API is called in `useEffect`...
  - **FIVE:** Next.js JavaScript will **render the page in the browser**
- **SIX:** Here's the thing... because the API is called every time the page renders...
  - The **data** can be constantly changing or even user-specific
  - The **size selector** availability data can change
  - The **product** can go on sale
  - The **header** can show logged-in status
  - And everything will be immediately reflected for the next page request
- More than likely the related product carousel would be loaded as a separate API + render

/////
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
 <div class="content-overlay">

    <h3>Advantages</h3>
      <p>Dynamic content (user-specific)</p>
      <p>Fast response times</p>

    <h3 style="margin-top: 5rem">Disadvantages</h3>
      <p>Slow render times</p>
      <p>Poor SEO & UI cache</p>

    <h3 style="margin-top: 5rem">Good candidates</h3>
      <p>Interactive dashboards</p>
      <p>3rd-party widgets</p>
  </div>
</div>

NOTES:

- So CSR is great for **dynamic content**
  - And since the page is mostly blank initially the **response is fast**
- However, because everything is rendered in the browser...
  - **render times are slow** especially since they wait on the API response
  - This is magnified on lower-end devices
  - **SEO is generally worse** too because there's no HTML markup for the search engine
  - Similarly there's no real markup to **cache in a CDN**

- So while CSR will totally work for the PDP...
  - And many sites use it for PDPs...
  - I ideally wouldn't use it for this PDP
  - SEO is too important & the client needs to see _something_ quickly
- Instead CSR is great for UIs like highly-interactive, user-specific dashboards
  - Think Figma or task managers like Asana
- It's also good for pages that rely heavily on browser-based 3rd-party widgets
  - Like embedding a Stripe checkout widget

=====
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: start">
  <div class="content-overlay">
    <h1>Server-side rendering (SSR)</h1>
  </div>
</div>

NOTES:

- Ok, let's move to what's likely the most prevalent form of rendering
  - **Server-side rendering**
- You may have also heard terms like "SSR" or "Dynamic rendering"

/////
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <p>Page HTML is generated on the server for <u>every request</u></p>

    <pre class="large"><code class="lang-typescript">export const getServerSideProps = async ({ params }) => {
  const apiUrl = \`api.acme.com/products/${params.id}/`
  const res = await fetch(apiUrl)
  const data = await res.json();

  return { props: { data } }
}

const ProductPage = ({ data }) => {
  // render page using data...
}
export default ProductPage</code></pre>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 164px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 219px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 451px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 624px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 679px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 219px;"></div>

  </div>
</div>

NOTES:

- **ONE:** The way to render server-side is by exporting a `getServerSideProps` function
- So for our product details page, instead of retrieving the product data in the browser...
  - It retrieves it within Next's Node server
- **TWO:** The dynamic route `id` now comes from the `params` context
- **THREE:** Then, using the props returned from `getServerSideProps`...
  - **FOUR:** Next then will pass that data as props to our `ProductPage` component
  - **FIVE:** And the server will render and return the the same UI, but as HTML
  - It doesn't need a loading state since it doesn't render server-side until it has the data
- **SIX:** Similar to CSR, SSR calls the API and renders the HTML on **every request**
  - As a result...
  - The data once again can be constantly changing or even user-specific
  - And the server will return HTML with the most up-to-date UI, as we'd expect
- The server could even retrieve the related products data in `getServerSideProps`
  - And return the HTML for that as well

/////
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-start">
 <div class="content-overlay">

    <h3>Advantages</h3>
      <p>Dynamic content (user-specific)</p>
      <p>SEO-friendly</p>
      <p>Fast render times</p>

    <h3 style="margin-top: 5rem">Disadvantages</h3>
      <p>Slow for response times</p>

    <h3 style="margin-top: 5rem">Good candidates</h3>
      <p>Dynamic product listings & pages</p>
      <p>Search results pages</p>
      <p>Checkout pages</p>
  </div>
</div>

NOTES:

- Similar to client-side rendering, SSR is also great for **dynamic content**
  - Because its data is retrieved on the server for **every request**
- And because the full UI is in the HTML response...
  - It's very **SEO-friendly** - crawlers have everything they need
  - **In-browser render times** are also fast because of all the HTML is there
- But it comes as the cost of **slow response times**
  - While the server is likely fast at rendering HTML
  - It's got to wait on the API response
  - So the user doesn't see _anything_ until the full response is complete

- So if this PDP had a lot of changing content
  - Like price or size availability changes, then SSR could be a good fit
  - But if the data was mostly static, it'd be overkill & a sub-optimal render experience
- In general SSR is good for pages that either...
  - 1/ Have data that could change with every render
  - 2/ Or have user-specific content
  - So think search results, checkout flows, etc

=====
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Static-site generation (SSG)</h1>
  </div>
</div>

NOTES:

- Now let's talk about **static-site generation**
- SSG became super popular around 2019 thanks to Gatsby
  - And Next later joined the party, electing to make all pages static by default

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <p>Page HTML is pre-rendered at <u>build time</u></p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getStaticPaths = async () => {
  const apiUrl = 'api.acme.com/products/'
  const res = await fetch(apiUrl)
  const allProducts = await res.json();
  const paths = allProducts.map((product) => ({
    params: { id: product.id }
  }))

  return { paths, fallback: false }
}</code></pre>

    <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-false" target="_blank"><code>fallback</code></a> property<p>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 219px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 275px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 298px; top: 451px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 679px;"></div>
  </div>
</div>

NOTES:

- With SSG, HTML pages are **pre-rendered at build** time...
  - when running `next build` before the server even starts
  - And that same HTML will be reused for **every request**
- For a dynamic route like our PDP (`src/pages/product/[id].tsx`)
  - **ONE:** The page file needs to export `getStaticPaths`
  - It's goal is to inform Next which static pages it should pre-render for the route
- **TWO:** So we call the **/products/** API route to get the list of **all** products
  - **THREE:** That then is massaged into an array of paths returned by `getStaticPaths`
  - So if our site has 100 products, then `getStaticPaths` will return 100 paths
  - FYI: The property within `params` (`id` here) needs to match the dynamic route `[id]`
- **FOUR:** The `fallback: false` property here means that any requested page that wasn't pre-rendered at build time...
  - will return a 404
  - So `acme-hoodie` would need to be included in the `paths`, otherwise 404
  - Only the paths returned by `getStaticPaths` will work

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <p>Page HTML is pre-rendered at <u>build time</u></p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getStaticPaths = async () => {
  const apiUrl = 'api.acme.com/products/'
  const res = await fetch(apiUrl)
  const allProducts = await res.json();
  const paths = allProducts.map((product) => ({
    params: { id: product.id }
  }))

  return { paths, fallback: true }
}</code></pre>

    <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-true" target="_blank"><code>fallback</code></a> property<p>

    <div class="code-highlight" style="height: 70px; top: 679px;"></div>
  </div>
</div>

NOTES:

- Alternatively, `getStaticPaths` can return `fallback: true` instead
  - This means that pages other than those pre-rendered can still be requested
  - When it's first requested, Next will show a fallback loading UI while it renders in the background
  - Then it uses that same HTML for every subsequent request
- We can use this fallback strategy to speed up the initial build
  - If instead of 100, we have 1000s of PDPs, building all of them would take forever
  - So we can build the most popular ones
  - And leave the long tail to be built on-demand

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <p>Page HTML is pre-rendered at <u>build time</u></p>

    <pre class="large"><code class="lang-typescript">export const getStaticProps = async ({ params }) => {
  const apiUrl = \`api.acme.com/products/${params.id}/`
  const res = await fetch(apiUrl)
  const data = await res.json();

  return { props: { data } }
}

const ProductPage = ({ data }) => {
  // render page using data...
}
export default ProductPage</code></pre>

    <div class="code-highlight fragment current-visible" style="height: 70px; top: 164px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 219px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 451px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 624px;"></div>
    <div class="code-highlight fragment current-visible" style="height: 70px; top: 679px;"></div>

  </div>
</div>

NOTES:

- Now when Next is pre-rendering at build time...
  - **ONE:** it takes the ids we passed in `getStaticPaths`...
  - and passes it to `getStaticProps` for every page
- **TWO:** This is now where `ProductPage` makes the API call to retrieve the data
  - It's still happening in Node, but just at build time, not in the server
  - **THREE:** But just like with `getServerSideProps`, the `data` that _is_ returned...
  - **FOUR:** Becomes the props passed to `ProductPage`
- **FIVE:** Lastly, the rendered page HTML is stored on the filesystem
  - And is the **same HTML** for every request

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
 <div class="content-overlay">

    <h3>Advantages</h3>
      <p>SEO-friendly</p>
      <p>Highly cacheable</p>

    <h3 style="margin-top: 5rem">Disadvantages</h3>
      <p>Slow build times</p>
      <p>Dynamic content (user-specific)</p>

    <h3 style="margin-top: 5rem">Good candidates</h3>
      <p>Marketing pages</p>
      <p>Blog posts</p>
      <p>Static product listings & pages</p>
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
  - but then we may miss out on SSGs cacheability goodness
- It takes planning and forethought to get the right mix of static & dynamic

- So if I wanted to use SSG for our PDP...
  - We can render the all the UI at build time (image, title, sizes, etc)
  - Then in the browser we can retrieve & apply any size availability changes
  - Enable/disable the checkout button
  - Load in any user info in the header
  - And retrieve the related products
- So for the dynamic stuff...
  - we pre-render static content w/ default content or loading states
  - And sync w/ up-to-date data in the browser
- But in general, SSG is best & simplest for logged out pages...
  - Where the page is typically the same for everyone
  - Things like marketing landing pages, blog posts, etc
  - Or even product listings or our product details page if they rarely changed

=====
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Incremental static regeneration (ISR)</h1>
  </div>
</div>

NOTES:

- So we've talked about CSR, SSR & just now SSG
  - Lemme confuse you by adding one more acronym 😆
- As I mentioned, the trouble with SSG is that it's built once
- We like that it's super fast because it's cacheable...
  - But the rendered HTML never changes until we trigger another build
- Here's where **incremental static regeneration** aims to improve SSG...
  - by bringing the server to the party 🎉

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <p>Page HTML is <u>regenerated</u> on the server after cache timeout</p>

    <pre class="large"><code class="lang-typescript">export const getStaticProps = async ({ params }) => {
  const apiUrl = \`api.acme.com/products/${params.id}/`
  const res = await fetch(apiUrl)
  const data = await res.json();

  return {
    props: { data },
    revalidate: 300, // 5 minutes (in secs)
  }
}</code></pre>

    <div class="code-highlight" style="height: 70px; top: 565px;"></div>
  </div>
</div>

NOTES:

- So the page will still be pre-rendered at build time
- Let's look at `getStaticProps` again
- It's the same except we include this `revalidate` property
  - It tells Next how long to keep around the cached version of the page
  - After cache time is up, it'll **"regenerate"** the page the next time it's requested (hence the name)
- So the page is still static, but not "permanently static"
  - It can change w/o a triggered rebuild

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <p>Page HTML is <u>regenerated</u> on the server after cache timeout</p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getStaticPaths = async () => {
  const apiUrl = 'api.acme.com/products/'
  const res = await fetch(apiUrl)
  const allProducts = await res.json();
  const paths = allProducts.map((product) => ({
    params: { id: product.id }
  }))

  return { paths, fallback: 'blocking' }
}</code></pre>

    <p><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-blocking" target="_blank"><code>fallback</code></a> property<p>

    <div class="code-highlight" style="height: 70px; top: 679px;"></div>
  </div>
</div>

NOTES:

- We can combine `revalidate` with the 3rd option for `fallback:`...
  - `'blocking'` to provide a different user experience
- If you remember, `false` meant that requested pages that were not pre-rendered are a 404
  - And `true` meant that non-pre-rendered pages can be requested...
  - but the user will see a fallback loading UI while Next pre-renders in the background
- With `'blocking'`, it won't show the fallback UI
- Instead Next waits to update the UI until the new page has been pre-rendered by the server
  - So it kinda sorta feels like SSR
  - But we still get the cacheability of SSG
  - It's a hybrid
  - Vercel calls it "dynamic at the speed of static"

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:flex-end">
 <div class="content-overlay">

    <h3>Advantages</h3>
      <p>SEO-friendly</p>
      <p>Fast initial load times</p>
      <p>Allows for frequent data updates</p>

    <h3 style="margin-top: 5rem">Disadvantages</h3>
      <p>Slow build times</p>
      <p>Dynamic, user-specific content</p>

    <h3 style="margin-top: 5rem">Good candidates</h3>
      <p>Headless CMS pages</p>
      <p>Periodically-updating product listings & pages</p>
  </div>
</div>

NOTES:

- So ISR has all the same advantages and disadvantages as SSG
  - The huge difference is that the HTML can actually **update w/o requiring a rebuild**
- Maybe for the PDP we want the size availability to always be up-to-date...
  - so we still make that API call in the browser for every page request
- But if we're ok with the price or the related products to be stale for a bit...
  - We could pre-render those without having to call the API in the browser
  - Then once the cache expired we'd get the a **new pre-rendered page** w/ updated data
  - This provides a faster UX
- If the data or imagery changed, those would get updated too
- Like static-site generation, ISR works best for pages that are the same for everyone...
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

    <ul>
      <li><strong>Login / onboarding / blog</strong> 👉🏾 SSG</li>
      <li><strong>Product details / marketing</strong> 👉🏾 ISR</li>
      <li><strong>Search results / shopping cart / order history</strong> 👉🏾 SSR</li>
      <li><strong>3rd-party checkout, tracking / deferred UI</strong> 👉🏾 CSR</li>
    </ul>
  </div>
</div>

NOTES:

- Next.js isn't _just_ a client-side renderer like CRA
- It's not _just_ a static-site generator like Gatsby
- It's not even _just_ a server-side renderer like... OG Next
- It's all of them!
  - And the beauty is that any given page can use a different render mode
- I went through the 4 most popular modes
  - But we can configure pages to be various combinations too
  - The combinations are endless!
- Honestly, we probably could build every page with any of these render modes...
  - But some lend themselves better to certain types of pages
- So for our one e-commerce site...
  - Maybe the **login, onboarding pages & blog pages** use SSG
  - ISR would be good for **product detail pages & landing pages** because they're static, but could change outside of the build cycle
  - **Search results pages, shopping cart, order history**,  and other user-tailored pages are likely good candidates for SSR
  - And finally CSR for **3rd-party checkout, the shipment tracking page**, and any secondary UI that can be loaded after the main page renders

=====
<!-- .slide: data-background="url(../../img/ts-react/curved-library-susan-yin-2JIvboGLeho-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Resources</h2>

    <ul>
      <li><a href="https://www.benmvp.com/blog/50-shades-react-rendering-nextjs/?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023" target="_blank"><em>50 shades of React rendering with Next.js</em></li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/server-side-rendering" target="_blank">Server-side rendering with Next.js</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/static-site-generation" target="_blank">Static-site generation</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/incremental-static-regeneration" target="_blank">Incremental static regeneration</li>
      <li><a href="https://nextjs.org/docs/pages/building-your-application/rendering/incremental-static-regeneration#on-demand-revalidation" target="_blank">On-demand Incremental static regeneration</li>
      <li><a href="https://nextjs.org/docs/getting-started/react-essentials#server-components" target="_blank">Client & server components</li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-server-side-props" target="_blank"><code>getServerSideProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths" target="_blank"><code>getStaticPaths</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-props" target="_blank"><code>getStaticProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/use-router" target="_blank"><code>useRouter</code></li>
    </ul>
  </div>
</div>

NOTES:

- So I know I just hit you with a bunch of information
- Get these slides you can click through to all of these resources
- The first is actually a blog I wrote about this topic a few years ago now
- The rest are guides and docs for the official Next.js site
  - "On-demand incremental static rengeration" is like ISR, but with a sort of webhook
- You may want to check out the "client & server components" one
  - Next 13 opens up even more flexibility and performance in how pages are rendered

=====
<!-- .slide: data-background="url(../../img/perfect-lib/kelly-sikkema-fvpgfw3IF1w-thanks-unsplash.jpg) no-repeat center" data-background-size="cover"  -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 30%" class="content-overlay closing">

  <h1 class="closing">Ben Ilegbodu</h1>

  <br />

  <p><a href="https://twitter.com/benmvp" target="_blank">@benmvp</a> | <a href="https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023" target="_blank">benmvp.com</a></p>
  <p><a href="mailto:ben@benmvp.com">ben@benmvp.com</a></p>
  <p><a href="https://github.com/benmvp" target="_blank">github/benmvp</a></p>

  </div>
</div>

NOTES:

- So as I wrap up...
  - I encourage you to give Next.js a try
- Or if you already have...
  - Evaluate whether the pages you are using the best rendering strategy
- I'm here for the remainder of the conference...
  - So you can ask me questions on Twitter (@benmvp) or find me afterwards
- Thanks!
