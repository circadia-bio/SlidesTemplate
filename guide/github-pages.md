# GitHub Pages

This template is configured to automatically render your slides and publish them as a public website every time you push to `main`. This page explains how to enable it, how it works, and how to troubleshoot common issues.

---

## How it works

The file `.github/workflows/deploy.yml` defines a GitHub Actions workflow that runs on every push to `main`. It does three things in sequence:

1. **Checkout** — downloads your repo onto a temporary Ubuntu machine
2. **Render** — runs `quarto render` to convert `index.qmd` into `docs/index.html`
3. **Deploy** — pushes the contents of `docs/` to a branch called `gh-pages`

GitHub Pages then serves whatever is on `gh-pages` as a public website. You never need to render locally or manually upload anything.

---

## Enabling GitHub Pages (one-time setup)

You only need to do this once per repo.

**Step 1 — Push to main at least once**

The `gh-pages` branch is created automatically by the first successful workflow run. It does not exist until you push.

```bash
git push origin main
```

Wait about 60 seconds, then check the **Actions** tab on GitHub to confirm the workflow ran successfully (green tick).

**Step 2 — Enable Pages in repo settings**

1. Go to your repo on GitHub
2. Click **Settings** (top menu)
3. Click **Pages** (left sidebar, under *Code and automation*)
4. Under **Source**, select **Deploy from a branch**
5. Under **Branch**, select `gh-pages` and folder `/ (root)`
6. Click **Save**

GitHub will show a banner with your live URL — it looks like:

```
https://circadia-bio.github.io/YOUR-REPO-NAME/
```

It may take 1–2 minutes for the site to go live the first time.

---

## Your live URL

The URL follows this pattern:

```
https://circadia-bio.github.io/YOUR-REPO-NAME/
```

For example, a repo named `chronobiologyNE_2026` would be at:

```
https://circadia-bio.github.io/chronobiologyNE_2026/
```

Share this URL with your audience instead of emailing a PDF.

---

## Updating your slides

Every time you push to `main`, the workflow reruns and the live URL updates automatically. There is nothing else to do.

```bash
# Make your changes to index.qmd, then:
git add index.qmd
git commit -m "📚 docs: update slide content for session 2"
git push
```

The site will reflect your changes within about 60–90 seconds of the push.

---

## Triggering the workflow manually

If you want to redeploy without making a code change — for example after changing a setting — you can trigger the workflow manually:

1. Go to your repo on GitHub
2. Click the **Actions** tab
3. Click **Render & Deploy to GitHub Pages** in the left sidebar
4. Click **Run workflow → Run workflow**

---

## Checking workflow status

Go to the **Actions** tab in your repo. Each push creates a new workflow run. Click on a run to see the logs for each step.

A green tick means the site deployed successfully.
A red cross means something failed — click the failed step to read the error message.

Common failure causes are listed in the Troubleshooting section below.

---

## What is `docs/` for?

Quarto renders the slides into `docs/` locally when you run `quarto render`. The `.gitignore` excludes `docs/` from your commits — the GitHub Action renders it fresh in the cloud each time. This means:

- Your repo stays clean (no generated HTML committed)
- The live site is always built from the latest source
- You never need to run `quarto render` before pushing

If you run `quarto render` locally, the output goes to your local `docs/` folder but is not committed. That is intentional.

---

## Repo must be public

GitHub Pages is free for public repositories. If your repo is private, Pages requires a GitHub Pro, Team, or Enterprise plan. Make sure your repo is set to **Public** in Settings → General.

---

## Troubleshooting

**Actions tab shows no workflows**

The `.github/workflows/deploy.yml` file is missing or was not committed. Check that it exists:

```bash
ls .github/workflows/
```

If missing, copy it from the SlidesTemplate repo and commit it.

---

**Workflow fails at the Render step**

Usually a syntax error in `index.qmd`. Run `quarto render index.qmd` locally to see the error message. Common causes:

- Missing blank line before or after a `:::` div fence
- Unclosed `::::` columns block
- Invalid YAML in the front matter

---

**Workflow fails at the Deploy step with a permissions error**

The workflow needs write access to push to `gh-pages`. Check that `permissions: contents: write` is present in `deploy.yml`:

```yaml
permissions:
  contents: write
```

Also check: Settings → Actions → General → Workflow permissions → set to **Read and write permissions**.

---

**Site shows a 404**

Either Pages is not enabled yet, or you are using the wrong URL. Double-check:

1. Settings → Pages → Branch is set to `gh-pages`, folder `/ (root)`
2. The workflow ran successfully (green tick in Actions)
3. The URL matches the pattern `https://circadia-bio.github.io/REPO-NAME/` exactly

---

**Site shows old content**

The workflow may not have run yet, or it failed silently. Check the Actions tab. If the latest run is green but content is stale, do a hard refresh in your browser (`Cmd+Shift+R` on Mac, `Ctrl+Shift+R` on Windows/Linux).

---

**Images not showing on the live site**

All assets must be inside the `assets/` folder and referenced with relative paths in `index.qmd`:

```markdown
assets/cover.png          ✅ correct
/assets/cover.png         ❌ wrong — absolute path breaks on GitHub Pages
~/assets/cover.png        ❌ wrong
```

---

## Presentation tips

Once your slides are live, you can present directly from the URL in any browser — no software needed on the presentation machine. A few useful options:

- Press `F` for fullscreen
- Press `S` to open speaker view (notes + timer) in a second window
- Press `O` for a slide overview / navigation grid
- Add `?print-pdf` to the URL to get a print-friendly view for PDF export
