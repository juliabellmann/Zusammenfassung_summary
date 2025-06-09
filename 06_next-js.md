# Markdown Notizen zu Next.js

Notizen zur Webseite https://nextjs.org/learn/pages-router .

# Pages Router

React: Vorrendern von Seiten für Performance und SEO 


## Starten im Terminal:

`npx create-next-app@latest`

- What is your project named? `<app-name>`
- Would you like to use TypeScript? >NO / Yes
- Would you like to use ESLint? No / >YES
- Would you like to use Tailwind CSS? No / >YES
- Would you like your code inside a `src/` directory? >NO / Yes
- Would you like to use App Router? (recommended) No (NF) / Yes (aktueller)
- Would you like to use Turbopack for `next dev`?  >NO / Yes
- Would you like to customize the import alias (`@/*` by default)? No / >YES
- What import alias would you like configured? @/*


## Entwicklungsserver starten

WICHTIG: Darauf achten, dass man direkt im Projektordner ist.

`npm run dev`

jetzt kann man über: http://localhost:3000 im Browser die Webseite sehen


## Routing

https://nextjs.org/docs/pages/building-your-application/routing

### Index Routes

Der Router leitet Dateien mit dem Namen "index" automatisch zur Wurzel des Verzeichnisses weiter.

    pages/index.js → /
    pages/blog/index.js → /blog

### Nested Routes

Der Router unterstützt verschachtelte Dateien. wenn verschachtelte Ordnerstruktur erstellt werden, werden die Dateien automatisch weiterhin auf dieselbe Weise geroutet.

    pages/blog/first-post.js → /blog/first-post
    pages/dashboard/settings/username.js → /dashboard/settings/username


### Dynamic Routes

Next.js unterstützt auch dynamische Routen. Wenn bspw. eine Datei `pages/posts/[id].js` erstellt wird, dann ist sie unter `posts/1`, `posts/2`, etc. aufrufbar.


## Layout

```js 
import Layout from '../components/layout'
 
export default function MyApp({ Component, pageProps }) {
  return (
    <Layout>
      <Component {...pageProps} />
    </Layout>
  )
}
```

## Link Component

In Next.js, you can use the Link Component next/link to link between pages in your application. <Link> allows you to do client-side navigation and accepts props that give you better control over the navigation behavior.

```js 
import Link from 'next/link';
```

Note: Before Next.js 12.2, it was required that the Link component wrapped an <a> tag, but this is not required in versions 12.2 and above
.

This shows that the browser does not load the full page and client-side navigation is working.
If you’ve used `<a href="…">` instead of `<Link href="…">` and did this, the background color will be cleared on link clicks because the browser does a full refresh.

You can learn more about the Link component in the API reference for next/link and routing in general in the routing documentation.
https://nextjs.org/docs/pages/api-reference/components/link

### Code splitting and prefetching

Only loading the code for the page you request also means that pages become isolated. If a certain page throws an error, the rest of the application would still work.

This ensures that the homepage loads quickly even if you have hundreds of pages.

Furthermore, in a production build of Next.js, whenever Link components appear in the browser’s viewport, Next.js automatically prefetches the code for the linked page in the background. By the time you click the link, the code for the destination page will already be loaded in the background, and the page transition will be near-instant!


Create a top-level directory called components.

## Adding CSS

Important: To use CSS Modules, the CSS file name must end with .module.css.

https://nextjs.org/docs/app/getting-started/css


## Assets

In der Webentwicklung sind Assets alle Komponenten und Ressourcen, die zusammen eine Website bilden. Dazu gehören statische Dateien wie Bilder, Fonts, CSS-Dateien und Javascripte. Assets sind entscheidend für die Funktionalität, Leistung und das Nutzererlebnis einer Website. 

Static Assets, wie Bilder -> top-lvl Ordner: public
Verweise wie bei pages

der "public" Ordner ist auch für `robots.txt`, google seiten verification und alle anderen static assets nützlich.
 https://nextjs.org/docs/app/building-your-application/optimizing/static-assets



 ## Images

 in HTML wurde <img >-Tag verwendet - Next.js: <Image>

<Image> 
- lazy load: default
- autom. Opimierung der Bilder

https://nextjs.org/docs/pages/building-your-application/routing/custom-document



## CSS Modules

ZUsätzlich zu CSS modulen kann die Next.js Application auf unterschieldiche Weise gestyled werden:
- Sass - was .css und .scss Dateien erlaubt
- PostCSS libaries wie Tailwind CSS
- CSS-in-JS libaries wie styled-jsx, styled-components und emotion

https://github.com/vercel/next.js/tree/canary/examples/with-emotion


## Global Styles

The default export of _app.js is a top-level React component that wraps all the pages in your application. You can use this component to keep state when navigating between pages, or to add global styles as we're doing here. Learn more about _app.js file.

https://nextjs.org/docs/pages/building-your-application/routing/custom-app

Important: You need to restart the development server when you add pages/_app.js. 

### Adding global styles

In Next.js, you can add global CSS files by importing them from pages/_app.js. You cannot import global CSS anywhere else.

The reason that global CSS can't be imported outside of pages/_app.js is that global CSS affects all elements on the page.

If you were to navigate from the homepage to the /posts/first-post page, global styles from the homepage would affect /posts/first-post unintentionally.

You can place the global CSS file anywhere and use any name. So let’s do the following:

- Create a top-level styles directory and a global.css file.
- Add the following CSS inside styles/global.css. This code resets some styles and changes the color of the a tag:

      html,
      body {
      padding: 0;
      margin: 0;
      font-family:
        -apple-system,
        BlinkMacSystemFont,
        Segoe UI,
        Roboto,
        Oxygen,
        Ubuntu,
        Cantarell,
        Fira Sans,
        Droid Sans,
        Helvetica Neue,
        sans-serif;
      line-height: 1.6;
      font-size: 18px;
      }

      * {
      box-sizing: border-box;
      }

      a {
      color: #0070f3;
      text-decoration: none;
      }

      a:hover {
      text-decoration: underline;
      }

      img {
      max-width: 100%;
      display: block;
      }

      Finally, import the CSS file inside the pages/_app.js file you've created earlier on:

      // `pages/_app.js`
      import '../styles/global.css';

      export default function App({ Component, pageProps }) {
      return <Component {...pageProps} />;
      }

Now, if you access http://localhost:3000/posts/first-post
, you’ll see that the styles are applied. Any styles imported in _app.js will be applied globally, to all pages of the application.





## SASS

Before you can use Next.js' built-in Sass support, be sure to install sass

    npm install -D sass



























---
Core Web Vitals - Nutzerfreundlichkeit der Webseite
https://web.dev/articles/vitals?hl=de#core-web-vitals

CLS - Cumulative Layout Shift - unerwartete Layoutveränderungen
https://web.dev/articles/cls?hl=de

npm install mongodb

npm i use-local-storage-state

