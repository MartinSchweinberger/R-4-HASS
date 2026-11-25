# Quantitative and Reproducible Research with R in the Humanities

**Blockseminar at Ludwig-Maximilians-Universität München**
Course number 14186 · Winter semester 2026/27
Instructor: Martin Schweinberger (University of Queensland)

Dates: **18–19 December 2026** and **8–9 January 2027**

Published book: <https://martinschweinberger.github.io/R-4-HASS/>

---

## About this course

An intensive, hands-on introduction to R for linguists and humanities
researchers. By the end of the four days you will have:

- A working R / RStudio setup, a public GitHub repository, and the skills
  to maintain both
- Confidence importing, cleaning, and visualising linguistic data
- Working knowledge of core text analytics methods — concordancing,
  frequency, collocation, keyword analysis, and network graphs
- An introduction to the main statistical models used in modern corpus
  linguistics (mixed-effects models and conditional inference trees)
- A reproducible Quarto document, hosted as a public website on GitHub
  Pages, that you can use as the template for your Prüfungsleistung

The course is **practice-oriented**. Short conceptual intros followed by
you working on your own machine, then I demonstrate, then you apply what
you've seen. Expect to spend most of each day with your hands on the
keyboard.

---

## Four-day timeline

| Day   | Date         | Focus                                 | Topics covered                                                                                      |
|-------|--------------|---------------------------------------|-----------------------------------------------------------------------------------------------------|
| Day 1 | Fri 18 Dec   | Foundations                           | RStudio, projects, packages · Git & GitHub · data types & import · `dplyr` · first `ggplot2`         |
| Day 2 | Sat 19 Dec   | Text analytics                        | String processing · regular expressions · quanteda workflow · concordancing · frequency · collocation & network graphs |
| Day 3 | Fri 8 Jan    | Statistics and modelling              | Descriptive statistics · regression concepts · mixed-effects models · conditional inference trees   |
| Day 4 | Sat 9 Jan    | Reproducible publishing               | Quarto documents · rendering · GitHub Pages · publishing your own research website                  |

### Daily structure

Each day runs for eight academic hours (six real hours), roughly
09:00–16:30, with two short breaks and a lunch break. Final times
appear in the LSF entry.

Total contact time across the four days: 32 academic hours.

---

## Before Day 1 — what you need to do

### 1. Install the software (all free and open source)

Install, in this order:

1. **R** (latest version) — <https://cran.r-project.org/>
2. **RStudio Desktop** — <https://posit.co/download/rstudio-desktop/>
3. **Quarto** — <https://quarto.org/docs/get-started/>
4. **Git** — <https://git-scm.com/downloads> (make sure to tick "add to PATH" during installation on Windows)
5. **A free GitHub account** — <https://github.com/>

### 2. Install the R packages

Open RStudio and run this once in the Console:

```r
install.packages(c(
  # Core tidyverse and workflow
  "tidyverse", "here", "readxl", "writexl",
  "flextable", "knitr", "rmarkdown", "checkdown",

  # Visualisation
  "scales", "RColorBrewer", "viridis",

  # Statistics
  "e1071", "car", "effectsize", "broom", "report", "performance",

  # Mixed-effects models
  "lme4", "lmerTest", "MuMIn", "sjPlot",

  # Tree-based models
  "partykit", "ggparty", "party", "Hmisc",

  # Text analytics
  "quanteda", "quanteda.textstats", "quanteda.textplots",
  "tidytext", "tokenizers", "gutenbergr", "tm",

  # Data formats
  "jsonlite", "xml2"
))
```

This takes 15–30 minutes depending on your connection. Run it the day
before, not on the morning of Day 1.

### 3. Create your course project

In RStudio: **File → New Project → New Directory**, name it `R-4-HASS`,
save it somewhere you'll find again.

### 4. Have your laptop charged and ready

You will spend four full days on your own laptop. Bring a charger. If
your laptop is on an institutional lockdown (university-managed,
corporate security), check in advance that you have administrator
rights to install software.

### 5. Troubleshooting

If any installation fails: email me (see **Contact** below) with the
specific error message. Don't arrive on Day 1 with it still broken —
Day 1 is tight and I can't individually debug setup issues for everyone
during class.

---

## The course book

The course has a dedicated online book covering every topic in detail:

**<https://martinschweinberger.github.io/R-4-HASS/>**

| Chapter | Topic                                               | Primary day   |
|---------|-----------------------------------------------------|---------------|
| 1       | Introduction to R and RStudio                       | Day 1         |
| 2       | Working with Data in R                              | Day 1         |
| 3       | String Processing                                   | Day 2         |
| 4       | Regular Expressions                                 | Day 2         |
| 5       | Data Cleaning and Tables                            | Day 1         |
| 6       | Data Visualisation with `ggplot2`                   | Day 1         |
| 7       | Statistics: Inferential Tests and Regression        | Day 3         |
| 8       | Mixed-Effects Models (incl. Conditional Inference Trees) | Day 3    |
| 9       | Text Analysis (Corpus Methods)                      | Day 2         |
| 10      | Reproducible Research and Publishing                | Day 4         |

### How to use the book

- **During the course:** the book is your reference. We won't read it
  cover-to-cover in class; instead, each session covers key points and
  you follow up in the book for depth.
- **Before each day:** skim the relevant chapters. Full reading is not
  required — a 15-minute browse of the headings and intro of each
  chapter is enough.
- **Between the two blocks** (19 Dec → 8 Jan): if you want extra prep,
  Chapter 7 (statistics) before Day 3 pays off.
- **After the course:** the book is your reference for your
  Prüfungsleistung.

---

## Data for the course

Corpus and example data will be distributed on **USB stick** on Day 1
(copyright restrictions mean they cannot be shared online). You will
copy the files into the `data/` folder of your `R-4-HASS` project.

Public datasets referenced in the book (e.g. Alice in Wonderland via
`gutenbergr`) can be downloaded directly from R without a USB.

---

## Assessment (Prüfungsleistung)

The Prüfungsleistung depends on the module under which you registered
for this seminar. This section covers:

1. **Which format applies to your module** — the summary table below
2. **What each format requires** — four detailed task descriptions
3. **How you will be marked** — a marking sheet per format
4. **How to submit** — email with a standardised subject line

Verify the format for your module independently with your own
Prüfungsamt. The specifications below reflect the current PStOs as
confirmed by the LMU Studierendensekretariat (Philipp Handl, November
2026), but Prüfungsordnungen vary and you remain responsible for
checking your own registration.

### Summary table — module to format

| Module                         | Format         | Length (pure text, without spaces) |
|--------------------------------|----------------|-----------------------------------|
| **P 12.2** (Lehramt Gymnasium) | Hausarbeit     | 34,000–51,000                     |
| **WP 2.1** (MA English Studies) | Essay         | 9,000–12,000                      |
| **WP 7.1** (MA English Studies) | Dokumentation | 22,500–30,000                     |
| **WP 18.1** (MA English Studies) | Dokumentation | 22,500–30,000                   |
| **WP 24.1** (MA English Studies) | Dokumentation | 5,000–7,500                     |
| **WP 25.1** (MA English Studies) | Dokumentation | 9,000–12,000                    |
| **WP 27.1** (MA English Studies) | Dokumentation | 5,000–7,500                     |
| **WP 32.1** (MA English Studies) | Dokumentation | 22,500–30,000                   |
| **WP 33.1** (MA English Studies) | Thesenpapier  | 3,000–6,000                      |
| **WP Ang 2.1** (GGSP)           | Essay          | 9,000–12,000                     |
| **WP Ang 3.1** (GGSP)           | Dokumentation  | 22,500–30,000                    |
| **WP Ang 5.1** (GGSP)           | Dokumentation  | 22,500–30,000                    |
| **WP Ang 6.1** (GGSP)           | Dokumentation  | 9,000–12,000                     |
| **WP Ang 7.1** (GGSP)           | Dokumentation  | 22,500–30,000                    |
| **WP Ang 8.1** (GGSP)           | Dokumentation  | 5,000–7,500                      |

### How character counts work

All character counts above are **pure prose text, without spaces**, and
exclude:

- Table of contents and bibliography
- Code chunks, output, and figures
- Footnotes

In Word: `Review → Word Count → Characters (no spaces)`.
For Quarto-rendered documents, the easiest check is to paste the prose
into a text editor and count characters without spaces.

Mild tolerance applies in either direction (roughly ±5%), but
substantial under- or overshooting will affect the marking.

### Submission — for all four formats

By email **from your LMU campus address** (`@campus.lmu.de`) to
**m.schweinberger@uq.edu.au**.

Subject line format (exactly):

```
LMU final assessment FIRST NAME LAST NAME
```

**Deadline: 31 March 2027.**

LMU requires all exam-related correspondence to use your campus email.
Submissions sent from private email addresses (Gmail, Yahoo, GMX,
university alumni addresses, etc.) may not be accepted. Use your
`@campus.lmu.de` address for the submission and for any related
follow-up.

---

### Format 1: Hausarbeit (P 12.2 Lehramt Gymnasium)

A traditional academic research paper applying quantitative methods
from the seminar to a question in English linguistics.

**Length:** 34,000–51,000 characters (pure text, without spaces).

**Topic:** An empirical question in English linguistics —
sociolinguistics, variationist linguistics, discourse analysis, corpus
linguistics, or a related area. Data may be your own, from the course
corpora, or from publicly available sources.

**Structure (recommended):**
1. Introduction stating the research question
2. Theoretical background and literature review
3. Data and methods
4. Results with visualisations
5. Discussion
6. Conclusion
7. References

**Methodology:** The quantitative analysis must be conducted in R.
Submission of your analysis code alongside the paper is required —
either as an appendix in the PDF or as a linked public GitHub
repository.

**Deliverable:** A single PDF, with code either appended or linked.

**Marking sheet:**

| Criterion                                      | Weight | Mark (1.0–5.0) |
|------------------------------------------------|--------|----------------|
| Research question and theoretical framing      | 20%    |                |
| Data, method, and R analysis                   | 35%    |                |
| Results and interpretation                     | 25%    |                |
| Academic writing and citations                 | 10%    |                |
| Code reproducibility                           | 10%    |                |
| **Final grade (weighted mean)**                | 100%   |                |

---

### Format 2: Dokumentation (reproducible Quarto document)

A reproducible Quarto document (`.qmd`) demonstrating one method from
the seminar applied to a worked example. The document integrates
narrative prose, R code, and output in a single file, delivered as a
public GitHub repository with rendered HTML.

**Length** (see table above for your module):
- 5,000–7,500 characters, 9,000–12,000 characters, or
  22,500–30,000 characters (pure text, without spaces)
- Code chunks, output, figures, and bibliography do not count toward
  the character budget

**Topic:** An empirical or methodological question in English
linguistics or a related humanities domain (literary studies, digital
humanities, discourse studies). Data may be your own, from the course
corpora, or from publicly available sources.

**Structure (recommended):**
1. Short introduction (motivation, research question or methodological
   focus)
2. Data (description with provenance)
3. Method (explanation and justification)
4. Analysis (R code and output with narrative commentary)
5. Interpretation
6. References

**Deliverable:** A public GitHub repository containing:
- `index.qmd` (the source Quarto document)
- Rendered HTML output
- The data file(s) or clear data provenance
- Optionally, publication via GitHub Pages (encouraged but not
  required)

For the submission email, include the repository URL (and GitHub Pages
URL, if used).

**Marking sheet:**

| Criterion                                                                  | Weight | Mark (1.0–5.0) |
|----------------------------------------------------------------------------|--------|----------------|
| Method and analysis (appropriateness, correctness, R code quality)         | 40%    |                |
| Reproducibility (anyone can clone and render)                              | 20%    |                |
| Clarity of narrative explanation                                           | 20%    |                |
| Interpretation of results                                                  | 10%    |                |
| Academic form (structure, citations, visualisation quality)                | 10%    |                |
| **Final grade (weighted mean)**                                            | 100%   |                |

---

### Format 3: Thesenpapier (WP 33.1 only)

A short thesis-driven discussion paper engaging with a methodological
or substantive issue from the seminar. In contrast to the Dokumentation
and Essay formats, the Thesenpapier is argumentative rather than
analytical: it defends a position through a structured sequence of
theses.

**Length:** 3,000–6,000 characters (pure text, without spaces; excluding
bibliography).

**Topic:** A methodological debate, theoretical issue, or practical
question arising from the seminar. Examples:
- *Is stopword removal appropriate for sociolinguistic text analysis?*
- *Mixed-effects models versus conditional inference trees in
  variationist corpus studies*
- *The limits of reproducibility in text-analytics research*

**Structure (recommended):**
1. Short opening paragraph framing the issue
2. Three to five theses, each a clear claim with a one-paragraph
   justification
3. Short closing paragraph noting implications or open questions
4. References

**Format:** Written in Quarto (`.qmd`) and rendered to PDF, Word, or
HTML before submission. The Quarto source file must be included so I
can verify the rendering workflow. An optional short R code chunk and
figure supporting one of the theses is encouraged but not required.

**Deliverable:** The rendered document (PDF, Word, or HTML) plus the
`.qmd` source file. These may be delivered as email attachments or as
a link to a public GitHub repository.

**Marking sheet:**

| Criterion                                           | Weight | Mark (1.0–5.0) |
|-----------------------------------------------------|--------|----------------|
| Clarity and originality of theses                   | 30%    |                |
| Quality of argumentation                            | 30%    |                |
| Engagement with seminar content                     | 20%    |                |
| Quarto document production and rendering            | 10%    |                |
| Academic writing and citations                      | 10%    |                |
| **Final grade (weighted mean)**                     | 100%   |                |

---

### Format 4: Essay (WP 2.1, WP Ang 2.1)

A focused academic essay on a methodological or empirical question
from the seminar, with embedded data analysis, produced in Quarto and
delivered as a rendered document.

**Length:** 9,000–12,000 characters (pure text, without spaces;
excluding bibliography, code, output, and figures).

**Topic:** An empirical or methodological question in English
linguistics or a related humanities domain. The essay should combine
argumentative discussion with at least one piece of R-based analysis
supporting the discussion.

**Structure (recommended):**
1. Introduction stating the question or thesis
2. Discussion of the method or issue (with references to seminar
   content and relevant literature)
3. An R analysis supporting the argument
4. Discussion and conclusion
5. References

**Format:** Written in Quarto (`.qmd`) and rendered to PDF, Word, or
HTML.

**Deliverable:** The rendered document (PDF, Word, or HTML) plus the
`.qmd` source file. These may be delivered as email attachments or as
a link to a public GitHub repository.

**Marking sheet:**

| Criterion                                           | Weight | Mark (1.0–5.0) |
|-----------------------------------------------------|--------|----------------|
| Clarity of argument                                 | 25%    |                |
| Method and R analysis                               | 30%    |                |
| Engagement with seminar content                     | 15%    |                |
| Reproducibility of Quarto workflow                  | 15%    |                |
| Academic writing and citations                      | 15%    |                |
| **Final grade (weighted mean)**                     | 100%   |                |

---

## How this repository is organised

```
R-4-HASS/
├── chapters/        # The book chapters (one .qmd per chapter)
├── data/            # Example data (populate from USB on Day 1)
├── docs/            # Rendered book (what GitHub Pages serves)
├── workshop/        # Day-by-day student workbooks
├── _quarto.yml      # Book configuration
├── index.qmd        # Book landing page
├── references.bib   # Bibliography
└── README.md        # This file
```

You don't need to clone this repository — the book is readable online.
If you want to clone it (to read offline, or to copy a code example):

```bash
git clone https://github.com/MartinSchweinberger/R-4-HASS.git
```

Your own project (which you create fresh on Day 1) will live in a
separate folder with the same name `R-4-HASS`, in your own GitHub
account.

---

## Getting help

### During the Blockseminar

Raise your hand. If you're stuck, chances are at least two other people
are stuck on the same thing.

### Between sessions and after the course

Email **m.schweinberger@uq.edu.au** with `LMU` at the start of the
subject line (e.g. `LMU — question about mixed-effects models`).

For exam-related correspondence use your LMU campus address
(`@campus.lmu.de`) — see the Assessment section above.

Note that I am based in Australia (UTC+10) outside the Blockseminar
weekends, so expect a timezone delay in replies.

### Where to search first

Before emailing:

1. The relevant book chapter
2. `?function_name` in R (built-in help)
3. The LADAL tutorial that chapter is based on: <https://ladal.edu.au/>
4. Stack Overflow with the `[r]` tag

---

## Common first-day problems

| Symptom                                          | Fix                                                                 |
|--------------------------------------------------|---------------------------------------------------------------------|
| `Error: could not find function "..."`           | Load the package: `library(pkg)`; install if missing                |
| `object '...' not found`                         | Run the code that creates it first                                  |
| `cannot open file '...'`                         | Check `getwd()`; use `here::here()`                                 |
| `git: command not found`                         | Reinstall Git with "add to PATH" option                             |
| No Git tab in RStudio                            | Tools → Project Options → Git/SVN, then restart RStudio             |
| Weird characters (Mßller instead of Müller)      | Encoding issue — specify UTF-8 at import time                       |

---

## Credits and licensing

The course material in this repository is adapted from tutorials
published by the **Language Technology and Data Analysis Laboratory
(LADAL)** at the University of Queensland: <https://ladal.edu.au/>

Original LADAL tutorials by Martin Schweinberger and collaborators;
adaptation for the LMU Blockseminar also by Martin Schweinberger. See
individual chapters for attribution notes.

Licence: CC BY-SA 4.0 for text content; MIT for code.

---

**Looking forward to seeing you all in December.**
