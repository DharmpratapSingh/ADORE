# adore — ylee's website

`hours i live` — a single-page portfolio in the form of a room.

## structure

- `index.html` — the entire site (HTML + CSS + JS inline)
- `art/` — illustrations referenced by the page

Static site, no build step. Open `index.html` locally or deploy as-is.

## deploy (Vercel)

1. Push this repo to GitHub.
2. In Vercel, **New Project → Import** the repo.
3. Framework Preset: **Other** · Build Command: *(none)* · Output Directory: `.`
4. Deploy.

The `.vercelignore` keeps the design source dump (zips, PDFs, screenshots) out of the deployment.
