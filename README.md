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

### Typical day structure

> ⚠ **Confirm with your instructor.** The schedule below is indicative. Please check the final times on the LSF entry.

| Time        | Activity               |
|-------------|------------------------|
| 09:00–09:10 | Welcome / recap        |
| 09:10–10:10 | Session 1              |
| 10:10–10:25 | Break                  |
| 10:25–11:55 | Session 2              |
| 11:55–12:55 | Lunch                  |
| 12:55–14:10 | Session 3              |
| 14:10–14:25 | Break                  |
| 14:25–15:25 | Session 4              |
| 15:25–16:15 | Session 5              |
| 16:15–16:30 | Wrap-up / next-day preview |

Total contact time: **8 academic hours (6 real hours) per day**, 32
academic hours across the four days.

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

> If your pre-course email asked you to create a folder called `R4SHH`,
> use `R-4-HASS` instead — it matches this repository and will save
> confusion on Day 1.

### 4. Have your laptop charged and ready

You will spend four full days on your own laptop. Bring a charger. If
your laptop is on an institutional lockdown (university-managed,
corporate security), check in advance that you have administrator
rights to install software.

### 5. Confirm your Studiengang

If you haven't already, submit this short form so I can register your
Prüfungsleistung correctly:

👉 <https://forms.gle/3R8pgTvNDLd5AuNP9>

### 6. Troubleshooting

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
- **Between the two blocks** (Dec 19 → Jan 8): if you want extra prep,
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

| Studiengang / Modul                              | What you submit                                                                                                                                                                                                      |
|--------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Hauptseminar P 12.2** (Lehramt Gymnasium)      | **Hausarbeit** — a term paper (ca. 15–20 pages) on an English linguistics or closely related topic, using textual data analysed in R. Standard structure: introduction, background, data & methods, results, discussion. Submission of your analysis code alongside the paper is encouraged. |
| **Masterseminar WP 33.1**                        | **Reproducible Quarto document** via public GitHub repository. Present one method from the seminar on a worked example. Scope: ca. 8–12 pages rendered HTML.                                                        |
| **GGSP and all other Studiengänge**              | Reproducible Quarto document (as above). Scope: ca. 5–8 pages rendered HTML.                                                                                                                                       |

**Submission deadline:** 31 March 2027 for all tracks.

> ⚠ **Verify independently with your Prüfungsamt.** Prüfungsordnungen
> vary; the overview above is a guide, not a binding commitment.

The technical skills needed for the Quarto document route (Quarto,
Git, GitHub, GitHub Pages) are covered during the seminar — especially
Day 4.

---

## How this repository is organised

```
R-4-HASS/
├── chapters/        # The book chapters (one .qmd per chapter)
├── data/            # Example data (populate from USB on Day 1)
├── docs/            # Rendered book (what GitHub Pages serves)
├── teaching/        # Instructor's day-by-day teaching scripts
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
subject line:

> `LMU — question about mixed-effects models`

Emails without the `LMU` prefix may be missed. Note that I am based
in Australia (UTC+10) outside the Blockseminar weekends, so expect a
timezone delay in replies.

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

**Looking forward to meeting you all in December.**
