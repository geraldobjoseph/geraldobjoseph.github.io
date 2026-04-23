# Geraldo Joseph — Site Editor Manual

A plain-language guide for updating your portfolio.
No coding knowledge needed for most tasks — just find, edit, save.

---

## Quick Access

### Option A — Edit directly in your browser (GitHub)
1. On any page of your site, **triple-click the copyright text** in the footer (the "© Geraldo Joseph…" line)
2. A hidden admin panel appears
3. Click **"Edit index.html on GitHub"** — you'll be prompted to sign into GitHub
4. Make your changes in the web editor, then scroll down and click **"Commit changes"**
5. Your site updates automatically within 1–2 minutes

> **Why is it hidden?** The trigger is invisible to visitors. The real security layer is your GitHub login — only someone with access to your GitHub account can actually save changes.

### Option B — Edit in VS Code (recommended for bigger changes)
1. Open the repo folder in VS Code
2. Edit `index.html` directly
3. Save the file
4. Push to GitHub (`Ctrl+Shift+G` → commit message → click "Sync Changes")
5. Site is live within 1–2 minutes

---

## How the File is Structured

The file has three main areas:

```
<head>          — Settings, fonts, all CSS styles
<body>          — Visible content (nav, sections, footer)
<script>        — Behaviour (animations, hamburger menu, admin panel)
```

You will almost always only touch **`<body>`**. The five sections are:

| Section    | HTML anchor | Label in code         |
|------------|-------------|----------------------|
| About      | `#about`    | `01 — About`         |
| Certs      | `#certs`    | `02 — Certifications`|
| Skills     | `#skills`   | `03 — Skills`        |
| Roadmap    | `#roadmap`  | `04 — Career Roadmap`|
| Contact    | `#contact`  | `05 — Contact`       |

---

## Common Tasks

### Update the About text

Find this block:

```html
<div class="about-text" style="margin-top:2rem;">
  <p>
    I'm a SysOps engineer with a strong…
  </p>
  <p>
    The transition isn't a pivot…
  </p>
  <p>
    Currently pursuing…
  </p>
</div>
```

Edit the text inside the `<p>` tags. Add or remove `<p>…</p>` blocks as needed.

---

### Update the stat cards (the big numbers)

Find the `.about-stats` block:

```html
<div class="about-stats reveal">
  <div class="stat-card">
    <div class="stat-num">2</div>
    <div class="stat-label">Certs Earned</div>
  </div>
  …
</div>
```

Change the number inside `<div class="stat-num">` and the label inside `<div class="stat-label">`.

---

### Mark a certification as "Earned"

Find the cert card you want to update. Change its class from `in-progress` or `planned` to `earned`, update the status text, and remove the `--fill-amount` style if present:

**Before (in-progress):**
```html
<div class="cert-card in-progress reveal">
  <div class="cert-status">Exam Ready</div>
  <div class="cert-name">CompTIA Security+</div>
  …
  <div class="cert-bar">
    <div class="cert-bar-fill" style="--fill-amount: 0.88;"></div>
  </div>
</div>
```

**After (earned):**
```html
<div class="cert-card earned reveal">
  <div class="cert-status">Earned</div>
  <div class="cert-name">CompTIA Security+</div>
  …
  <div class="cert-bar"><div class="cert-bar-fill"></div></div>
</div>
```

That's it. The green colour and full progress bar are applied automatically.

Also remember to update the **stat card** number for "Certs Earned" in the About section.

---

### Add a brand new certification

Copy this template and paste it inside the `<div class="cert-grid">` block, after the last existing `</div>` closing a cert card:

```html
<div class="cert-card planned reveal">
  <div class="cert-status">Planned</div>
  <div class="cert-name">CERT NAME HERE</div>
  <div class="cert-issuer">ISSUER · Short description</div>
  <div class="cert-detail">One or two sentences about why this cert matters.</div>
  <div class="cert-bar" style="opacity:0.3"><div class="cert-bar-fill"></div></div>
</div>
```

Change `planned` to `in-progress` or `earned` as appropriate.

**Progress bar fill amounts** (for `in-progress` only):

| Progress | Value |
|----------|-------|
| 25%      | `style="--fill-amount: 0.25;"` |
| 50%      | `style="--fill-amount: 0.50;"` |
| 75%      | `style="--fill-amount: 0.75;"` |
| 90%      | `style="--fill-amount: 0.90;"` |
| 100%     | Use `earned` class instead |

---

### Add a skill tag

Find the relevant skill group (e.g. "DevOps & Cloud (Building)") and add a new `<span>` inside `.skill-tags`:

```html
<span class="skill-tag core">Terraform</span>
```

Use `core` for solid/proven skills, `learning` for skills you are actively building.

---

### Update the Career Roadmap

Each step is a `.roadmap-item`. The dot class controls the colour:

| Class    | Meaning                  | Colour       |
|----------|--------------------------|--------------|
| `done`   | Completed                | Green        |
| `active` | Currently working on     | Red/accent   |
| `next`   | Upcoming / planned       | Grey         |

To advance a step (e.g. Security+ from active → done after passing the exam):

1. Change `.roadmap-dot active` → `.roadmap-dot done`, and change the symbol to `✓`
2. Change `.roadmap-tag active` → `.roadmap-tag done`
3. Update the tag text from `"Exam Imminent"` to `"Complete"`
4. Change Linux+ dot from `next` to `active`, update its tag

---

### Update contact information

Find the contact section and edit the `href` attributes:

```html
<a href="mailto:YOUR@EMAIL.COM" class="contact-link">Email</a>
<a href="https://linkedin.com/in/YOUR-SLUG" …>LinkedIn</a>
<a href="https://github.com/YOUR-USERNAME" …>GitHub</a>
```

---

### Update hero tagline

Find the `<p class="hero-title">` block:

```html
<p class="hero-title">
  <strong>Systems-first thinking, cloud-ready execution.</strong><br>
  Building on a solid foundation…
</p>
```

Edit the bold headline and/or the sentence below it.

---

## Admin Panel URL — If Your Repo Changes

If you rename your GitHub repository, update this URL inside `index.html`:

```html
href="https://github.com/geraldobjoseph/geraldobjoseph.github.io/edit/main/index.html"
```

Pattern: `https://github.com/USERNAME/REPO-NAME/edit/BRANCH/index.html`

---

## Colours & Fonts — Quick Reference

All colours are defined at the top of the `<style>` block as CSS variables. You only need to change these two lines to re-brand the whole site:

```css
--ink:    #0C0C0C;   /* Text, dark elements */
--accent: #D63200;   /* Red — headings, highlights, active states */
```

Fonts are loaded from Google Fonts. The three used are:
- **Syne** — headings and display text
- **IBM Plex Mono** — labels, tags, small caps text
- **DM Sans** — body copy

---

## Deploying Changes

Changes made through the GitHub web editor or pushed via VS Code deploy automatically via **GitHub Pages**. No build step is needed. Expect a 1–3 minute delay for changes to appear live.

To check deployment status: GitHub repo → **Actions** tab → look for a green tick.

---

*Keep this file in your repo root for future reference.*
