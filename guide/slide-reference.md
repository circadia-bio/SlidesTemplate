# Slide Reference

A complete reference for every layout, class, and formatting option available in the template.

---

## Slide structure

Every slide starts with a `##` heading and ends with `---`. The heading becomes the slide title.

```markdown
## Slide title

Slide content here.

---

## Next slide
```

The cover slide is a special raw HTML block at the top of the file — do not add a `##` heading for it.

---

## Text classes

### `.intro`

A mid-blue introductory sentence, slightly smaller than body text. Use it as the first line of a slide to set context before the bullets.

```markdown
## Sleep Diaries

::: {.intro}
A consensus-based sleep diary app for iOS, Android and web.
:::

- Feature one
- Feature two
```

### `.cta`

A coral bold accent line. Use it at the bottom of a slide for a URL, version number, or call to action.

```markdown
[v1.1.3 · sleepdiaries.circadia-lab.uk]{.cta}
```

### `**bold**`

Bold text renders in coral, matching the template's emphasis style. Use it for the label part of a bullet:

```markdown
- **Sleep Diaries** — participant-facing sleep diary app
- **ScoreMe** — lab/clinic questionnaire scorer
```

### `.smaller`

Scales down all text on a slide. Apply it to the heading when a slide has more content than usual:

```markdown
## This slide has a lot on it {.smaller}

- Bullet one
- Bullet two
- ...
```

---

## Lists

Lists automatically use coral em-dash bullets. Just write standard Markdown:

```markdown
- First item
- Second item
- Third item
```

Nested lists are supported but use them sparingly — they add visual complexity.

---

## Two-column layout

Use the standard Quarto columns syntax. The template sets `align-items: start` so columns align to the top.

```markdown
:::: {.columns}

::: {.column width="50%"}
Left column content.
:::

::: {.column width="50%"}
Right column content.
:::

::::
```

You can change the widths — for example `width="40%"` and `width="60%"` for an asymmetric split. Make sure they add up to 100%.

---

## Code blocks

Standard fenced code blocks with language syntax highlighting:

````markdown
```r
library(slumbR)
study <- read_study("exports/")
study_summary(study)
```
````

````markdown
```python
import pyActigraphy
reader = pyActigraphy.io.read_raw("data.agd")
```
````

````markdown
```bash
docker compose up
```
````

Inline code uses a coral chip style: write `` `code` `` in your text.

---

## Tables

Standard Markdown tables. The template styles the header row in navy with white text and alternates row backgrounds.

```markdown
| Variable | Definition | Threshold |
|---|---|---|
| `tst_min` | Total sleep time | ≥ 420 min (7 h) |
| `se_pct` | Sleep efficiency | ≥ 85% |
```

---

## Callout blocks

Quarto callouts render with the template colour scheme. Use `.callout-tip` (coral border) for key points and `.callout-note` (blue border) for supplementary information.

```markdown
::: {.callout-tip}
This is a key point worth highlighting.
:::

::: {.callout-note}
This is a supplementary note.
:::
```

---

## Fragments (click-to-reveal)

Wrap content in `::: {.fragment}` to make it appear on click:

```markdown
## The problem we're solving

Tools are often fragmented and brittle.

::: {.fragment}
We built a stack of open-source tools to address this.
:::
```

---

## Incremental lists

Make list items appear one by one:

```markdown
::: {.incremental}
- First point appears on click one
- Second point appears on click two
- Third point appears on click three
:::
```

---

## Background colours

Set a solid background on any slide using `data-background-color`:

```markdown
## Section divider {data-background-color="#004474"}

::: {style="color: white;"}
White text on navy background.
:::
```

---

## Slide visibility

To include backup slides that don't count toward the slide total or progress bar:

```markdown
## Backup slide {visibility="uncounted"}
```

---

## Speaker notes

Add notes visible only in speaker view (press `S` during the presentation):

```markdown
## My slide

Content visible to the audience.

::: {.notes}
This is a note only you can see. Press S to open speaker view.
:::
```

---

## Useful keyboard shortcuts during presentation

| Key | Action |
|---|---|
| `Space` or `→` | Next slide |
| `←` | Previous slide |
| `F` | Fullscreen |
| `S` | Speaker view |
| `O` | Slide overview |
| `B` | Blank/black screen |
| `Esc` | Exit fullscreen / overview |
