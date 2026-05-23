# 🎞️ SlidesTemplate

**Circadia Lab Quarto/RevealJS presentation template.**

[![License: MIT](https://img.shields.io/badge/licence-MIT-yellow)](./LICENSE)
[![Quarto](https://img.shields.io/badge/Quarto-RevealJS-blue?logo=quarto)](https://quarto.org)

---

## 📖 What is this?

A ready-to-use Quarto RevealJS slide template matching the Circadia Lab visual identity — Playfair Display headings, Alice body text, navy/coral/cream colour palette, and the split-panel cover slide.

Clone or use as a GitHub template to start a new presentation in seconds. Every push to `main` automatically re-renders the slides and publishes them to a public GitHub Pages URL — no manual export required.

---

## 🚀 Quick start

```bash
# 1. Click "Use this template" on GitHub and name your new repo
# 2. Clone it
git clone https://github.com/circadia-bio/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME

# 3. Preview locally
quarto preview template.qmd

# 4. Edit template.qmd, commit, and push — slides deploy automatically
git add -A
git commit -m "✨ feat: initial slide content"
git push
```

See [`docs/getting-started.md`](docs/getting-started.md) for a full step-by-step guide.

---

## 🗂️ Structure

```
SlidesTemplate/
├── template.qmd              # ⭐ Your presentation — edit this
├── custom.scss               # Circadia Lab theme (fonts, colours, layout)
├── _quarto.yml               # Quarto project config
├── SlidesTemplate.Rproj      # RStudio project file
├── assets/
│   ├── cover.png             # Cover slide background
│   ├── circadia_logo.png     # Watermark shown on every content slide
│   └── northumbria.png       # Northumbria University logo on cover
├── .github/
│   └── workflows/
│       └── deploy.yml        # Auto-render + deploy to GitHub Pages
└── docs/
    ├── getting-started.md    # Full setup and authoring guide
    ├── slide-reference.md    # All available classes and layouts
    └── github-pages.md       # How to enable and use GitHub Pages
```

---

## ✨ Features

- **Cover slide** — full-bleed background with right-aligned title, subtitle, presenter, date; footer and logo hidden automatically
- **Content slides** — cream background, Playfair Display titles, Alice body, coral em-dash bullets
- **`.intro`** — mid-blue introductory paragraph
- **`.cta`** — coral bold accent line
- **`.smaller`** — scale down font on content-heavy slides
- **Two-column layouts** — `:::: {.columns}` with sensible defaults
- **Circadia logo watermark** — 35% opacity, auto-hidden on cover
- **Auto-deploy** — GitHub Actions renders and publishes on every push

---

## 🎨 Colour palette

| Token | Hex | Use |
|---|---|---|
| Navy | `#004474` | Titles, primary text |
| Blue | `#1B6799` | Subtitles, intro text, footer |
| Coral | `#FC544A` | Bullets, bold emphasis, CTAs |
| Cream | `#FAEBD7` | Slide background |

---

## 📚 Documentation

| Guide | What it covers |
|---|---|
| [`docs/getting-started.md`](docs/getting-started.md) | Installation, first render, file overview |
| [`docs/slide-reference.md`](docs/slide-reference.md) | Every class, layout, and formatting option |
| [`docs/github-pages.md`](docs/github-pages.md) | Enabling Pages, custom domains, troubleshooting |

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
- 🛏 [**slumbR**](https://github.com/circadia-bio/slumbR) — R companion for Sleep Diaries exports
- 🧮 [**tallieR**](https://github.com/circadia-bio/tallieR) — R companion for ScoreMe exports
- 🔬 [**circadia-bio**](https://github.com/circadia-bio) — the Circadia Lab GitHub organisation

---

## 📄 Licence

Released under the [MIT License](./LICENSE).

Copyright © Circadia Lab — Lucas França & Mario Leocadio-Miguel
