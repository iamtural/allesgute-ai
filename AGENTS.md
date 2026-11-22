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

### Brand (round 5, Nov 22 2026, branch `feature/round-5-chalk`)

- **Name**: always **"Alles Gute"**, with a space. Domain/email stay `allesgute.ai`; never show ".ai" in the brand.
- **Buyer**: a busy, posh millennial mother in Berlin or Märkisch-Oderland. Unmistakably clear: what it is, three offers, how to order.
- **The one idea**: Paulina's own black chalk dish labels ("Banana Waffeln", "Apfel Kuchen", "Pizza Muffins"). The hero photo is her real label; prices are black label shapes standing in front of the food; the food section is her labels as they stood on the table. Never fake her handwriting in a font.
- **Colour** (from her table): pale-sage ground `#dce5dc`; chalkboard black `#1a1c1a` (ink, price labels, the food field); chalk `#eeefe9` on black; strawberry red `#ab2a40` for actions and Paulina's letter; curtain green `#2d514c` for the hand-over list and the enquiry. Offer cards keep blush `#f0d9d1`, butter `#efe2b8`, sky `#d4dfec` (Tural's call). No cream or warm white.
- **Type**: EB Garamond 400 set large (hero up to 144px, tracking -0.04em) for headings, letter, prices; Jost 400/500 for text. Self-hosted only.
- **Shapes**: photos are square-cornered editorial crops (round-3 arches retired). Labels and fields use a 9px radius like her real label holders; buttons stay pills.
- **Motion**: hero crossfade of three of her photos (dots to choose, stops on choice), a slow filmstrip of ten of her photos (pauses on hover/focus), section entrances. All off under reduced motion.
- **Photos**: Paulina's own, cropped tight so no licensed characters (Frozen, Paw Patrol, character toppers) are visible. Crops live in `images/v5/`. Never alter her photos beyond cropping without asking. Never use stock or AI-made food or people.

### Sections in `index.html`

| Section | Purpose |
|---|---|
| `.hero` | "Kommt einfach als Gäste." The real dishes, three chalk price labels, region. Crossfade of her label, table and waffles |
| `.film` | "Von Paulinas Tischen": moving strip of ten of her photos |
| `#angebote` | Three coloured offer cards, then "Was ihr abgebt" (the chore list, green) |
| `#ablauf` | "So bestellt ihr": three numbered steps and an enquiry button |
| `#essen` | Black chalk field. "Gesund bis zum Nachtisch." Her real labels, plus snacks, sweets, cake, allergies |
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
