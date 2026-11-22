# AllesGute.AI — Agent Handoff

You are working on **allesgute.ai**, a landing page for a Berlin-based kids' birthday catering business run by Paulina Salahov. The site is live at https://allesgute.ai.

---

## Repo structure

```
index.html          ← entire site: HTML + inline CSS + inline JS (single file)
images/             ← 8 photos used in the hero and gallery sections
LAUNCH_GUIDE.md     ← original deployment notes
AGENTS.md           ← this file
```

No build step. No framework. No dependencies. Plain HTML file deployed to Netlify.

---

## Deployment

- **Hosting**: Netlify (project: `merry-dusk-63754c`)
- **Live domain**: https://allesgute.ai (custom domain, SSL auto-provisioned by Let's Encrypt)
- **Deploy method**: currently manual ZIP upload — will be migrated to GitHub-connected auto-deploy
- **Once GitHub is connected**: every push to `main` auto-deploys to production. Use PRs + Netlify branch previews for review before merging.

---

## Site overview

**Business**: AllesGute — birthday catering for children's parties in Berlin  
**Owner**: Paulina Salahov (German/Polish background, two daughters: Laura 5, Laia 2)  
**Languages**: Trilingual — German (primary), English, Polish (language switcher in nav)  
**WhatsApp booking**: +491783129500  

### Key sections in `index.html`

| Section | Purpose |
|---|---|
| `#hero` | Headline + CTA + hero cake image |
| `#packages` | 3 packages: Starter (199€), Standard (299€), Premium (449€) |
| `#ablauf` | 4-step "how it works" process |
| `#ueber-uns` | Paulina's personal story + portrait |
| `#faq` | 8 FAQ accordion items |
| `#anfragen` | Contact/booking form (Formspree integration, see below) |

### Design system (inline in `<style>` tag)

```css
--color-primary: #C8375A      /* berry red — brand accent */
--color-bg: #FAF8F5           /* warm off-white */
--font-heading: 'Playfair Display', serif
--font-body: 'Inter', sans-serif
```

Strawberry cursor system: Laura (big 🍓 follows mouse) + Laia (small 🍓 trails with delay). Do not remove — it's intentional branding.

---

## Pending tasks (priority order)

### 1. Formspree — REQUIRED before site is usable for bookings

The contact form at `#anfragen` has a placeholder form ID. Find this in `index.html`:

```html
<form action="https://formspree.io/f/YOUR_FORMSPREE_ID" method="POST">
```

Replace `YOUR_FORMSPREE_ID` with Paulina's actual Formspree form ID once she provides it.  
Paulina signs up at https://formspree.io — free tier handles up to 50 submissions/month.

### 2. Payment links — booking buttons need real URLs

The "Paket buchen" buttons in the packages section currently link to `#anfragen` (the contact form). Once Paulina creates Stripe or PayPal payment links for each package, update:

- Starter (199€): replace `href="#anfragen"` with the payment link
- Standard (299€): same
- Premium (449€): same

### 3. Impressum + Datenschutz — LEGALLY REQUIRED in Germany

Currently both footer links point to `href="#"`. German law (Telemediengesetz) requires a real Impressum and Datenschutzerklärung on every commercial website.

**Impressum must include**: full name, address, phone, email of the responsible person.  
**Datenschutz**: GDPR-compliant privacy policy covering contact form data, cookies, analytics.

Options:
- Create `/impressum.html` and `/datenschutz.html` as separate pages
- Or add `id="impressum"` / `id="datenschutz"` sections at the bottom of index.html
- Update the footer `<a href="#">` links accordingly

### 4. Performance: image optimization

Images in `images/` are unoptimized originals (total ~87MB folder). Before production traffic scales:
- Convert to WebP format
- Resize to max 1200px width for hero images, 800px for gallery
- Add `loading="lazy"` to all `<img>` tags below the fold (most already have it; verify)

### 5. Analytics (optional)

Add Google Analytics 4 or Plausible (privacy-first, recommended for EU) tracking snippet in `<head>`.

---

## What NOT to change

- The trilingual content system (DE/EN/PL switcher in nav). Translations are stored in `data-de`, `data-en`, `data-pl` attributes on each element.
- The strawberry cursor JS (bottom of `<body>`) — intentional branding
- The two-strawberry system variable names: `cursorLaura` and `cursorLaia`
- WhatsApp number: `+491783129500`
- The existing photo filenames — they are referenced directly in `index.html`

---

## Code style

- All CSS is in a single `<style>` block in `<head>`
- All JS is in a single `<script>` block at the end of `<body>`
- No external CSS frameworks (custom CSS only)
- Mobile-first responsive design via CSS Grid and Flexbox
- Language switching: JS reads `data-lang` attribute on `<html>` tag and sets each element's `textContent` from its `data-{lang}` attribute

---

## How to test locally

```bash
# Just open the file — no server needed
open index.html

# Or serve with Python for accurate relative paths
python3 -m http.server 8080
# then visit http://localhost:8080
```

---

## PR conventions

- Branch naming: `feature/task-name` or `fix/what-was-broken`
- One concern per PR
- For anything touching copy: include before/after in the PR description
- Netlify will auto-generate a preview URL per PR once GitHub is connected — use it to visually verify before merging to `main`
