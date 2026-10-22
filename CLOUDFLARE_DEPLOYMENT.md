# FSI (Foundation Structure Inspection) - Cloudflare Deployment Guide

## 1. Cloudflare Pages (Free Tier - Recommended & Optimal)
Since this Astro site is fully static (`output: "static"`):
- **Bandwidth & Requests:** 100% UNLIMITED and FREE on Cloudflare Pages.
- **SSL / CDN:** Automatic global edge network with instant SSL certificates.

### How to Deploy to Cloudflare Pages (2 Options):

#### Option A: Direct Git Push (Zero Maintenance)
1. Push `C:\Users\Asus\Documents\2000foundationBidar` to your GitHub / GitLab repository.
2. In Cloudflare Dashboard, go to **Workers & Pages** -> **Create application** -> **Pages** -> **Connect to Git**.
3. Set Build Settings:
   - **Framework Preset:** `Astro`
   - **Build Command:** `bunx --bun astro build` (or `bun run build`)
   - **Build Output Directory:** `dist`
4. Click **Save and Deploy**. Done!

#### Option B: Direct CLI Deployment via Wrangler
Run in the project directory:
```bash
bunx wrangler pages deploy dist --project-name fsi-engineering
```

---

## 2. Cloudflare Worker (Static Assets via Wrangler)
If you prefer running directly under **Cloudflare Workers** (Workers with Assets):
1. In `wrangler.toml` or via command:
```bash
bunx wrangler deploy --assets=dist
```
- The free plan of Workers allows **100,000 requests per day**, which is plenty for a landing page. (Cloudflare Pages is recommended because it has no daily request cap).

---

## 3. Email Dispatch Setup (FormSubmit)
Both forms (`BookingTerminal.astro` on Home and `contact-us.astro`) are configured to dispatch directly to:
**`mahmoudi.6486@gmail.com`**

### First-Time Activation Step (One-Time Only):
1. The very first time you submit the form on the live site, FormSubmit will send a single **Confirmation Email** to `mahmoudi.6486@gmail.com`.
2. Open that email in your Gmail inbox and click the **"Activate Form"** button.
3. From that moment on, every form submission will immediately arrive in your Gmail with:
   - Client Name
   - Client Phone Number (click-to-call)
   - Client Email Address
   - Property Address (Dallas-Fort Worth)
   - Selected Inspection Category
   - Property Notes / Deadline
   - Formatted in a clean table with spam protection and zero server maintenance.
