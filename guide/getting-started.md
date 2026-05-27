# Getting Started

This guide walks you through setting up the template, editing your first slide deck, and getting it live on GitHub Pages.

---

## Prerequisites

You need two things installed on your machine:

**Quarto** — the tool that renders `.qmd` files into HTML slides.
Download from [quarto.org](https://quarto.org/docs/get-started/). Install the latest release for your OS. You can verify it works by running:

```bash
quarto --version
```

**Git** — for version control and pushing to GitHub.
Most Macs have it already. Check with `git --version`. If not, install via [git-scm.com](https://git-scm.com).

**RStudio** (optional but recommended) — the `.Rproj` file lets you open the project directly and use the Render button. Download from [posit.co](https://posit.co/download/rstudio-desktop/).

---

## Creating your presentation repo

### Option A — GitHub template (recommended)

1. Go to [github.com/circadia-bio/SlidesTemplate](https://github.com/circadia-bio/SlidesTemplate)
2. Click **Use this template → Create a new repository**
3. Name it something descriptive, e.g. `chronobiologyNE_2026` or `lab-meeting-jan-2026`
4. Set visibility to **Public** (required for free GitHub Pages)
5. Click **Create repository**
6. Clone it to your machine:

```bash
git clone https://github.com/circadia-bio/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME
```

### Option B — Clone directly

If you just want a local copy without your own GitHub repo:

```bash
git clone https://github.com/circadia-bio/SlidesTemplate.git my-talk
cd my-talk
```

---

## Project structure

```
YOUR-REPO/
├── index.qmd             # Your presentation source — edit this
├── custom.scss           # Theme file — only touch this if you need style changes
├── _quarto.yml           # Project settings — output directory etc.
├── assets/
│   ├── cover.png         # Cover slide background image
│   ├── circadia_logo.png # Logo watermark shown on every content slide
│   └── northumbria.png   # Northumbria University logo on the cover
├── guide/
│   ├── getting-started.md   # This file
│   ├── slide-reference.md   # All classes, layouts, and formatting options
│   └── github-pages.md      # How to enable and use GitHub Pages
└── .github/workflows/
    └── deploy.yml        # GitHub Actions — renders and deploys automatically
```

You will spend almost all your time in `index.qmd`. The other files rarely need changing.

---

## Editing your slides

Open `index.qmd` in RStudio or any text editor.

### 1. Update the cover slide params

At the very top of the file you'll find a `params:` block. This is the only place you need to edit to customise the cover slide:

```yaml
---
params:
  title: "Presentation Title"
  subtitle: "Subtitle or context"
  presenter: "Presenter Name"
  event: "Conference · Date"
---
```

Change all four values to match your talk. The cover slide will render them automatically — you do not need to touch the raw HTML block below.

You can also override params at render time from the terminal without editing the file:

```bash
quarto render index.qmd -P title:"My Talk" -P presenter:"Lucas França"
```

### 2. Update the footer

In the `format:` block, update the `footer:` line if you want a different footer text on content slides:

```yaml
format:
  revealjs:
    footer: "Circadia Lab · circadia-lab.uk · github.com/circadia-bio"
```

### 3. Add your content slides

After the closing ` ``` ` of the HTML block, add slides using standard Markdown `##` headings:

```markdown
## My slide title

Content goes here.

---

## Next slide
```

Each `---` starts a new slide. See [`slide-reference.md`](slide-reference.md) for all available layouts and formatting options.

---

## Previewing locally

In your terminal, from the project folder:

```bash
quarto preview index.qmd
```

This opens a browser window with a live preview. The slides update automatically every time you save `index.qmd`.

In RStudio, click the **Render** button at the top of the editor — it does the same thing.

---

## Replacing the cover image

The `assets/cover.png` is the full-slide background for the title slide. It contains the clock photo, diagonal cut, cream right panel, logos, and QR code baked in.

To use your own cover:
1. Create an image at **1920 × 1080px** (or any 16:9 ratio)
2. Save it as `assets/cover.png` (replace the existing file)
3. The text overlay in `index.qmd` is positioned for the standard Circadia layout — if your image has a different cream zone, you may need to adjust the `left` and `top` pixel values in the HTML block

---

## Deploying to GitHub Pages

See [`github-pages.md`](github-pages.md) for full instructions. The short version: push to `main` and GitHub Actions handles everything automatically.

---

## Troubleshooting

**Blank slides** — usually caused by missing blank lines inside `:::` div fences. Every `:::` block needs a blank line after the opening fence and before the closing fence.

**Text overflowing** — add `{.smaller}` after the slide title: `## My slide {.smaller}`

**Fonts not loading** — the Google Fonts import requires an internet connection. The fonts load fine in browsers but may fall back to Georgia/serif in some offline renderers.

**Cover text misaligned** — the pixel positions in the HTML block (`left`, `top`, `width`, `height`) are fixed to the 1280×720 slide canvas. If the text drifts, check that `width: 1280` and `height: 720` are still set in the `format:` block. The params values themselves have no effect on positioning.
