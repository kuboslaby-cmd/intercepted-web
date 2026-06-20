# Intercepted website

Pre-launch marketing site for Intercepted (intercepted.app). Currently a single static
coming-soon page with waitlist capture. No build step.

## Structure

- `index.html` - the coming-soon page (self-contained: styles + script inline)
- `assets/` - app icon, favicon, Apple touch icon, OG image

## Local preview

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000   # then visit http://localhost:8000
```

## Waitlist

The form posts to a Supabase `waitlist` table. Set `SUPABASE_URL` and
`SUPABASE_ANON_KEY` near the bottom of `index.html`. Enable Row Level Security on the
table with an insert-only policy for the `anon` role. Until those are set, the form
shows a local success state so the page can ship as-is.

## Deploy (Cloudflare Pages, connected to this GitHub repo)

1. Push this repo to GitHub (see below).
2. Cloudflare dashboard > Workers & Pages > Create > Pages > Connect to Git.
3. Pick this repo. Build settings:
   - Framework preset: **None**
   - Build command: *(leave empty)*
   - Build output directory: **/**
4. Deploy. Then add the custom domain `intercepted.app` (one click, since the domain
   is already on Cloudflare).

Every push to `main` redeploys automatically.
