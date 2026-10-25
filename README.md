# R-4-HASS — Quarto Book Project

Working materials for *Quantitative and Reproducible Research with R in the Humanities*. Teaching material for the LMU Munich block seminar (18–19 Dec 2026 & 8–9 Jan 2027).

Repo: <https://github.com/MartinSchweinberger/R-4-HASS>
Expected published URL: <https://martinschweinberger.github.io/R-4-HASS/>

## Status

Quarto **book** project (`project: type: book`, native `.qmd`, not bookdown). 10 of 11 planned units are drafted; chapters 3, 4, 8, 9 are the earlier June drafts that still need the adaptation pass; chapter 11 content was folded into chapter 10 by design.

| # | Unit | File | Status |
|---|------|------|--------|
| 1 | Introduction to R and RStudio | `chapters/01-r_intro.qmd` | ✅ adapted |
| 2 | Working with Data in R | `chapters/02-data_loading.qmd` | ✅ adapted |
| 3 | String Processing | `chapters/03-string-processing.qmd` | ⚠️ June draft — adaptation pass pending |
| 4 | Regular Expressions | `chapters/04-regular-expressions.qmd` | ⚠️ June draft — adaptation pass pending |
| 5 | Data Cleaning and Tables | `chapters/05-tables.qmd` | ✅ adapted |
| 6 | Data Visualisation with ggplot2 | `chapters/06-data_viz_intro.qmd` | ✅ adapted (aggressively trimmed from LADAL original) |
| 7 | Statistics: Inferential Tests and Regression | `chapters/07-statistics.qmd` | ✅ adapted (merge of 3 LADAL tutorials) |
| 8 | Mixed-Effects Models | `chapters/08-mixed-effects-models.qmd` | ⚠️ June draft — adaptation pass pending |
| 9 | Text Analysis (Corpus Methods) | `chapters/09-text-analysis.qmd` | ⚠️ June draft — adaptation pass pending |
| 10 | Reproducible Research & Publishing | `chapters/10-publish.qmd` | ✅ adapted (also covers planned unit 11) |
| 11 | Publishing via GitHub | — | ✻ merged into Chapter 10 |

**Scope deviations from the course description to note:**

- Chapter 7 drops PCA and clustering ("multivariate techniques" in the course description). The chapter now focuses on classical inference and regression as the foundation for Chapter 8.
- Chapter 10 combines the planned Units 10 (Quarto authoring) and 11 (GitHub publishing) into one unit. The chapter is heavy on publishing and lighter on authoring, on the assumption that students will have been reading a Quarto book throughout the course.
- Chapter 6 trimmed the LADAL data-viz tutorial from ~4,700 lines to ~550 lines. The advanced topics (patchwork, annotations, legend fine-tuning, shapes/lines detail) are pointed at as further resources rather than taught.

## Publishing to GitHub Pages

### Current state

`docs/` is in `.gitignore` — nothing is being served yet. To go live, choose one of the two approaches below.

### Approach A — Manual (recommended for first publish)

Simplest, works today, consistent with what Chapter 10 teaches. The trade-off: you must re-render locally before every push.

1. **Remove `docs/` from `.gitignore`**:
   ```
   # Edit .gitignore and delete the `docs/` line
   ```

2. **Install LaTeX for PDF output** (one-time, if you plan to generate PDF alongside HTML):
   ```r
   install.packages("tinytex")
   tinytex::install_tinytex()
   ```

3. **Render the book locally** from the project root:
   ```
   quarto render
   ```
   HTML lands in `docs/`. Open `docs/index.html` in a browser to review.

4. **Commit and push**:
   ```
   git add docs/ .gitignore
   git commit -m "Publish rendered book to docs/"
   git push
   ```

5. **Enable Pages on GitHub**:
   - Go to <https://github.com/MartinSchweinberger/R-4-HASS/settings/pages>
   - **Source**: *Deploy from a branch*
   - **Branch**: `main`, **Folder**: `/docs`
   - **Save**

6. Wait 1–3 minutes. The site goes live at <https://martinschweinberger.github.io/R-4-HASS/>.

For every subsequent update: edit → `quarto render` → review `docs/index.html` → `git add docs/` → commit → push.

### Approach B — GitHub Actions (later migration)

Cleaner long-term: Actions renders on push, you never commit `docs/`. Takes an afternoon to set up correctly because the Action has to install all your R package dependencies on each run. Worth doing once the book is stable and you want students to be able to contribute without having Quarto locally.

Create `.github/workflows/publish.yml`:

```yaml
name: Render and Publish

on:
  push:
    branches: main
  workflow_dispatch:

jobs:
  build-deploy:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4

      - uses: quarto-dev/quarto-actions/setup@v2

      - uses: r-lib/actions/setup-r@v2
        with:
          r-version: '4.3.2'

      - name: Install R package dependencies
        run: |
          install.packages(c(
            "tidyverse", "here", "flextable", "checkdown",
            "ggplot2", "dplyr", "tidyr", "stringr", "readr",
            "readxl", "jsonlite", "xml2",
            "e1071", "effectsize", "report", "performance", "car", "broom",
            "scales", "RColorBrewer", "viridis",
            "lme4", "lmerTest", "MuMIn", "sjPlot",
            "quanteda", "tm", "tidytext", "gutenbergr",
            "rmarkdown", "knitr"
          ))
        shell: Rscript {0}

      - name: Render and publish
        uses: quarto-dev/quarto-actions/publish@v2
        with:
          target: gh-pages
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```

Then on GitHub: **Settings → Pages → Source: GitHub Actions**. The first push after this triggers a build (visible in the Actions tab). Published to `gh-pages` branch, which Pages serves automatically.

Note: the Action takes 5–10 minutes per build because it reinstalls all R packages each time. Caching via `r-lib/actions/setup-r-dependencies` with `renv` is the proper fix but requires an `renv.lock` file in the repo.

## Before you render

### 1. Missing data files (will cause hard errors)

Copy these from the LADAL tutorial data folders into `data/` at the repo root. All chapters use `here::here("data", "filename.rda")` so the location is standardised.

**Chapter 2 — Data Loading:**
- `testdat.csv`, `testdat2.csv`, `testdat.txt`, `testdat.xlsx`, `testdat.rda`, `english.txt`, `data.json`, `data.xml`, `mydoc.docx`

**Chapter 3 — String Processing** (June draft):
- `tx1.rda`, `tx2.rda`, `tx3.rda`, `tx4.rda`, `testcorpus/linguistics04.txt`
- The `linguistics04.txt` has hardcoded quiz answers (101 words, 673 characters) tied to this specific file — see TODO callout in the chapter.

**Chapter 6 — Data Visualisation:**
- `pvd.rda` (Penn Parsed Corpora of Historical English)

**Chapter 7 — Statistics:**
- Inferential: `itdata.rda`, `ptdata.rda`, `fedata.rda`, `mwudata.rda`, `uhmdata.rda`, `frdata.rda`, `x2data.rda`, `x2edata.rda`, `mdata.rda`, `d03.rda`
- Regression: `sld.rda`, `mld.rda`, `bld.rda`

**Chapter 8 — Mixed-Effects Models** (June draft):
- `lmd.rda`, `mbd.rda`, `cld.rda`, `ratex.rda`, `pict.rda`

**Chapter 9 — Text Analysis** (June draft):
- `darwin.rda`, `melville.rda`, `orwell.rda`
- `alice.rda` is optional — the chapter falls back to downloading via `gutenbergr`.

Each location is also flagged with a `callout-warning` in the chapter itself.

### 2. checkdown rendering — unverified

All checkdown interactive quiz blocks (radio-button questions, hints) remain in chapters 3, 4, 7, 8, 9. The package is built for plain RMarkdown/Quarto HTML and *should* work in a Quarto book, but this has not been confirmed. After first render, check the quiz widgets actually display and function. Fallback: convert to static `callout-tip` "Exercise" blocks. Quick fix if needed.

### 3. Bibliography — needs verification

`references.bib` contains 10 citation keys from the June drafts: Barr et al. 2013, Bartoń/MuMIn, Bell 2008, Friedl 2006, Johnson 2009/2014, Murayama 2014, Peng 2016, Pinheiro & Bates 2000, Winter 2019, Zuur & Ieno. Several entries marked `% VERIFY` because exact page numbers, editions, or (in one case) year could not be confirmed against primary sources. Check before publishing.

The newly-adapted chapters (1, 2, 5, 6, 7, 10) do not add new bib entries — they reference Winter (2019), Gries (2021), Field et al. (2012), Wickham (2016) in prose only. Add proper entries if you want these cite-linked.

### 4. Content gaps flagged in-text

Three structural gaps:

- **Chapter 8 (Mixed-Effects Models)** originally presumed a regression-fundamentals background. **Chapter 7 now fills that gap** — linear regression, logistic regression, diagnostics, interpretation. Update any prerequisite callouts in Ch 8 accordingly on the next adaptation pass.
- **Chapter 9 (Text Analysis)** is adapted from "Part 2" of a two-part LADAL series; "Part 1" (introta, conceptual foundations) is not in this book. Options: add introta as new content, write a short refresher into Ch 9, or brief participants verbally.
- **Chapter 7** does not cover PCA or clustering (the "multivariate techniques" part of the course description). Points to LADAL tutorials and standard references in its Further Resources section.

### 5. Pre-course email to students needs updating

The welcome email already sent to students contains **stale LADAL URLs** (from the old LADAL slug naming): fix before pointing anyone at the links. Replace in that email:

- `/tutorials/r_intro/r_intro.html` → `/tutorials/intror/intror.html`
- `/tutorials/quant_intro/quant_intro.html` → `/tutorials/introquant/introquant.html`
- `/tutorials/data_loading/data_loading.html` → `/tutorials/load/load.html`
- `/tutorials/regular_expressions/` → `/tutorials/regex/`
- `/tutorials/publish/` → `/tutorials/bookdown/`
- `/tutorials/text_analysis_intro/` → `/tutorials/introta/`
- `/tutorials/text_analysis/text_analysis.html` is correct — leave alone

The pre-course package install list in the email covers only 4 packages (tidyverse, here, flextable, readxl). The full book uses roughly 40. Send a follow-up with the complete install block (easiest: lift the `install-*` chunks from each chapter's setup section).

## Chapter adaptation conventions

Apply these when converting the remaining June drafts (chapters 3, 4, 8, 9).

### Strip LADAL boilerplate

- YAML `params:` block
- `schema-org` JSON-LD chunk (SEO metadata, irrelevant outside the LADAL site)
- Decorative UQ Great Court banner (`uq1.webp`) and chili icons (`gy_chili.png`, `yr_chili.jpg`, `g_chili.jpg`)
- "Prerequisite Tutorials" callout at the top (replace with a short note referencing book chapters if needed)
- "Citation" callout at the top with the auto-generated BibTeX chunk
- "Citation & Session Info" block at the bottom and the `sessionInfo()` call
- AI Transparency Statement callout
- "Back to top" / "Back to HOME" navigation links
- Empty References section (handled book-wide by `references.bib` + `99-references.qmd`)

Replace with a single `callout-note` **Attribution** block at the end of the chapter pointing to the LADAL source URL.

### Namespace heading IDs

Every section ID gets a unique `{#sec-<topic>-<section>}` prefix because the LADAL originals all reuse generic IDs (`#intro`, `#setup`, `#preparation`, `#prep`) that collide once chapters live in one book.

- `#intro` → `#sec-dataviz-intro`, `#sec-stats-intro`, `#sec-publish-intro`
- `#setup` → `#sec-<topic>-setup`
- `#assumptions` → `#sec-stats-assumptions`
- etc.

For cross-references between chapters, use `@sec-...` (Quarto cross-reference syntax), not raw `#anchor` links.

### Rename collision-prone chunks

Chunk labels must be unique book-wide. Suffix collision-prone names with the chapter topic:

- `setup` → `setup-dataviz`, `setup-stats`, `setup-publish`
- `load`, `load-data`, `prep3`, `prep5` → `-<topic>` suffix
- Any chunk whose name is likely used elsewhere (plot1, model1, check, install) → `-<topic>` suffix

### Fix data paths

- `base::readRDS("tutorials/<topic>/data/<file>.rda", "rb")` → `base::readRDS(here::here("data", "<file>.rda"))`
- `read.csv("data/<file>.csv")` → `read.csv(here::here("data", "<file>.csv"))`

The `here::here()` call makes paths work regardless of where in the project the chapter is being rendered from.

### Fix LADAL cross-references

- Internal cross-refs to another LADAL tutorial that **is** in this book → convert to `@sec-...`
- Cross-refs to tutorials **not** in this book → either remove, or keep as external hyperlinks to the live LADAL page

## Open TODOs

1. **Adapt June drafts** — chapters 3, 4, 8, 9 need the convention pass above
2. **Wire everything into `_quarto.yml`** — chapters 3, 4, 8, 9 are the only ones currently active; uncomment 1, 2, 5, 6, 7, 10 and sort
3. **Source missing data files** (see §1 above)
4. **First end-to-end render test** — `quarto render` from the project root, fix whatever breaks
5. **Verify checkdown** rendering in the Quarto book context
6. **Verify bibliography entries** marked `% VERIFY`
7. **Update Chapter 8 prerequisites callout** — it can now point to Chapter 7 for the regression background that was previously a gap
8. **Decide on introta** for Chapter 9 — add, write a short refresher, or brief verbally
9. **Fix the welcome email** — replace stale LADAL URLs (see §5)
10. **Send follow-up email** with the full ~40-package install block
11. **Publish to GitHub Pages** — Approach A for first publish; migrate to Approach B later if desired
