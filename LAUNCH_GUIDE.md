# AllesGute.AI — Launch Guide
### From files on your Mac to live at allesgute.ai

---

## Step 1 — Add your photos

Create a folder called `images` inside your `AllesGute.AI` project folder and drop these files in:

| Filename | What it is |
|---|---|
| `hero-party.jpg` | Main hero image — a beautiful party table or happy kids at a birthday |
| `paulina-portrait.jpg` | Paulina's photo for the About section — warm, natural, not corporate |
| `party-1.jpg` | Gallery image |
| `party-2.jpg` | Gallery image |
| `party-3.jpg` | Gallery image |

Then open `index.html`, search for `<!-- Replace with:` and swap the placeholder divs for the real `<img>` tags shown in the comments.

---

## Step 2 — Set up Formspree (contact form)

1. Go to [formspree.io](https://formspree.io) and create a free account
2. Create a new form — name it "AllesGute Bookings"
3. Copy your Form ID (looks like `xpzvwkrb`)
4. Open `index.html`, find `YOUR_FORMSPREE_ID` and replace it with your ID
5. Test by submitting the form — you'll get an email at the address you registered with

---

## Step 3 — Deploy via GitHub Pages

### 3a. Create a GitHub account
Go to [github.com](https://github.com) → Sign up (free). Use your t.salahov@gmail.com or hello@allesgute.ai.

### 3b. Create a new repository
1. Click the **+** button top-right → **New repository**
2. Name it exactly: `allesgute-ai` (or `allesgute.ai` — either works)
3. Set it to **Public**
4. Do NOT initialize with README
5. Click **Create repository**

### 3c. Upload your files
On the empty repo page, click **uploading an existing file** (or drag & drop).

Upload everything inside your `AllesGute.AI` folder:
- `index.html`
- `images/` folder (all photos)

Click **Commit changes**.

### 3d. Enable GitHub Pages
1. In your repo, click **Settings** (top tab)
2. Scroll to **Pages** in the left sidebar
3. Under **Source**, select: **Deploy from a branch**
4. Branch: `main` / folder: `/ (root)`
5. Click **Save**

GitHub will give you a URL like `https://yourusername.github.io/allesgute-ai` — the site is now live there.

### 3e. Add your custom domain
Still in **Settings → Pages**:
1. Under **Custom domain**, type: `allesgute.ai`
2. Click **Save**
3. Check **Enforce HTTPS** (appears after DNS is set up)

---

## Step 4 — Update GoDaddy DNS

1. Log in to [GoDaddy](https://godaddy.com) → My Products → `allesgute.ai` → DNS
2. Delete any existing A records pointing to GoDaddy's servers
3. Add these **4 A records** (one at a time):

| Type | Name | Value | TTL |
|---|---|---|---|
| A | @ | 185.199.108.153 | 600 |
| A | @ | 185.199.109.153 | 600 |
| A | @ | 185.199.110.153 | 600 |
| A | @ | 185.199.111.153 | 600 |

4. Add a **CNAME record**:

| Type | Name | Value | TTL |
|---|---|---|---|
| CNAME | www | yourusername.github.io | 600 |

DNS propagation takes 10–30 minutes, sometimes up to a few hours. Once live, `allesgute.ai` will load your site with HTTPS.

---

## Step 5 — Test everything

- [ ] Site loads at `allesgute.ai`
- [ ] HTTPS padlock shows in browser
- [ ] Language switcher works (DE / EN / PL)
- [ ] Price calculator slider moves correctly
- [ ] Contact form submits and you receive an email
- [ ] Site looks good on your phone

---

## Managing the site after launch

**To change content:** Edit `index.html` on your computer → go back to GitHub → open the file → click the pencil (Edit) icon → paste the new version → Commit. Site updates in ~1 minute.

**To change booking status** (open / closed / booked): In `index.html`, find this near the top of the `<script>` section:

```javascript
const CFG={status:"open",email:"hello@allesgute.ai"};
```

Change `"open"` to `"closed"` or `"booked"` and commit. A banner appears automatically.

**To add a new language:** Duplicate a language block in the `T` object in the script, translate all strings, add the option to the dropdown in the HTML.

---

## Optional: Accept payments

For taking deposits or full payment online, connect one of these to your booking confirmation email:

- **Stripe** — professional, used by most catering businesses, takes ~2% per transaction
- **PayPal** — simpler setup, slightly higher fees
- **Sumup** — popular in Germany, good for in-person + online

Start with Stripe: [stripe.com](https://stripe.com) → create account → use their Payment Links feature (no code needed) — paste the link into your booking confirmation email.

---

*Built with love for Paulina & AllesGute.AI — May 2026*
