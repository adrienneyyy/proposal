# Propose Already

A single-page countdown site: time left until end of year, styled like a
retro CRT boot log. No build step — it's one `index.html` plus two image
assets.

## What's in here

```
propose-already/
├── index.html        ← the whole site (HTML + CSS + JS in one file)
├── og-image.png       ← 1200×630 preview image for iMessage/IG/Twitter/etc.
├── favicon.ico
├── favicon-16.png
├── favicon-32.png
├── vercel.json         ← deployment config
└── README.md
```

## Change the deadline

Open `index.html`, find this line near the bottom in the `<script>` tag:

```js
const target = new Date("2026-12-31T23:59:59");
```

Change the date to whatever you want. It's parsed in the visitor's local
timezone.

## Deploy to GitHub

1. Create a new repo on GitHub (e.g. `propose-already`), **do not**
   initialize it with a README (you already have one here).
2. From this folder, run:

   ```bash
   git init
   git add .
   git commit -m "propose already"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/propose-already.git
   git push -u origin main
   ```

## Deploy to Vercel

**Option A — Vercel dashboard (no terminal needed)**
1. Go to [vercel.com/new](https://vercel.com/new)
2. Import the GitHub repo you just pushed
3. Framework preset: choose **"Other"** (it's a static site, no build
   command needed)
4. Click **Deploy**

**Option B — Vercel CLI**
```bash
npm i -g vercel
vercel
```
Follow the prompts, accept the defaults (no build command, output
directory is the project root).

## Point proposealready.com at it

In your Vercel project settings → **Domains**, add `proposealready.com`
and follow Vercel's instructions to update your DNS records (usually an
`A` record to `76.76.21.21` or a `CNAME` to `cname.vercel-dns.com`,
depending on your registrar).

Once the domain is live, the Open Graph tags in `index.html` are already
pointed at `https://proposealready.com/`, so link previews on iMessage,
Instagram, and Twitter will pull `og-image.png` automatically.
