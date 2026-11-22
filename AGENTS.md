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

**Region**: Berlin and Märkisch-Oderland (Paulina lives in Neuenhagen). Not Havelland.

### Brand (Nov 2026 redesign, branch `feature/brand-redesign`)

- **Idea**: Paulina labels every dish on her tables with a black chalk card ("Banana Waffeln", "Apfel Kuchen"). Those chalk labels are the page's device: dark `.label` cards in the `Chalk` hand face (Caveat subset), soft rounded photos, Paulina's handwritten greeting, and a live cake that lights one candle per year in the enquiry form.
- **Mark**: `images/mark.svg`, two flat strawberries: big Laura, small Laia leaning on her. Wordmark "AllesGute" in EB Garamond. Never show ".ai" in the brand; the domain is only an address.
- **Colour, taken from Paulina's own photos**: linen ground `#f7f1ea`, curtain green `#2f5552` (prices, footer, the mark's leaves), strawberry red `#b02a42` / `#a3263c` (actions, booking section, the berries), waffle honey `#efc483` (prices on green, candle flames), berry blush `#f4dcd4` (how it works), chalk `#231f1c` (her labels). Photos share one white-balance grade so they sit in the same light.
- **Type**: EB Garamond (self-hosted woff2, latin + latin-ext for Polish) for everything; Chalk only on labels and the message preview. No Google Fonts link (GDPR).
- **Photos**: `images/v2/*.webp` are crops of Paulina's own photos with one shared grade. Never use licensed characters (Paw Patrol, Frozen) in frame, never stock or AI-generated food or people. Originals stay in `images/`.
- **Prices**: quoted per party. "Geburtstagstisch ab 150 €" (= 8 children x 19 €, the old base rate) and "Die ganze Feier nach Absprache". Paulina must confirm these numbers.
- **Removed on purpose**: the emoji strawberry cursor (read as cheap on a premium page; the daughters now live in the mark and the "Laura & Laia" tile).

### Sections in `index.html`

| Section | Purpose |
|---|---|
| `.hero` | "Heute seid ihr auch Gäste." + slow crossfade of three real party photos |
| `.intro` | "Drei Stunden in der Küche." Paulina's reason for doing this |
| `#tisch` | Band of four food photos with chalk labels |
| `#preise` | Prices set like a menu, two groups |
| `#paulina` | Who cooks, the mark's story, facts |
| `.moments` | Five moments from first message to singing along (drag row) |
| `#fragen` | Six questions |
| `#anfrage` | Live WhatsApp message builder with preview (+491783129500) |
| `impressum.html`, `datenschutz.html` | Legal pages. **Fill the [placeholders] (address, tax status) before merging to main.** |

### Checks

Design checks used the tasteskill inspector: `node ~/.claude/skills/design-taste-frontend/scripts/inspect.mjs index.html` (0 FAIL is the floor). Working files land in `.taste-skill/` (gitignored).

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
