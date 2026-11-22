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

### Brand (round 3, Nov 22 2026, branch `feature/round-3-soul`)

- **Buyer**: a busy, posh millennial mother in Berlin or Märkisch-Oderland. She wants it beautiful and done for her. Brief for round 3: soul from restraint, honest product tags and Paulina's own voice (Cucinelli/Muji register). Photo shoot list: `docs/round-2-brief.md`.
- **Colour**: one pale-sage ground `#dce5dc` everywhere (Tural's pick), ink `#1c2826`, Paulina's curtain green `#2d514c` for the two big fields (hand-over list, enquiry), strawberry red `#ab2a40` for actions only. No cream or warm white, no boxed grey panels.
- **Type**: EB Garamond 400 (`fonts/EBGaramond-*.woff2`) for headings, the letter and prices; Jost 400/500 for text. Self-hosted only, no Google Fonts link (GDPR).
- **One shape: the arch.** Every photo sits in an arch window, the two green fields have a curtain-dome top, buttons, toggles, chore rows and form fields are pills or round. No scallops, seal or stickers.
- **Offer**: three packages, always called "Angebot": Der Tisch (ab 140 €), Die Feier (ab 270 €), Ihr seid Gäste (ab 350 €), each for 8 children. Each is a product tag: Enthält / Ich mache / Für / Passt, wenn. No package is preselected; its button selects it (red ring on the photo) and jumps to the WhatsApp form.
- **Copy is specific**: name the real dishes (Gemüse mit Dip, Pizza-Muffins, Bananenwaffeln, Apfelkuchen, Beeren auf Sahne). Every snack and dessert is a healthy choice. Never invent facts.
- **Live thing**: "Was ihr abgebt", a chore list with package toggles. The enquiry-form cake lights one candle per year.
- **Mark**: `images/mark.svg`, two strawberries: big Laura and small Laia leaning on her. Never show ".ai" in the brand.
- **Photos**: `images/v4/*.webp`, Paulina's own photos re-cropped to 4:5 and graded cooler and calmer. Each package shows its own outcome: the labelled banana waffles, the themed cake, Paulina serving the guests. Never use licensed characters, stock, or AI food or people. Several sources are soft video stills; the styled shoot will replace them.

### Sections in `index.html`

| Section | Purpose |
|---|---|
| `.hero` | "Kommt einfach als Gäste." The real dishes, from 140 €, 8 to 30 children, region. Whole-table photo in an arch |
| `#angebote` | Three package cards, then "Was ihr abgebt" (the chore list) |
| `#essen` | "Gesund bis zum Nachtisch." Snacks, sweets, cake, labels and allergies, named specifically |
| `#paulina` | "Ein Brief von Paulina": her letter (Paulina to confirm wording), signature, Laura & Laia, facts |
| `.how` | Three steps: one message is enough |
| `#fragen` | Six questions |
| `#anfrage` | Live WhatsApp message builder (+491783129500), with the package pre-selected |
| `impressum.html`, `datenschutz.html` | Legal pages. Filled Nov 22 2026: Kantstr. 17, 15366 Neuenhagen bei Berlin; Kleinunternehmerin (§ 19 UStG). |

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
