# Foundation Repair Advocate

Independent foundation second opinions and Pro Level floor elevation surveys for Arizona homeowners.

Paid advocacy — not a pier company, not a free sales inspection. Built as a static Astro site for Cloudflare.

## Quick start

```bash
npm install
npm run dev      # http://localhost:4321
npm run build    # output → dist/
npm run preview
npm run deploy   # build + wrangler deploy (requires Cloudflare auth)
```

## Pages

- `/` — Home
- `/what-you-get/` — Services and scope
- `/why-us/` — Why independent vs sales visits
- `/how-it-works/` — Process
- `/service-area/` — Arizona coverage
- `/contact/` — Phone-first contact

Site constants (phone, nav) live in `src/lib/site.ts`.

## Cloudflare deploy

**Option A — Pages (recommended for Git auto-deploy)**

1. Push to GitHub (`tappel003-byte/foundationrepairadvocate`)
2. Cloudflare Dashboard → Workers & Pages → Create → Connect to Git
3. Build command: `npm run build`
4. Build output directory: `dist`
5. Environment variable: `NODE_VERSION` = `22`
6. Custom domain: `foundationrepairadvocate.com` (already on Cloudflare registrar)

**Option B — Workers static assets (wrangler)**

```bash
npm run deploy
```

Then attach custom domain in Cloudflare → Workers → foundationrepairadvocate → Settings → Domains.

See `SETUP.md` for DNS and Search Console steps.

## Brand note

Do not use "FRA" monogram in customer-facing assets — collides with Foundation Repair Association.
