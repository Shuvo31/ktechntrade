# KtechnTrade Website

> Build Digital. Grow Smarter.

## Repo Structure

```
/
├── index.html          ← Complete single-page website
├── render.yaml         ← Render static site config
├── README.md
└── assets/             ← Put all brand images here
    ├── ktechntrade-lockup-horizontal.png
    ├── ktechntrade-icon-cyan-1024.png
    ├── ktechntrade-icon-dark-1024.png
    ├── ktechntrade-mark-color-2048.png
    └── ktechntrade-mark-reversed-2048.png
```

## Local Preview

Just open `index.html` in any browser — no build step needed.

## Deploy to Render

1. Push this repo to GitHub.
2. Go to [render.com](https://render.com) → **New → Static Site**.
3. Connect your GitHub repo.
4. Settings:
   - **Build Command:** *(leave blank)*
   - **Publish Directory:** `.`
5. Click **Create Static Site** — Render auto-deploys on every push.

## Connect GoDaddy Domain

1. In Render: **Settings → Custom Domain** → add your domain (e.g. `ktechntrade.com`).
2. Copy the **CNAME value** Render gives you.
3. In GoDaddy DNS Manager:
   - Delete the existing `A` record for `@` (or `www`).
   - Add a **CNAME** record: `www` → `<your-render-cname>.onrender.com`.
   - For the apex domain (`@`), add an **A** record pointing to Render's IP (shown in their custom domain panel), or use a DNS flattening service.
4. Wait up to 48 hrs for DNS propagation (usually under 1 hour).

## Contact Form

The form currently shows a success animation client-side only.  
To make it actually send emails, replace the `setTimeout` in the submit handler with a `fetch` call to one of:

- **[Formspree](https://formspree.io)** — free tier, no backend needed  
- **[Web3Forms](https://web3forms.com)** — free, no backend  
- Your own FastAPI/Node.js backend endpoint

```js
// Example with Formspree:
form.addEventListener('submit', async e => {
  e.preventDefault();
  const res = await fetch('https://formspree.io/f/YOUR_ID', {
    method: 'POST',
    body: new FormData(form),
    headers: { Accept: 'application/json' }
  });
  if (res.ok) { /* show success */ }
});
```
