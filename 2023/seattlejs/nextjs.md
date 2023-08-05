<!-- markdownlint-disable MD034 -->

<!-- .slide: data-state="title-page" data-background="url(../../img/webdev/jason-leung-479251-unsplash.jpg) no-repeat center" data-background-size="cover" -->

<div style="display: flex; align-items:center; justify-content: flex-end">
 <div style="width: 45%;" class="content-overlay">

  <h1>50 shades of React rendering with Next.js</h1>

  <br />

  <h2>Ben Ilegbodu</h2>

  <br />

  <p>[@benmvp](https://twitter.com/benmvp) | [benmvp.com](https://www.benmvp.com/?utm_source=benmvp&utm_medium=slides&utm_campaign=seattlejs-2023) | [@halfstackconf](https://twitter.com/halfstackconf/)</p>

  <br />

  <p>August 8, 2023</p>

  </div>
</div>

NOTES:
**RESTART THE TIMER!!!!**

/////

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

/////

# History of Next.js

/////

/////

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
<!-- .slide: data-background="url(../../img/nextjs/sample-product-page.png) no-repeat top right 10%" data-background-size="contain" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    https://acme.store/product/acme-hoodie
  </div>
</div>

=====
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Client-side rendering (CSR)</h1>
  </div>
</div>

NOTES:

/////
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <p>Page HTML is rendered in the <u>browser</u></p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const ProductPage = () => {
  const [data, setData] = useState(undefined);
  const { query } = useRouter()

  useEffect(() => {
    fetch(\`api.acme.com/products/${query.id}/\`)
      .then(res => res.json())
      .then(data => setData(data))
  }, [])

  return <p>{data ? \`The data ${data}\` : 'Loading...'}</p>
}</code></pre>
  </div>
</div>

NOTES:

- Client-side rendering is how single-page apps (SPAs) started out
  - It's the most common
  - Create React App is like this still
- Browser downloads a minimal HTML page
  - And the JS needed for the page
- The JavaScript is used to update the DOM & render the page
  - Typically after requesting data in the browser

/////
<!-- .slide: data-background="url(../../img/nextjs/laptop-carlos-muza-hpjSkU2UYSU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 45%;">
        <h3>Advantages</h3>
        <ul>
          <li>Dynamic content (user-specific)</li>
        </ul>
        <h3 style="margin-top: 2rem">Disadvantages</h3>
        <ul>
          <li>Slow load times</li>
          <li>Poor SEO</li>
        </ul>
      </div>
      <div style="flex:0 0 45%;">
        <h3>Good candidates</h3>
        <ul>
          <li>Interactive dashboards</li>
          <li>3rd-party widgets</li>
        </ul>
      </div>
    </div>
  </div>
</div>

NOTES:

- What this means for our product page is...

- In general routing with CSR has been a pain
  - Updating the URL, deep linking, etc.
  - Had to use `react-router` or similar
  - And code-splitting was challenging too
- Smooths that out
  - It will...
- CSR can be used on any page, but...
- It's necessary for browser-only UIs (i.e. integrating w/ Stripe)

=====
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: start">
  <div class="content-overlay">
    <h1>Server-side rendering (SSR)</h1>
  </div>
</div>

NOTES:

- Also know as "SSR" or "Dynamic rendering"

/////
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <p>Page HTML is generated on the server for <u>every request</u></p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getServerSideProps = async ({ params }) => {
  const apiUrl = \`api.acme.com/products/${params.id}/`
  const res = await fetch(apiUrl)
  const data = await res.json();

  return { props: { data } }
}

export const ProductPage = ({ data }) => {
  // render page using data...
}</code></pre>
  </div>
</div>

/////
<!-- .slide: data-background="url(../../img/nextjs/servers-ismail-enes-ayhan-lVZjvw-u9V8-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 45%;">
        <h3>Advantages</h3>
        <ul>
          <li>Dynamic content (user-specific)</li>
          <li>SEO-friendly</li>
        </ul>
        <h3 style="margin-top: 2rem">Disadvantages</h3>
        <ul>
          <li>Slow for dynamic content</li>
        </ul>
      </div>
      <div style="flex:0 0 45%;">
        <h3>Good candidates</h3>
        <ul>
          <li>Dynamic product pages</li>
          <li>Dynamic product listings</li>
          <li>Search results pages</li>
          <li>Checkout pages</li>
        </ul>
      </div>
    </div>
  </div>
</div>

NOTES:

- What this means for our product page is...
- Good for pages that either...
  - Have data that could change with every render
  - Have user generated content

=====
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-end">
  <div class="content-overlay">
    <h1>Static site generation (SSG)</h1>
  </div>
</div>

NOTES:

- Static-site generation became really popular thanks to Gatsby

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
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

    <p>The <a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-false" target="_blank"><code>fallback</code></a> property<p>
  </div>
</div>

NOTES:

- The HTML is built when running `next build`
  - It will be reused for **every request**
  - And can be cached in a CDN
- This is actually the default for Next
- `id` returned in `paths` matches `[id]`
- `fallback: false` means

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
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

- Alternatively, we can use `fallback: true`
  - This means...

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <p>Page HTML is pre-rendered at <u>build time</u></p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getStaticProps = async ({ params }) => {
  const apiUrl = \`api.acme.com/products/${params.id}/`
  const res = await fetch(apiUrl)
  const data = await res.json();

  return { props: { data } }
}

export const ProductPage = ({ data }) => {
  // render page using data...
}</code></pre>
  </div>
</div>

NOTES:

- The HTML is built when running `next build`
  - It will be reused for **every request**
  - And can be cached in a CDN
- This is actually the default for Next

/////
<!-- .slide: data-background="url(../../img/nextjs/pages-olga-tutunaru-JMATuFkXeHU-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 45%;">
        <h3>Advantages</h3>
        <ul>
          <li>SEO-friendly</li>
          <li>Highly cacheable</li>
        </ul>
        <h3 style="margin-top: 2rem">Disadvantages</h3>
        <ul>
          <li>Slow build times</li>
          <li>Dynamic, user-specific content</li>
        </ul>
      </div>
      <div style="flex:0 0 45%;">
        <h3>Good candidates</h3>
        <ul>
          <li>Marketing pages</li>
          <li>Static product pages</li>
          <li>Static product listings</li>
          <li>Blog posts</li>
          <li>Help & docs</li>
        </ul>
      </div>
    </div>
  </div>
</div>

NOTES:

- Best for logged out pages, pages that are the same for everyone
- What this means for our product page is...
- Because it is pre-rendered at build time
  - It's built only once
  - Great for cacheability, but not so great for dynamic content
- Can add dynamism by pre-rendering the page with placeholders
  - Fill in those placeholders with dynamic content
  - Recommended products could load client-side

=====
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: flex-start">
  <div class="content-overlay">
    <h1>Incremental static regeneration (ISR)</h1>
  </div>
</div>

NOTES:

- The trouble with SSG is it's build once
  - The rendered HTML never changes until the next build

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <p>Page HTML is <u>regenerated</u> on the server after cache timeout</p>

    <pre class="large"><code class="lang-typescript">// src/pages/product/[id].tsx
export const getStaticProps = async ({ params }) => {
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

- The page will still be pre-rendered at build time
- But...

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
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

  return { paths, fallback: blocking }
}</code></pre>

    <p>The <a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths#fallback-blocking" target="_blank"><code>fallback</code></a> property<p>
  </div>
</div>

NOTES:

- Can combine with `fallback: blocking` property for a different experience
  - In this case...

/////
<!-- .slide: data-background="url(../../img/nextjs/salamander-michaela-klikova-izRfVtrRX30-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex;justify-content:center">
 <div class="content-overlay" style="width: 100%;">

    <div style="display:flex;align-items:center;justify-content:space-between">
      <div style="flex:0 0 45%;">
        <h3>Advantages</h3>
        <ul>
          <li>SEO-friendly</li>
          <li>Fast initial load times</li>
          <li>Allows for frequent data updates</li>
        </ul>
        <h3 style="margin-top: 2rem">Disadvantages</h3>
        <ul>
          <li>Dynamic, user-specific content</li>
        </ul>
      </div>
      <div style="flex:0 0 45%;">
        <h3>Good candidates</h3>
        <ul>
          <li>CMS-driven pages</li>
          <li>Periodically-updating product pages</li>
          <li>Periodically-updating product listings</li>
        </ul>
      </div>
    </div>
  </div>
</div>

NOTES:

- Best for pages that are the same for everyone but need to update regularly
- Can still render dynamic content client-side

=====
<!-- .slide: data-background="url(../../img/nextjs/mockups-hal-gatewood-weRQAu9TA-A-unsplash.jpg) no-repeat top" data-background-size="cover" -->

<div style="display:flex; justify-content: center">
  <div class="content-overlay">
    <h2>Best render mode per page</h2>

    <ul>
      <li>A - SSR</li>
      <li>B - CSR</li>
      <li>C - SSG</li>
      <li>D - ISR</li>
    </ul>
  </div>
</div>

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
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-server-side-props" target="_blank"><code>getServerSideProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-paths" target="_blank"><code>getStaticPaths</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/get-static-props" target="_blank"><code>getStaticProps</code></li>
      <li><a href="https://nextjs.org/docs/pages/api-reference/functions/use-router" target="_blank"><code>useRouter</code></li>
    </ul>
  </div>
</div>

NOTES:

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
