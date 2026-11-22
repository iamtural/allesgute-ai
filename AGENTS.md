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

### Brand (round 2, Nov 22 2026, branch `feature/brand-redesign`)

- **Buyer**: a busy, posh millennial mother in Berlin or Märkisch-Oderland. She wants it beautiful and done for her. Brief, references and the 10-shot photo list: `docs/round-2-brief.md`.
- **Register**: "Spielzimmer", a Nordic playroom (Konges Sløjd and Liewood): oat ground `#f4eee4`, sage `#d8dfcd`, blush `#f1d8cf`, butter `#f3e4b5`, ink `#35332d`, strawberry red `#ab2a40` for actions only.
- **Type**: Fraunces 500 (`fonts/Fraunces-500.woff`) for headings and Jost 400/500 (`fonts/Jost-*.woff2`) for text. Caveat (`Hand`) is used only for "Hallo, ich bin Paulina." and her signature. All fonts are self-hosted, with no Google Fonts link (GDPR). EB Garamond stays for the legal pages only.
- **Devices**: arch-shaped photo windows, scalloped section edges (tablecloth or bunting), a round "Alles Gute zum Geburtstag" seal around the strawberry mark, and price stickers on the package cards.
- **Offer**: three named packages: No.1 Der Tisch (ab 140 €), No.2 Die Feier (ab 270 €), No.3 Ihr seid Gäste (ab 350 €). Prices set by Tural and Paulina, Nov 22 2026. Each card has a "Passt, wenn…" line, and its button selects the package and jumps to the WhatsApp form.
- **Live thing**: "Was ihr abgebt", a chore list that ticks off as she picks a package. The enquiry-form cake still lights one candle per year.
- **Mark**: `images/mark.svg`, two strawberries: big Laura and small Laia leaning on her. Never show ".ai" in the brand.
- **Photos**: `images/v3/*.webp` are brightened crops of Paulina's own photos. Each package shows its own outcome: the laid table, the themed cake, and Paulina serving the guests. Never use licensed characters, stock, or AI food or people. A styled shoot (`docs/round-2-brief.md`) will replace these.

### Sections in `index.html`

| Section | Purpose |
|---|---|
| `.hero` | "Kommt einfach als Gäste." What it is, from 140 €, 8 to 30 children, region. Whole-table photo in an arch, plus the seal |
| `#angebote` | Three package cards, then "Was ihr abgebt" (the chore list) |
| `#essen` | "Obst zuerst." Healthy-but-beautiful hook, with three proof lines |
| `#paulina` | Who cooks: her story, signature, Laura & Laia, facts |
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
