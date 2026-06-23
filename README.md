# Nicole Lee — academic portfolio

A clean academic website built with [Quarto](https://quarto.org) and hosted free on
GitHub Pages. **About** and **Research** are live; Hardware / Tools / Writing
are stubbed.

---

## One-time setup (before you can preview)

1. **Install Quarto** → <https://quarto.org/docs/get-started/> (it was not installed on
   the machine that scaffolded this site).
2. **Install the Academicons extension** (needed for the ORCID + Google Scholar navbar
   icons — they will not render without it). From this folder run:
   ```
   quarto add schochastics/academicons
   ```
   This creates an `_extensions/` folder — commit it.

## Preview locally

```
quarto preview
```

Opens a live-reloading preview in your browser. Edit a `.qmd`, save, and it refreshes.
**Render early and tweak the SCSS** — Bootstrap/Quarto class names sometimes differ from
the starting selectors in `theme-light.scss`; inspect in the browser and adjust.

## Deploy

Deployment is automatic via GitHub Actions (`.github/workflows/publish.yml`): **every
push to `main`** rebuilds the site and publishes it to the `gh-pages` branch.

One-time step on GitHub: **Settings → Pages → Build and deployment → Source = Deploy from
a branch → `gh-pages` / `(root)`.**

Manual alternative: `quarto publish gh-pages`.

**This repo is named `lnicole08.github.io`**, so the live site will be at the clean root
URL: **<https://lnicole08.github.io/>**.

(Future: when you rename your GitHub account, rename this repo to `‹new-username›.github.io`
to keep the bare-root URL.)

---

## Editing content

Pages are plain Quarto markdown (`.qmd`) — prose + media. Edit the file, save, push.

- About → `index.qmd`
- Research → `research.qmd`
- Stubs → `hardware.qmd`, `tools.qmd`, `writing.qmd`

### Adding media (all media lives in `images/`)

1. **Photo / CAD render / diagram** — save to `images/`, then:
   ```
   ![Alt text describing the image](images/your-file.jpg){width="600"}
   ```
   Always write real alt text. JPG/PNG/WebP all fine. Keep each under ~2 MB.
2. **Short looping clip** (fly behaviour, rig, CAD turntable) — export an **MP4** to
   `images/`, then:
   ```
   {{< video images/your-clip.mp4 >}}
   ```
   Keep local videos under ~50 MB (GitHub warns at 50 MB, blocks at 100 MB). MP4 beats GIF.
3. **Longer / heavier video** — upload to YouTube/Vimeo and embed by URL:
   ```
   {{< video https://youtu.be/VIDEO_ID >}}
   ```
   Recommended for anything over ~30 s — keeps the repo small.

**Find every spot that needs you:** search the source for `NICOLE:` — each is a visible
HTML comment marking a media slot or input. Search for `‹TODO` for the remaining
placeholder links/text.

---

## Outstanding follow-ups

- [x] Install Quarto + run `quarto add schochastics/academicons` (see setup above).
- [ ] **Contact form — create a new email** dedicated to the site (so your personal
      address stays private).
- [ ] **Contact form — sign up at [formspree.io](https://formspree.io)** with that new
      email, create a form, and **give the Formspree form ID to Claude** (or paste it into
      `contact.qmd`, replacing `REPLACE_WITH_FORMSPREE_ID`). The email never appears on the
      public page — only the form ID does.
- [x] Fill `‹TODO›` links: GitHub, Google Scholar, LinkedIn (in `_quarto.yml` and
      `index.qmd`).
- [x] Add headshot → `images/nicole.jpg` (square crop).
- [x] Confirm the homepage tagline and the menu font (Jost confirmed).
- [ ] Set **Settings → Pages** source to `gh-pages` after the first push.

### Deliberately deferred (do later, only if you want them)

- **Dark mode** — palette is ready in the brief; add `theme-dark.scss` and switch
  `_quarto.yml` to `theme: { light: theme-light.scss, dark: theme-dark.scss }`.
- **Hardware / Tools / Writing** content — currently stubs.
- **Executable notebook pages** (e.g. a live DABEST figure) — Quarto can run an `.ipynb`
  at render time; add a Python step to the publish Action then. **nbdev is not used and
  not needed** for the portfolio.
