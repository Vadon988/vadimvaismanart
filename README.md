# Vadim Vaisman Art — Landing Page

> Hyperrealistic portrait drawings in colored pencil & charcoal · Haifa, Israel

**Live site → [vadon988.github.io/vadimvaismanart](https://vadon988.github.io/vadimvaismanart/)**

---

## About

Personal landing page for **Vadim Vaisman**, a hyperrealistic portrait artist based in Haifa, Israel.  
The page showcases original artwork, explains the commission process, and captures inquiries from potential clients.

---

## Features

| Feature | Details |
|---|---|
| **Gallery** | Masonry grid with filter tabs (color / sketch) |
| **Lightbox** | Full-screen artwork preview on click |
| **Contact form** | Sends email via [Web3Forms](https://web3forms.com) + syncs lead to Airtable CRM |
| **Scroll animations** | IntersectionObserver — each section reveals on scroll |
| **SEO** | Structured data (JSON-LD), Open Graph, canonical, geo meta tags |
| **Security** | CSP, X-Content-Type-Options, Referrer-Policy, Permissions-Policy headers |
| **RTL** | Full right-to-left Hebrew layout |
| **Mobile** | Fully responsive, no JS frameworks |

---

## Tech Stack

- Pure **HTML5 / CSS3 / Vanilla JS** — zero dependencies, no build step
- Fonts: [Google Fonts](https://fonts.google.com) — Heebo + Playfair Display
- Form backend: [Web3Forms](https://web3forms.com) (email) + [Airtable](https://airtable.com) (CRM)
- Hosting: **GitHub Pages** (gh-pages branch)

---

## File Structure

```
vadimvaismanart/
├── index.html            # Main landing page (auto-generated — do not edit manually)
├── landing_template.html # Source template edited in Studio Manager
├── og-image.JPG          # Open Graph / social share image
├── logo.png              # Site logo
├── artwork/              # Gallery images (auto-populated from Studio Manager)
│   ├── hero.jpg          # Hero section background
│   └── *.jpg             # Painting thumbnails
└── .nojekyll             # Disables Jekyll so filenames starting with _ are served
```

> **Note:** `index.html` and the `artwork/` folder are regenerated automatically each time  
> you press **"פרסם דף נחיתה"** in the Studio Manager dashboard.  
> Edit `landing_template.html` for layout/content changes.

---

## How Deployment Works

This repo is managed by a local **Flask Studio Manager** app.  
When you click **"פרסם דף נחיתה"** (Publish Landing Page) in the dashboard:

1. The app scans the paintings gallery and copies images to `artwork/`
2. It injects API keys (Web3Forms, Airtable) into the HTML template
3. It strips any secret tokens before pushing to this public repo
4. It uploads all files to this `gh-pages` branch via the **GitHub Tree API**  
   (N blob POSTs → 1 tree → 1 commit → 1 ref update = single atomic push)
5. GitHub Pages serves the updated site within ~60 seconds

---

## Custom Domain (Optional)

To use a custom domain (e.g. `vadimvaisman.com`):

1. Buy a domain from [Cloudflare Registrar](https://www.cloudflare.com/products/registrar/) or any registrar
2. Add a `CNAME` file to this repo containing your domain name
3. In your DNS: add a `CNAME` record pointing to `vadon988.github.io`
4. In the repo **Settings → Pages**, set the custom domain and enable "Enforce HTTPS"

---

## Contact

**Vadim Vaisman** — Portrait artist, Haifa  
WhatsApp / inquiries via the contact form on the live site.

---

*Deployed and managed via [Studio Manager](https://github.com/vadon988/vadimvaismanart) — a custom Flask-based CRM & publishing tool.*
