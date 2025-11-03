# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Quarto book project titled "Estimation Statistics" that teaches statistical concepts focused on effect sizes and confidence intervals as alternatives to traditional p-value-based hypothesis testing. The book is written in R using Quarto markdown (.qmd) files and renders to HTML and PDF formats.

## Build and Development Commands

### Building the Book

```bash
quarto render
```
Output is generated in the `docs/` directory.

### Preview the Book

```bash
quarto preview
```
Opens an interactive preview in the browser that auto-refreshes on changes.

### Render Specific Formats

```bash
# HTML only
quarto render --to html

# PDF only
quarto render --to pdf
```

## Project Structure

### Book Configuration
- `_quarto.yml` - Main Quarto configuration defining book structure, chapters, formats, and theme
- Book chapters are defined in order:
  - `index.qmd` - Introduction/Motivation
  - `01-effect-sizes.qmd` - Effect Size chapter
  - `02-confidence-intervals.qmd` - Confidence Intervals chapter
  - `03-using-estimations.qmd` - Putting the pieces together chapter
  - Appendices: `prerequisites.qmd` and `r-fundamentals.qmd`

### R Environment
- Uses `renv` for R package management (R 4.4.1)
- `.Rprofile` loads renv automatically
- `renv.lock` defines package dependencies

### Key R Packages Used
Based on the content, the book uses:
- `effectsize` - Computing effect sizes like Cohen's d
- `dabestr` - Creating Gardner-Altman and Cumming estimation plots
- `besthr` - Creating Derevnina plots for categorical data
- `resample` - Bootstrap estimation of confidence intervals
- `ggplot2` - Plotting and visualization
- `dplyr` - Data manipulation

### Assets
- `fig/` - Contains figures and images used in the book
- `book.bib` - Bibliography references
- `packages.bib` - Package citations

## Book Content Architecture

The book teaches estimation statistics through three main concepts:

1. **Effect Sizes** (Chapter 1): Standardized measures of difference magnitude (Cohen's d, Pearson's r) that are more interpretable than p-values alone

2. **Confidence Intervals** (Chapter 2): Range estimates showing where parameters likely fall, computed both parametrically (for normal data) and via bootstrap resampling (for any distribution)

3. **Ensemble Visualization** (Chapter 3): Combining effect sizes and CIs in information-rich plots:
   - Gardner-Altman plots (two-group comparisons)
   - Cumming plots (multi-group comparisons)
   - Derevnina plots (categorical/discrete data)

The pedagogical approach emphasizes:
- Showing raw data points rather than hiding them in summary statistics
- Using multiple complementary statistics rather than relying on p-values alone
- Creating clear, interpretable visualizations that reveal data patterns

## Working with Quarto R Code

### Code Chunks
Quarto uses special code chunk syntax:

```r
#| message: false
#| echo: true
#| layout-ncol: 2
```

These chunk options control execution and output display.

### Conditional Content
The book uses format-specific content:

```
::: {.content-visible when-format="html"}
![Animation](fig/animation.gif)
:::
```

### Callouts
Special formatted boxes for notes:

```
:::{.callout-note}
## Title
Content here
:::
```

Types include: `.callout-note`, `.callout-important`, `.callout-warning`

## Development Workflow

When editing content:
1. Edit the appropriate .qmd file
2. Use `quarto preview` to see changes live
3. Verify both HTML and PDF rendering work correctly before committing
4. Check that R code chunks execute without errors
5. Ensure figures display correctly in all output formats