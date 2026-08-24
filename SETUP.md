# Foundation Repair Advocate — Go live (≈10 minutes)

Domain **foundationrepairadvocate.com** is on Cloudflare. Code is on GitHub: https://github.com/tappel003-byte/foundationrepairadvocate

## Step 1 — Cloudflare Pages (do this first)

1. Open [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create**
2. Choose **Pages** → **Connect to Git** → authorize GitHub if needed
3. Select repo **`foundationrepairadvocate`**
4. Build settings:

   | Setting | Value |
   |---------|--------|
   | Production branch | `main` |
   | Framework preset | Astro (or None) |
   | Build command | `npm run build` |
   | Build output directory | `dist` |
   | Environment variable | `NODE_VERSION` = `22` |

5. Click **Save and Deploy**. First build takes ~1–2 minutes.
6. You’ll get a `*.pages.dev` URL — open it and confirm the site looks right.

## Step 2 — Custom domain

1. In the Pages project → **Custom domains** → **Set up a custom domain**
2. Add `foundationrepairadvocate.com`
3. Add `www.foundationrepairadvocate.com` (optional)
4. Cloudflare adds DNS automatically since the domain is already in your account.

Wait a few minutes, then visit https://foundationrepairadvocate.com

## Step 3 — Search Console (when live)

1. [Google Search Console](https://search.google.com/search-console) → add property
2. Verify via DNS TXT record in Cloudflare (easiest)
3. Submit sitemap: `https://foundationrepairadvocate.com/sitemap-index.xml`

## Phone number — Quo vs Google Voice

The number on the site lives in **one file**: `src/lib/site.ts` (`PHONE` and `PHONE_TEL`). Change it there, commit, push — Pages redeploys automatically.

**Quo (~$19/mo after trial)**  
Pros: business voicemail, texting, call recording, dedicated 928 line.  
Cons: costs money before you have revenue.

**Google Voice (free)**  
Pros: free, forwards to your cell, fine for testing the business.  
Cons: you may not get a 928 number; less “business phone” polish; no Quo-style CRM.

You don’t need to settle this before launch. Pick whichever number you’ll actually answer for the next 30 days, put it in `site.ts`, and go live. Swapping later is a 2-minute edit.

During Quo’s 7-day trial: use it or cancel before billing. No need to keep paying $20/mo while you’re still testing whether calls come in.

## Local preview

```bash
npm install
npm run dev          # http://localhost:4321
npm run build        # production build → dist/
```

## What this site is not

- No links to MFRC, TLS Foundations, or Sandia GEO
- No pier sales CTAs
- Footer disclaimer covers contractor / HI / PE scope
