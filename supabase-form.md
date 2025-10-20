# Supabase Form 

## neues Projekt aufsetzen

Das neue Projekt wird als neuer Unterodner in dem aktuell ausgewählten Ordner abgespeichert.

npx create-next-app@latest

    What is your project named? <app-name>
    Would you like to use TypeScript? >NO / Yes
    Would you like to use ESLint? No / >YES
    Would you like to use Tailwind CSS? No / >YES
    Would you like your code inside a src/ directory? >NO / Yes
    Would you like to use App Router? > No  / Yes
    Would you like to use Turbopack for next dev? >NO / Yes
    Would you like to customize the import alias (@/* by default)? > No / YES


## Styled components

npm install styled-components


## supabase neues projekt anlegen

-> supabase

-> Projekt anlegen

-> lib -> supabaseClient.js anlegen 

// lib/supabaseClient.js
import { createClient } from '@supabase/supabase-js'

const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL
const supabaseAnonKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY

export const supabase = createClient(supabaseUrl, supabaseAnonKey)


-> im Root des Projekt die Datei .2nv.local anlegen

NEXT_PUBLIC_SUPABASE_URL=https://your-project-id.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=your-anon-key

## Supabase installieren

npm install @supabase/supabase-js


## Supabase-Projekt erstellen

New Project

Project Settings -> API für .env.local

NEXT_PUBLIC_SUPABASE_URL=https://projecturl.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY= ...



## in next.config.mjs styledComponents ergänzen

/** @type {import('next').NextConfig} */
const nextConfig = {
  reactStrictMode: true,
  compiler: {
    styledComponents: true,
  },
};

export default nextConfig;


## SSH key erstellen um VSCode mit Git zu verknüpfen / schreiberechte o.ä. falls an neuem PC erstellt

### Anzeigen ob key vorhanden
ls -al ~/.ssh

### generieren eines neuen SSH keys
ssh-keygen -t ed25519 -C "your_email@example.com"

### key hinzufügen
ssh-add ~/.ssh/id_ed25519

### key zu github hinzufügen
cat ~/.ssh/id_ed25519.pub

1. Go to GitHub → Settings → SSH and GPG keys
2. Klicke New SSH Key
3. neuen Namen eingeben und Key einfügen
4. speichern
