# Foundation Repair Advocate — Go live (≈10 minutes)

Domain **foundationrepairadvocate.com** is on Cloudflare. Code is on GitHub: https://github.com/tappel003-byte/foundationrepairadvocate

## Step 1 — Cloudflare Workers (current setup)

This site deploys as a **Worker** (not Pages). Repo: https://github.com/tappel003-byte/foundationrepairadvocate

### Build settings (Cloudflare dashboard → Worker → Settings → Build)

| Setting | Value |
|---------|--------|
| Production branch | `main` |
| Build command | `npm run build` |
| Deploy command | `npx wrangler deploy` |

**Important:** Use `wrangler deploy` — **not** `wrangler versions upload`. The latter requires a manual **Promote** step. `wrangler deploy` goes live immediately and attaches custom domains from `wrangler.toml`.

### Custom domain

`wrangler.toml` includes `foundationrepairadvocate.com` and `www`. After a successful deploy, check **Workers → foundationrepairadvocate → Domains**.

If the dashboard **Add Domain** button does nothing, the domain should still attach on deploy. Fallback: **DNS** → **Records** → **Add record** → Type **Worker** → Name `@` → Worker **foundationrepairadvocate** (repeat for `www`).

Temporary URL while DNS connects: https://foundationrepairadvocate.tappel003.workers.dev/

## Step 1 (legacy) — Cloudflare Pages

<details>
<summary>Pages setup (not used for this project)</summary>

1. Open [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create**
2. Choose **Pages** → **Connect to Git**
3. Select repo **`foundationrepairadvocate`**
4. Build settings:

   | Setting | Value |
   |---------|--------|
   | Production branch | `main` |
   | Framework preset | Astro (or None) |
   | Build command | `npm run build` |
   | Build output directory | `dist` |
   | Environment variable | `NODE_VERSION` = `22` |

5. Click **Save and Deploy**.

</details>

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

**Quo (~$19/mo after trial)** — optional if you want CNAM/business caller ID later.

**Google Voice (free)** — current number **(928) 298-5756**. Forwards to your cell. See below for caller ID limits.

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
