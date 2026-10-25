# R-4-HASS — Quarto Book Project

Working materials for *Quantitative and Reproducible Research with R in the Humanities*.

## Status

Quarto **book** project (not bookdown — uses native `.qmd`). 4 of 11 planned units are drafted, converted from LADAL tutorials. The rest are awaiting source material.

| # | Unit | Status |
|---|------|--------|
| 1 | Introduction to R and RStudio | not started |
| 2 | Working with Data in R | not started |
| 3 | String Processing | ✅ `chapters/03-string-processing.qmd` |
| 4 | Regular Expressions | ✅ `chapters/04-regular-expressions.qmd` |
| 5 | Data Cleaning, Processing, Annotation | not started |
| 6 | Data Visualisation with ggplot2 | not started |
| 7 | Statistical and Multivariate Analysis | not started |
| 8 | Mixed-Effects Models | ✅ `chapters/08-mixed-effects-models.qmd` |
| 9 | Text Analysis (Corpus Methods) | ✅ `chapters/09-text-analysis.qmd` |
| 10 | Reproducible Research with Quarto | not started |
| 11 | Publishing via GitHub | not started |

## Before you render

You need R + Quarto installed locally — neither was available in the environment these files were prepared in, so **none of the 4 drafted chapters have been render-tested**. Run `quarto render` from the project root and fix whatever breaks; the most likely failure points are listed below.

### 1. Missing data files (will cause hard errors)

Copy these from the original LADAL tutorial data repositories into `data/`:

- **String processing**: `tx1.rda`, `tx2.rda`, `tx3.rda`, `tx4.rda`
- **String processing (paused exercise)**: `testcorpus/linguistics04.txt` — also has hardcoded quiz answers (101 words, 673 characters) tied to this exact file; see the TODO callout in the chapter.
- **Mixed-effects models**: `lmd.rda`, `mbd.rda`, `cld.rda`, `ratex.rda`, `pict.rda`
- **Text analysis**: `darwin.rda`, `melville.rda`, `orwell.rda`. (`alice.rda` is optional — the chapter falls back to downloading *Alice in Wonderland* via `gutenbergr` if the file isn't present.)

Each location is also flagged with a `callout-warning` directly in the relevant `.qmd` file.

### 2. checkdown rendering — UNVERIFIED

All four chapters keep their original `checkdown` interactive quiz blocks (radio-button questions, hints). This package is built for plain RMarkdown/Quarto HTML output and *should* work in a Quarto book, but this has not been confirmed. After your first render, check that the quiz widgets actually display and function. If they don't, the fallback is converting them to static `callout-tip` "Exercise" blocks — flag it and that's a quick fix.

### 3. Bibliography — needs verification

`references.bib` contains 10 real citation keys pulled from the source material (Barr et al. 2013, Bartoń/MuMIn, Bell 2008, Friedl 2006, Johnson 2009/2014, Murayama 2014, Peng 2016, Pinheiro & Bates 2000, Winter 2019, Zuur & Ieno). Several entries are marked `% VERIFY` because I could not confirm exact page numbers, editions, or — in one case — the correct year, against primary sources. Check these against the original publications before publishing.

### 4. Content gaps flagged in-text

Two structural gaps are called out as `callout-warning` blocks inside the chapters themselves, not just here:

- **Mixed-Effects Models** presumes a regression-fundamentals background (OLS, fixed-effects logistic/ordinal regression) that no other planned unit currently covers.
- **Text Analysis** is adapted from "Part 2" of a two-part LADAL series; "Part 1" (conceptual foundations) isn't part of this book.

Decide whether to add prerequisite content, write a short refresher into the existing chapters, or accept the gap and brief participants verbally.

## Heading ID convention

Every chapter section uses a unique `{#sec-<chapter>-<section>}` ID (e.g. `{#sec-string-processing-intro}`, `{#sec-regex-patterns}`). This was necessary because the original LADAL tutorials all reused generic IDs like `#intro` and `#setup`, which collide once multiple tutorials live in one book. **Keep this convention** for any new chapters you add or convert, and use `@sec-...` (not raw `#anchor` links) for any cross-references between chapters.

## What was stripped from the original LADAL tutorials

- YAML `params:` blocks, schema.org JSON-LD (SEO metadata, irrelevant outside the LADAL website)
- Per-chapter "Citation" callouts and auto-generated BibTeX blocks
- `sessionInfo()` dumps
- "AI Transparency Statement" callouts (replaced book-wide by the acknowledgement in `index.qmd` plus one short "Source and Attribution" note per chapter)
- Cross-links to other LADAL tutorials not included in this book (e.g. `r_intro`, `data_loading`, `table`, `regression`, `text_analysis_intro`) — either removed or, where the target chapter *is* in this book (String Processing, Regular Expressions), converted to real `@sec-...` cross-references
- LADAL banner/decorative images (`uq1.webp`, `gy_chili.png`, `yr_chili.jpg`)
