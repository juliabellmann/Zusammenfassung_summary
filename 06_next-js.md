# Markdown Notizen zu Next.js
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







npm install mongodb

npm i use-local-storage-state

