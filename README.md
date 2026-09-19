# Amos Maponya — Portfolio

A single-page personal portfolio site. Plain HTML, CSS and JavaScript — no framework,
no build step, no dependencies.

## Run it locally

Just double-click `index.html`.

Or, if you'd rather serve it properly (recommended, so the PDF download and fonts behave
exactly as they will in production):

```bash
python -m http.server 8000
# then open http://localhost:8000
```

## Files

```
index.html          all page content
styles.css          design tokens + all styling (light & dark themes)
main.js             theme toggle, mobile menu, scroll-spy, reveal animations
assets/
  img/              portrait + graduation photos
  logos/            ADEI, Sand Technologies, Genpact, ERG Africa
  docs/             Amos-Maponya-CV.pdf  (the downloadable résumé)
```

The original source images and CV are still in the project root; `assets/` holds the
renamed copies the site actually uses.

## Editing content

Everything is in `index.html`, in plain HTML in the order it appears on the page.

| To change… | Look for… |
|---|---|
| Hero headline / intro | `<section class="hero">` |
| About narrative | `<section id="about">` |
| Jobs | `<li class="job">` inside `<section id="experience">` |
| Projects | `<article class="card">` inside `<section id="projects">` |
| Skills | `<div class="skill-block">` inside `<section id="skills">` |
| Education | `<article class="edu">` inside `<section id="education">` |
| Email / phone / links | `<section id="contact">` |

To change the accent colour, edit `--accent` (and the dark-mode `--accent`) at the top of
`styles.css`. Everything else follows from it.

### Adding a new job

Copy an existing `<li class="job">…</li>` block, change the text, and drop the company
logo into `assets/logos/`. Logos are assumed to be **dark artwork on a white/light ground** —
they blend into the page in light mode and sit on a white plate in dark mode. A logo that is
*light* artwork won't be visible; recolour it or export it dark before adding it.

## Deploying to Vercel

The site is static, so there is no build command and no framework preset needed.

**Option A — CLI (fastest):**

```bash
npm i -g vercel
cd "C:\Users\amosp\Desktop\Portfolio"
vercel
# Framework preset: Other · Build command: (leave empty) · Output directory: ./
```

**Option B — GitHub:**

1. Create a new, empty repo on GitHub (e.g. `amos-portfolio`).
2. In this folder: `git init && git add . && git commit -m "Portfolio site"`
3. `git remote add origin <your-repo-url>` then `git push -u origin main`
4. On vercel.com → *Add New Project* → import the repo → Framework preset **Other** → Deploy.

Netlify and GitHub Pages work the same way — it's a static folder.

## Browser support

Modern Chrome, Edge, Firefox and Safari. Respects `prefers-reduced-motion` and
`prefers-color-scheme`, and has a print stylesheet.
