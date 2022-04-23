---
title: Pages
date: April 23, 2022 7:50 PM
---
<!--StartFragment-->

> This document is for Next.js versions 9.3 and up. If you're using older versions of Next.js, refer to our [previous documentation](https://nextjs.org/docs/tag/v9.2.2/basic-features/pages).

In Next.js, a **page** is a [React Component](https://reactjs.org/docs/components-and-props.html) exported from a `.js`, `.jsx`, `.ts`, or `.tsx` file in the `pages` directory. Each page is associated with a route based on its file name.

**Example**: If you create `pages/about.js` that exports a React component like below, it will be accessible at `/about`.

```jsx

```

### [Pages with Dynamic Routes](https://nextjs.org/docs/basic-features/pages#pages-with-dynamic-routes)

Next.js supports pages with dynamic routes. For example, if you create a file called `pages/posts/[id].js`, then it will be accessible at `posts/1`, `posts/2`, etc.

> To learn more about dynamic routing, check the [Dynamic Routing documentation](https://nextjs.org/docs/routing/dynamic-routes).

## [Pre-rendering](https://nextjs.org/docs/basic-features/pages#pre-rendering)

By default, Next.js **pre-renders** every page. This means that Next.js generates HTML for each page in advance, instead of having it all done by client-side JavaScript. Pre-rendering can result in better performance and SEO.

Each generated HTML is associated with minimal JavaScript code necessary for that page. When a page is loaded by the browser, its JavaScript code runs and makes the page fully interactive. (This process is called *hydration*.)

### [Two forms of Pre-rendering](https://nextjs.org/docs/basic-features/pages#two-forms-of-pre-rendering)

Next.js has two forms of pre-rendering: **Static Generation** and **Server-side Rendering**. The difference is in **when** it generates the HTML for a page.

* **[Static Generation (Recommended)](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)**: The HTML is generated at **build time** and will be reused on each request.
* **[Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)**: The HTML is generated on **each request**.

Importantly, Next.js lets you **choose** which pre-rendering form you'd like to use for each page. You can create a "hybrid" Next.js app by using Static Generation for most pages and using Server-side Rendering for others.

We **recommend** using **Static Generation** over Server-side Rendering for performance reasons. Statically generated pages can be cached by CDN with no extra configuration to boost performance. However, in some cases, Server-side Rendering might be the only option.

You can also use **Client-side Rendering** along with Static Generation or Server-side Rendering. That means some parts of a page can be rendered entirely by client side JavaScript. To learn more, take a look at the [Data Fetching](https://nextjs.org/docs/basic-features/data-fetching/client-side) documentation.

## [Static Generation (Recommended)](https://nextjs.org/docs/basic-features/pages#static-generation-recommended)

**Examples**

* [WordPress Example](https://github.com/vercel/next.js/tree/canary/examples/cms-wordpress) ([Demo](https://next-blog-wordpress.vercel.app/))
* [Blog Starter using markdown files](https://github.com/vercel/next.js/tree/canary/examples/blog-starter) ([Demo](https://next-blog-starter.vercel.app/))
* [DatoCMS Example](https://github.com/vercel/next.js/tree/canary/examples/cms-datocms) ([Demo](https://next-blog-datocms.vercel.app/))
* [TakeShape Example](https://github.com/vercel/next.js/tree/canary/examples/cms-takeshape) ([Demo](https://next-blog-takeshape.vercel.app/))
* [Sanity Example](https://github.com/vercel/next.js/tree/canary/examples/cms-sanity) ([Demo](https://next-blog-sanity.vercel.app/))
* [Prismic Example](https://github.com/vercel/next.js/tree/canary/examples/cms-prismic) ([Demo](https://next-blog-prismic.vercel.app/))
* [Contentful Example](https://github.com/vercel/next.js/tree/canary/examples/cms-contentful) ([Demo](https://next-blog-contentful.vercel.app/))
* [Strapi Example](https://github.com/vercel/next.js/tree/canary/examples/cms-strapi) ([Demo](https://next-blog-strapi.vercel.app/))
* [Prepr Example](https://github.com/vercel/next.js/tree/canary/examples/cms-prepr) ([Demo](https://next-blog-prepr.vercel.app/))
* [Agility CMS Example](https://github.com/vercel/next.js/tree/canary/examples/cms-agilitycms) ([Demo](https://next-blog-agilitycms.vercel.app/))
* [Cosmic Example](https://github.com/vercel/next.js/tree/canary/examples/cms-cosmic) ([Demo](https://next-blog-cosmic.vercel.app/))
* [ButterCMS Example](https://github.com/vercel/next.js/tree/canary/examples/cms-buttercms) ([Demo](https://next-blog-buttercms.vercel.app/))
* [Storyblok Example](https://github.com/vercel/next.js/tree/canary/examples/cms-storyblok) ([Demo](https://next-blog-storyblok.vercel.app/))
* [GraphCMS Example](https://github.com/vercel/next.js/tree/canary/examples/cms-graphcms) ([Demo](https://next-blog-graphcms.vercel.app/))
* [Kontent Example](https://github.com/vercel/next.js/tree/canary/examples/cms-kontent) ([Demo](https://next-blog-kontent.vercel.app/))
* [Builder.io Example](https://github.com/vercel/next.js/tree/canary/examples/cms-builder-io) ([Demo](https://cms-builder-io.vercel.app/))
* [Static Tweet (Demo)](https://static-tweet.vercel.app/)

If a page uses **Static Generation**, the page HTML is generated at **build time**. That means in production, the page HTML is generated when you run `next build` . This HTML will then be reused on each request. It can be cached by a CDN.

In Next.js, you can statically generate pages **with or without data**. Let's take a look at each case.

### [Static Generation without data](https://nextjs.org/docs/basic-features/pages#static-generation-without-data)

By default, Next.js pre-renders pages using Static Generation without fetching data. Here's an example:

```jsx

```

Note that this page does not need to fetch any external data to be pre-rendered. In cases like this, Next.js generates a single HTML file per page during build time.

### [Static Generation with data](https://nextjs.org/docs/basic-features/pages#static-generation-with-data)

Some pages require fetching external data for pre-rendering. There are two scenarios, and one or both might apply. In each case, you can use these functions that Next.js provides:

1. Your page **content** depends on external data: Use `getStaticProps`.
2. Your page **paths** depend on external data: Use `getStaticPaths` (usually in addition to `getStaticProps`).

#### [Scenario 1: Your page **content** depends on external data](https://nextjs.org/docs/basic-features/pages#scenario-1-your-page-content-depends-on-external-data)

**Example**: Your blog page might need to fetch the list of blog posts from a CMS (content management system).

```jsx

```

To fetch this data on pre-render, Next.js allows you to `export` an `async` function called `getStaticProps` from the same file. This function gets called at build time and lets you pass fetched data to the page's `props` on pre-render.

```jsx

```

To learn more about how `getStaticProps` works, check out the [Data Fetching documentation](https://nextjs.org/docs/basic-features/data-fetching/get-static-props).

#### [Scenario 2: Your page paths depend on external data](https://nextjs.org/docs/basic-features/pages#scenario-2-your-page-paths-depend-on-external-data)

Next.js allows you to create pages with **dynamic routes**. For example, you can create a file called `pages/posts/[id].js` to show a single blog post based on `id`. This will allow you to show a blog post with `id: 1` when you access `posts/1`.

> To learn more about dynamic routing, check the [Dynamic Routing documentation](https://nextjs.org/docs/routing/dynamic-routes).

However, which `id` you want to pre-render at build time might depend on external data.

**Example**: suppose that you've only added one blog post (with `id: 1`) to the database. In this case, you'd only want to pre-render `posts/1` at build time.

Later, you might add the second post with `id: 2`. Then you'd want to pre-render `posts/2` as well.

So your page **paths** that are pre-rendered depend on external data**.** To handle this, Next.js lets you `export` an `async` function called `getStaticPaths` from a dynamic page (`pages/posts/[id].js` in this case). This function gets called at build time and lets you specify which paths you want to pre-render.

```jsx

```

Also in `pages/posts/[id].js`, you need to export `getStaticProps` so that you can fetch the data about the post with this `id` and use it to pre-render the page:

```jsx

```

To learn more about how `getStaticPaths` works, check out the [Data Fetching documentation](https://nextjs.org/docs/basic-features/data-fetching/get-static-paths).

### [When should I use Static Generation?](https://nextjs.org/docs/basic-features/pages#when-should-i-use-static-generation)

We recommend using **Static Generation** (with and without data) whenever possible because your page can be built once and served by CDN, which makes it much faster than having a server render the page on every request.

You can use Static Generation for many types of pages, including:

* Marketing pages
* Blog posts and portfolios
* E-commerce product listings
* Help and documentation

You should ask yourself: "Can I pre-render this page **ahead** of a user's request?" If the answer is yes, then you should choose Static Generation.

On the other hand, Static Generation is **not** a good idea if you cannot pre-render a page ahead of a user's request. Maybe your page shows frequently updated data, and the page content changes on every request.

In cases like this, you can do one of the following:

* Use Static Generation with **Client-side Rendering:** You can skip pre-rendering some parts of a page and then use client-side JavaScript to populate them. To learn more about this approach, check out the [Data Fetching documentation](https://nextjs.org/docs/basic-features/data-fetching/client-side).
* Use **Server-Side Rendering:** Next.js pre-renders a page on each request. It will be slower because the page cannot be cached by a CDN, but the pre-rendered page will always be up-to-date. We'll talk about this approach below.

## [Server-side Rendering](https://nextjs.org/docs/basic-features/pages#server-side-rendering)

> Also referred to as "SSR" or "Dynamic Rendering".

If a page uses **Server-side Rendering**, the page HTML is generated on **each request**.

To use Server-side Rendering for a page, you need to `export` an `async` function called `getServerSideProps`. This function will be called by the server on every request.

For example, suppose that your page needs to pre-render frequently updated data (fetched from an external API). You can write `getServerSideProps` which fetches this data and passes it to `Page` like below:

```jsx

```

As you can see, `getServerSideProps` is similar to `getStaticProps`, but the difference is that `getServerSideProps` is run on every request instead of on build time.

To learn more about how `getServerSideProps` works, check out our [Data Fetching documentation](https://nextjs.org/docs/basic-features/data-fetching/get-server-side-props)

## [Summary](https://nextjs.org/docs/basic-features/pages#summary)

We've discussed two forms of pre-rendering for Next.js.

* **Static Generation (Recommended):** The HTML is generated at **build time** and will be reused on each request. To make a page use Static Generation, either export the page component, or export `getStaticProps` (and `getStaticPaths` if necessary). It's great for pages that can be pre-rendered ahead of a user's request. You can also use it with Client-side Rendering to bring in additional data.
* **Server-side Rendering:** The HTML is generated on **each request**. To make a page use Server-side Rendering, export `getServerSideProps`. Because Server-side Rendering results in slower performance than Static Generation, use this only if absolutely necessary.

<!--EndFragment-->