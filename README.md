# ForelCards — Supabase version

This version keeps the existing design/admin panel but uses the Supabase `public.cards` table instead of browser-only IndexedDB when a publishable key is configured.

## One final setup step

Open `supabase-config.js` and replace:

`PASTE_YOUR_PUBLISHABLE_KEY_HERE`

with the **Publishable key** from Supabase → Settings → API Keys.

The project URL is already filled in.

Do not use a `service_role` or secret key in the browser.

## Expected table

The existing Supabase table is expected to be named `public.cards` and to contain the fields used by the site:
- `id`
- `character`
- `rank`
- `platform`
- `description`
- `link`
- `image`
- `date`

The site reads, adds, updates, and deletes cards through Supabase. Existing cards in this browser's IndexedDB are automatically uploaded to Supabase if the Supabase table is empty.

## Run

This is a static site. It can be served by any static hosting provider. For local testing, serve the folder over HTTP rather than opening `index.html` directly.

Note: the existing admin password is still client-side and therefore is not a secure authentication mechanism. For a production admin panel, use Supabase Auth + RLS rather than relying on a password embedded in JavaScript.
