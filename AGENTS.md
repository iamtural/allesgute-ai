# AllesGute.AI — Agent Handoff

You are working on **allesgute.ai**, a landing page for a Berlin-based kids' birthday catering business run by Paulina Zagorska Salahova. The site is live at https://allesgute.ai.

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
**Owner**: Paulina Zagorska Salahova (German/Polish background, two daughters: Laura 5, Laia 2)  
**Languages**: Trilingual — German (primary), English, Polish (language switcher in nav)  
**WhatsApp booking**: +491783129500  

**Region**: Berlin and Märkisch-Oderland (Paulina lives in Neuenhagen). Not Havelland.

### Brand (round 4, Nov 22 2026, branch `feature/round-4-clear`)

- **Name**: always **"Alles Gute"**, with a space (Tural, Nov 22). The domain and email stay `allesgute.ai`. Never show ".ai" in the brand.
- **Buyer**: a busy, posh millennial mother in Berlin or Märkisch-Oderland. Everything must be unmistakably clear: what it is, the three offers, how to order, where to send.
- **Colour**:
  - Pale-sage ground `#dce5dc`.
  - Strawberry red `#ab2a40` for actions and for one field, Paulina's letter.
  - Curtain green `#2d514c` for two fields: the hand-over list and the enquiry.
  - Each offer card has its own tone: blush `#f3dbd3`, butter `#f2e5b9`, sky `#d6e1ef`.
  - No cream or warm white.
- **Type**: EB Garamond 400 for headings, the letter and prices; Jost 400/500 for text. Self-hosted only, no Google Fonts link (GDPR).
- **Shapes are round**:
  - Photos sit in arches or domes.
  - The coloured fields have a dome top.
  - Buttons, toggles, fields and step numbers are pills or circles.
- **Offer**: three cards, always called "Angebot": Der Tisch (ab 140 €), Die Feier (ab 270 €), Ihr seid Gäste (ab 350 €), each for 8 children. Each card has a whole photo, Enthält / Ich mache / Passt, wenn, and a button. Nothing is preselected. A button selects its card (raised, outlined) and jumps to the WhatsApp form.
- **Copy is specific**: name the real dishes. Every snack and dessert is a healthy choice. Never invent facts.
- **Photos**: Paulina's own.
  - Hero: `images/v4/table.webp`, the real table in front of the green curtain. Used unretouched on Tural's call: the Frozen canvas and napkins were official decorations. A version without them is in `docs/table-without-disney.webp` if ever needed.
  - Offers: `images/v3/flatlay|theme-cake|cutting.webp`.
  - Never use stock or AI-made food or people.

### Sections in `index.html`

| Section | Purpose |
|---|---|
| `.hero` | "Kommt einfach als Gäste." The real dishes, from 140 €, 8 to 30 children, region. Paulina's curtain table, captioned |
| `#angebote` | Three coloured offer cards, then "Was ihr abgebt" (the chore list, green) |
| `#ablauf` | "So bestellt ihr": three numbered steps and an enquiry button |
| `#essen` | "Gesund bis zum Nachtisch." Snacks, sweets, cake, labels and allergies, named specifically |
| `#paulina` | "Ein Brief von Paulina" on the strawberry-red field (Paulina to confirm wording) |
| `#fragen` | Six questions |
| `#anfrage` | Live WhatsApp message builder (+491783129500), with the package pre-selected (green) |
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
