# 🎞️ SlidesTemplate

**Circadia Lab Quarto/RevealJS presentation template.**

[![License: MIT](https://img.shields.io/badge/licence-MIT-yellow)](./LICENSE)
[![Quarto](https://img.shields.io/badge/Quarto-RevealJS-blue?logo=quarto)](https://quarto.org)

---

## 📖 What is this?

A ready-to-use Quarto RevealJS slide template matching the Circadia Lab visual identity — Playfair Display headings, Alice body text, navy/coral/cream colour palette, and the split-panel cover slide.

Clone or use as a GitHub template to start a new presentation in seconds.

---

## 🚀 Getting Started

### Prerequisites

- [Quarto](https://quarto.org) ≥ 1.4
- [R](https://www.r-project.org/) + RStudio (optional — for the `.Rproj`)

### Use as a template

Click **Use this template** on GitHub, name your repo, then clone it locally.

### Or clone directly

```bash
git clone https://github.com/circadia-bio/SlidesTemplate.git my-talk
cd my-talk
```

### Add your assets

Replace the placeholder text in `template.qmd` and drop your own `cover.png` into `assets/` if you want a custom cover image. The shared Circadia and Northumbria logos are already included.

### Preview

```bash
quarto preview template.qmd
```

### Render

```bash
quarto render template.qmd
```

Output goes to `docs/`.

---

## 🗂️ Structure

```
SlidesTemplate/
├── template.qmd          # ⭐ Start here — edit this for your talk
├── custom.scss           # Circadia Lab theme (fonts, colours, layout)
├── _quarto.yml           # Project config
├── SlidesTemplate.Rproj  # RStudio project file
├── assets/
│   ├── cover.png         # Cover slide background (replace with your own)
│   ├── circadia_logo.png # Circadia Lab logo (watermark on slides)
│   └── northumbria.png   # Northumbria University logo
└── .github/workflows/
    └── deploy.yml        # Auto-render and deploy to gh-pages on push
```

---

## ✨ Features

- **Cover slide** — full-bleed background image with right-aligned title, subtitle, presenter, date; footer and logo hidden automatically
- **Content slides** — cream background, Playfair Display titles, Alice body, coral em-dash bullets
- **`.intro`** — mid-blue intro paragraph class
- **`.cta`** — coral bold accent line
- **`.smaller`** — Quarto native class for slides with more content
- **Two-column layouts** — `:::: {.columns}` with `align-items: start`
- **Circadia logo watermark** — 35% opacity, bottom-left, hidden on cover
- **Auto-deploy** — GitHub Actions renders and publishes to `gh-pages` on every push to `main`

---

## 🎨 Colour palette

| Token | Hex | Use |
|---|---|---|
| Navy | `#004474` | Titles, primary text |
| Blue | `#1B6799` | Subtitles, intro text, footer |
| Coral | `#FC544A` | Bullets, emphasis, CTAs |
| Cream | `#FAEBD7` | Slide background |

---

## 👥 Authors

| Role | Name |
|---|---|
| Developer / Researcher | Lucas França |
| Researcher | Mario Leocadio-Miguel |

---

## 🤝 Related Tools

- 🌙 [**SleepDiaries**](https://github.com/circadia-bio/SleepDiaries) — participant-facing sleep diary app
- 📋 [**ScoreMe**](https://github.com/circadia-bio/ScoreMe) — research questionnaire scorer
- 🔬 [**circadia-bio**](https://github.com/circadia-bio) — the Circadia Lab GitHub organisation

---

## 📄 Licence

Released under the [MIT License](./LICENSE).

Copyright © Circadia Lab — Lucas França & Mario Leocadio-Miguel
