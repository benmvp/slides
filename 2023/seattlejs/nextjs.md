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
  </div>
</div>

NOTES:

- When React burst on the scene in 2015, it was a game changer for many reasons
- Other UI libraries of the day attached directly to the DOM
  - Think jQuery or Backbone
  - Everything operated on the DOM
- React on the other hand **separated the UI** from the rendering
- Because of this the generated UI could be rendered in multiple different ways...
  - Using different renders
- **React Native** works because React can be rendered in a mobile environment
- **Netflix** and other streaming providers can also use React...
  - Because they've built renders for TVs
- Here we have what was the most common render...
  - For the Web that renders the UI into a browser DOM element

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
  </div>
</div>

NOTES:

- **Next.js** took React's ability to **render** to a string in order to render a React app server-side
  - This was the "isomorphic React" revolution
  - The ability to render the same UI on the server as well as in the browser
- Next started way back in 2016, focusing mainly on server-side rendering
- The UI is rendered to a string on the server
  - And then **"hydrated"** in the browser attaching event handlers and such

/////
<!-- .slide: data-background="url(../../img/esnext/simon-rae-221560-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay" style="width: 65%;">
    <img src="../../img/nextjs/nextjs-logo-dark.svg" alt="Logo for Next.js" class="plain" />
  </div>
</div>

NOTES:

- Around Next 9 (2019), Next started emphasizing pre-rendering at build time
- So not only could we render server-side, but before the server even ran
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
  - Used to live in the Bay Area for 20 years
  - Moved back home

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

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <p>https://acme.store/product/acme-hoodie</p>

    <pre class="large"><code class="lang-typescript">
// src/pages/product/[id].tsx

</code></pre>
  </div>
</div>

NOTES:

- Let's take a look at this made up product details page (aka PDP)
  - It's got the title & main product images
  - The price
  - The sizes (which may or may not be out-of-stock)
  - The add-to-cart button (which or may not be enabled)
  - The carousel of related products at the bottom
  - And the related products
- I want us to keep all of this in mind
  - Because we'll be using it as our example for the code
- Oh and before we begin,
- Next.js uses what's called **path-based routing**
  - Meaning that if we want a page at `/product/acme-hoodie`
  - We'll put our page component at `src/product/`
- It also supports **dynamic path-based routing**
  - So if we want to support having multiple pages within `/product`...
  - we can use `[id]`
  - And `acme-hoodie` would be one of the ids
- Without further ado, let's dive in

=====
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Client-side rendering (CSR)</h1>
  </div>
</div>

NOTES:

- First let's start with CSR, client-side rendering

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
  </div>
</div>

NOTES:

- Within that component file (`/product/[id].tsx`)...
  - The default export is the page component
- Client-side rendering (aka CSR) is how single-page apps (SPAs) started out
  - It's probably the most common
  - Create React App is like this still
- For our product details page, Next will pre-render a minimal HTML file at build time
  - It'll have our loading state
- Then the Next.js JavaScript will **render the page in the browser**...
  - It grabs the `id` (from `[id]`) in puts in the `query` object returned by Next's built-in router
  - After the product API is called
- Because the API is called every time the page renders...
  - The data can be constantly changing or even user-specific
  - The size selector in-stock data can change
  - The product can go on sale
  - The header can show logged-in status
  - And everything will be immediately reflected with the next page request
- More than likely the related product carousel would be loaded as a separate render

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

- So CSR is great for dynamic content
  - And since the page is mostly blank initially the response is fast
- However, because everything is rendered in the browser...
  - Browser render times are slow especially since they wait on the API return
  - This is magnified on lower in devices
  - SEO is generally worse because there's no HTML markup for the search engine
  - Similarly there's no real markup to cache in the CDN
- So I probably wouldn't use CSR for this PDP
  - SEO is too important & the client needs to see _something_ quickly
- Instead CSR is great for UIs like highly-interactive, user-specific dashboards
  - Think Figma or task managers like Asana
- It's also good for pages that rely heavily on browser-based 3rd-party
  - Like embedding a Stripe checkout widget

=====
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: start">
  <div class="content-overlay">
    <h1>Server-side rendering (SSR)</h1>
  </div>
</div>

NOTES:

- Ok, let's move to what's likely the most familiar form of rendering
  - Server-side rendering
- Also know as "SSR" or "Dynamic rendering"

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
  </div>
</div>

NOTES:

- The way to render server-side is by also exporting a `getServerSideProps` function
- So for our product details page, instead of retrieving the product data in the browser
  - It retrieves it within Next's Node server
  - The dynamic route `id` now comes from the `params` context s
  - Next then will pass that data as props to our `ProductPage` component
  - And the server will render and return the the same UI as HTML
  - It doesn't need a loading state since it doesn't render server-side until it has the data
- Similar to CSR, SSR calls the API and renders the HTML on **every request**
  - As a result...
  - The data once again can be constantly changing or even user-specific
  - And the server will return HTML with the most up-to-date UI as we'd expect
- The server could even retrieve the related products data
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

- Similar to client-side rendering, SSR is also great for dynamic content
  - Because its data is retrieved on the server for every request
- And because the full UI is in the HTML response
  - It's very SEO-friendly - crawlers have everything they need
  - In-browser render times are also fast because of this
- But it comes as the cost of slow response times
  - While the server is fast at rendering HTML
  - It's got to wait on the API response
  - So the user doesn't see _anything_ until the response is complete
- So if this PDP had a lot of changing content
  - Like price or stock changes
  - SSR could be a good fit
  - But if the data was mostly static, it'd be overkill & a sub-optimal render experience
- In general SSR is good for pages that either...
  - Have data that could change with every render
  - Or have user-specific content
  - So think search results, checkout flows, etc

=====
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Static-site generation (SSG)</h1>
  </div>
</div>

NOTES:

- Now let's talk about static-site generation
- Static-site generation became super popular around 2019 thanks to Gatsby
  - And Next joined the party, electing to make pages static by default

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
  </div>
</div>

NOTES:

- With SSG, HTML pages are **pre-rendered at build** time (when running `next build`)
  - That same HTML will be reused for **every request**
- For a dynamic route like our PDP (`src/pages/product/[id].tsx`)
  - The page file needs to export `getStaticPaths`
  - It's goal is to inform which static pages it should pre-render for the route
- So it'll call the **products** API route to get the list of **all** products
  - That then is massaged into an array of paths returned by `getStaticPaths`
  - The property within `params` (`id` here) needs to match the dynamic route `[id]`
- The `fallback: false` property means that any requested page that wasn't pre-rendered at build time...
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
  </div>
</div>

NOTES:

- Alternatively, `getStaticPaths` can return `fallback: true` instead
  - This means that pages other than those pre-rendered can be requested
  - Next will then render that page when it's first requested while showing a fallback loading UI
  - Then it uses that HTML for every subsequent request
- We can use this strategy to speed up the build
  - If we have 100s of PDPs, building all of them would take forever
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
  </div>
</div>

NOTES:

- Now when Next is pre-rendering at build time...
  - it takes the ids we passed in `getStaticPaths` and passes it to `getStaticProps` for every render
- This is now where `ProductPage` makes the API call to retrieve the data
  - It's still happening in Node, but just at build time, not in the server
  - But just like with `getServerSideProps`, the `data` is returned which becomes props to `ProductPage`
- The render UI HTML is stored on the filesystem and returned for **every request**

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

- The appeal of static rendering is that it's super fast
  - The HTML is already ready when the user requests it
  - In fact it can be cacheable by CDNs because it's the same for everybody
  - But the flip side of the coin is that it results in slower build time...
  - because all of these pages have to built before the server even runs
- However like SSR it's also SEO-friendly because all of the HTML is there
- The idea with SSG is that there's a single page file for everyone...
  - So dynamic or user-specific data can be tricky
  - We can of course make API requests in the browser for the dynamic...
  - but then we may miss out on SSGs cacheability goodness
- It takes planning and forethought to get the right mix of static & dynamic
- So for our PDP...
  - We can render the all the UI at build time (image, title, sizes, etc)
  - Then in the browser we can mark the necessary sizes out of stock
  - Enable/disable the checkout button
  - Load in any user info in the header
  - And retrieve the related products
- So we pre-render static content (default or loading states)
  - And update in the browser
- In general, SSG is best for logged out pages...
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
- As I mentioned, the trouble with SSG is it's built once
  - We like that it's super fast because it's cacheable
  - But the rendered HTML never changes until the next build
- Here's where incremental static regeneration aims to improve SSG

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
  </div>
</div>

NOTES:

- So the page will still be pre-rendered at build time
- Let's look at `getStaticProps`
- It's the same except we include this `revalidate` property
  - It tells Next how long to keep around this cached version of the page
  - After cache time is up, it'll **regenerate** the page the next time it's requested (hence the name)
- So the page is still static, but not "permanent"
  - It can change w/o a rebuild

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
  </div>
</div>

NOTES:

- We can combine this with the 3rd option for `fallback`: `'blocking'` to provide a different experience
- If you remember, `false` meant that requested pages that were not pre-rendered are a 404
  - And `true` meant that non-pre-rendered pages can be requested...
  - but it'll show a fallback loading UI while it pre-renders
- With `'blocking'`, it won't show the fallback UI
  - But instead wait to update the UI until the new page has been pre-rendered by the server
  - So it kinda sorta feels like SSR
  - But we still get the cacheability of SSG
  - It's a hybrid

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
  - The huge difference is that the HTML can actually update w/o requiring a rebuild
- Maybe for the product details page we want the stock state to always be up-to-date...
  - so we still request that in the browser
  - So if we're ok with the price or the related products to be stale for our cache time...
  - We could pre-render those without having to update the API in the browser providing a better UX
  - We could even change the title & imagery regularly too
- Like static-site generation, ISR works best for pages that are the same for everyone...
  - but they have data that needs to update regularly
- Best for pages that are the same for everyone but need to update regularly
  - I'm thinking of headless CMS pages where UI changes can be hands-off by Engineering
  - Or semi-static product listings & pages
  - They need to be able to update, but they aren't changing on every request either

=====
<!-- .slide: data-background="url(../../img/nextjs/mockups-hal-gatewood-weRQAu9TA-A-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>One site, many render types</h2>

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
- It's not _just_ a server-side renderer like... OG Next
- It's all of them!
  - And the beauty is that any given page can use a different render mode
- I went through the 4 most popular modes
  - But we can configure pages to be various combinations too
- We could build every page with any of these render modes...
  - But some lend themselves better to certain types of pages
- So for our one e-commerce site...
  - Maybe the **login, onboarding pages & blog pages** use SSG
  - ISR would be good for **product detail pages & landing pages** because they're static, but could change outside of the build cycle
  - **Search results pages, shopping cart, order history**,  and other user-tailored pages are likely good candidates for SSR
  - And finally CSR for **3rd-party checkout, the shipment tracking page**, and any secondary UI that can be loaded after the main page

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
- So if you get the slides you can click through to all of these resources
- The first is actually a blog I wrote about this topic a few years ago now
- The rest are guides and docs for the official Next.js site
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
- Or if you have...
  - Evaluate whether the pages are using the best rendering strategy
- I'm here for the remainder of the conference...
  - So you can ask me questions on Twitter (@benmvp) or find me afterwards
- Thanks!
