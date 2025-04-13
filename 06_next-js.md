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


---


npm install mongodb

npm i use-local-storage-state

