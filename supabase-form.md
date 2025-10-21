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


## Supabase - Query zum Table erstellen für das anlegen des Profils

-- Create profiles table and RLS policies for per-user profiles
BEGIN;

CREATE TABLE IF NOT EXISTS public.profiles (
  id uuid PRIMARY KEY REFERENCES auth.users(id) ON DELETE CASCADE,
  company_name text,
  company_street text,
  company_house_nr text,
  company_zip text,
  company_city text,
  company_contact_person text,
  created_at timestamptz DEFAULT now(),
  updated_at timestamptz DEFAULT now()
);

-- Trigger to update updated_at
CREATE OR REPLACE FUNCTION public.set_updated_at()
RETURNS trigger LANGUAGE plpgsql AS $$
BEGIN
  NEW.updated_at = now();
  RETURN NEW;
END;
$$;

DROP TRIGGER IF EXISTS set_updated_at_trigger ON public.profiles;
CREATE TRIGGER set_updated_at_trigger
BEFORE UPDATE ON public.profiles
FOR EACH ROW EXECUTE FUNCTION public.set_updated_at();

-- Enable RLS and policies
ALTER TABLE public.profiles ENABLE ROW LEVEL SECURITY;

-- Allow authenticated users to SELECT/UPDATE their own profile
CREATE POLICY "profiles_owner_select" ON public.profiles
  FOR SELECT TO authenticated
  USING (id = (SELECT auth.uid()));

CREATE POLICY "profiles_owner_insert" ON public.profiles
  FOR INSERT TO authenticated
  WITH CHECK (id = (SELECT auth.uid()));

CREATE POLICY "profiles_owner_update" ON public.profiles
  FOR UPDATE TO authenticated
  USING (id = (SELECT auth.uid()))
  WITH CHECK (id = (SELECT auth.uid()));

COMMIT;

## Create profiles RLS policies

-- Enable RLS (already enabled but safe to run)
ALTER TABLE public.profiles ENABLE ROW LEVEL SECURITY;

-- Revoke any broad privileges (defensive)
REVOKE ALL ON public.profiles FROM PUBLIC;

-- Create SELECT policy for owners
CREATE POLICY profiles_owner_select ON public.profiles
  FOR SELECT
  TO authenticated
  USING ((id = (SELECT auth.uid())));

-- Create INSERT policy for owners
CREATE POLICY profiles_owner_insert ON public.profiles
  FOR INSERT
  TO authenticated
  WITH CHECK ((id = (SELECT auth.uid())));

-- Create UPDATE policy for owners
CREATE POLICY profiles_owner_update ON public.profiles
  FOR UPDATE
  TO authenticated
  USING ((id = (SELECT auth.uid())))
  WITH CHECK ((id = (SELECT auth.uid())));

-- Optionally allow service_role to bypass (no policy needed for service_role)

-- Validate: simple select count as owner would succeed for rightful user (can't validate here)