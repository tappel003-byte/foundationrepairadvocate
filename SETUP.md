# Foundation Repair Advocate — Go-live checklist

Domain **foundationrepairadvocate.com** is on Cloudflare. Phone **(928) 251-2608** is on Quo (OpenPhone).

## 1. GitHub

Repo: https://github.com/tappel003-byte/foundationrepairadvocate

Push from local:

```bash
git push -u origin main
```

## 2. Cloudflare Pages (recommended)

1. [Cloudflare Dashboard](https://dash.cloudflare.com) → **Workers & Pages** → **Create**
2. **Pages** → **Connect to Git** → select `foundationrepairadvocate`
3. Build settings:
   - Framework preset: **Astro** (or None)
   - Build command: `npm run build`
   - Build output: `dist`
   - Node version: **22**
4. Deploy. First build should produce 6 pages + sitemap.

## 3. Custom domain

Because the domain is already in the same Cloudflare account:

1. Pages project → **Custom domains** → **Set up a domain**
2. Enter `foundationrepairadvocate.com` and `www.foundationrepairadvocate.com`
3. Cloudflare creates DNS records automatically.

If using Workers instead of Pages, add a route or custom domain on the Worker after `npm run deploy`.

## 4. SSL & redirects

- Force HTTPS (Cloudflare default)
- Optional: redirect `www` → apex in **Rules** → **Redirect rules**

## 5. Google Search Console

1. [search.google.com/search-console](https://search.google.com/search-console)
2. Add property: `https://foundationrepairadvocate.com`
3. Verify via DNS TXT (Cloudflare) or HTML tag
4. Submit sitemap: `https://foundationrepairadvocate.com/sitemap-index.xml`
5. Request indexing on `/` and `/contact/` first

## 6. Quo / phone

Confirm Quo forwards to your mobile and voicemail greeting mentions Foundation Repair Advocate (not TLS, not MFRC).

## 7. What this site is not

- No links to MFRC, TLS Foundations, or Sandia GEO
- No pier sales CTAs
- Footer disclaimer covers contractor / HI / PE scope

## Local preview

```bash
cd fra
npm install
npm run dev
```

Production preview after build:

```bash
npm run build && npm run preview
```
