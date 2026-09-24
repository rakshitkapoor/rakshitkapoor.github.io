
# Rakshit's Quarto Website

This repository contains my personal website and blog, built with [Quarto](https://quarto.org/). It includes computational posts written in Python and R for DSCI 521 Milestone 3.

## Website and repository

- **Live website:** https://rakshitkapoor.github.io/
- **GitHub repository:** https://github.com/rakshitkapoor/rakshitkapoor.github.io

## Computational posts

### Python: Exploring Penguin Size

**File:** `posts/penguin-python/index.qmd`

This post uses Python to investigate penguin body mass and flipper length. It includes data exploration, species-level summary statistics, a scatter plot, and a comparison of average body mass.

**Main packages:** `palmerpenguins`, `pandas`, and `matplotlib`.

### R: Exploring Penguin Bill Measurements

**File:** `posts/penguin-r/index.qmd`

This post uses R to compare bill length and bill depth across penguin species. It includes data exploration, grouped summary statistics, a scatter plot, and a comparison of average bill length.

**Main packages:** `palmerpenguins`, `dplyr`, `ggplot2`, and `knitr`.

## Dataset

Both posts use the [Palmer Penguins dataset](https://allisonhorst.github.io/palmerpenguins/), which contains measurements of Adelie, Chinstrap, and Gentoo penguins.

The dataset is available through the `palmerpenguins` packages for Python and R. The posts load the data directly from the installed packages rather than downloading a CSV file during rendering.

Dataset reference:

Horst, A. M., Hill, A. P., and Gorman, K. B. (2020). *palmerpenguins: Palmer Archipelago (Antarctica) penguin data*. R package.

## Prerequisites

To reproduce the website, install:

- [Git](https://git-scm.com/)
- [Quarto](https://quarto.org/docs/get-started/)
- [uv](https://docs.astral.sh/uv/)
- Python 3.14, managed through `uv`
- R 4.6.1
- The R package `renv`

Python dependencies are recorded in `pyproject.toml` and `uv.lock`. The Python version is specified in `.python-version`.

R dependencies are recorded in `renv.lock`, and the project uses `renv` for package management.

## Reproduce the website

### 1. Clone the repository

```bash
git clone https://github.com/rakshitkapoor/rakshitkapoor.github.io.git
cd rakshitkapoor.github.io
```

### 2. Restore the Python environment

Install the locked Python dependencies:

```bash
uv sync --locked
```

The project uses Python 3.14. The `uv` environment includes Jupyter and `ipykernel`, which Quarto uses to execute the Python post.

### 3. Restore the R environment

Start R from the repository root:

```bash
R
```

Install `renv` if it is not already available:

```r
install.packages("renv", repos = "https://cloud.r-project.org")
```

Restore the packages recorded in the lockfile:

```r
renv::restore()
```

Exit R:

```r
q()
```

If prompted to save the workspace, select **No**.

### 4. Render the website

From the repository root, run:

```bash
uv run quarto render
```

Quarto executes the computational posts and generates the complete website in the `docs/` directory.

To preview the website locally, run:

```bash
uv run quarto preview
```

### 5. View the generated website

The generated website is stored in `docs/`. GitHub Pages publishes this directory from the repository's `main` branch.

The live website is available at:

https://rakshitkapoor.github.io/

## Repository structure

```text
.
├── _quarto.yml
├── index.qmd
├── about.qmd
├── blog.qmd
├── posts/
│   ├── first-weeks/
│   │   └── index.qmd
│   ├── penguin-python/
│   │   └── index.qmd
│   └── penguin-r/
│       └── index.qmd
├── pyproject.toml
├── uv.lock
├── .python-version
├── renv.lock
├── .Rprofile
├── renv/
│   └── activate.R
├── docs/
│   └── .nojekyll
└── README.md
```

## Reproducibility

The repository includes separate dependency management for Python and R:

- **Python:** `uv.lock` records the resolved Python dependencies.
- **R:** `renv.lock` records the R package versions.
- **Quarto:** Both computational posts contain executable code chunks and display their generated results.

The `.venv/`, `renv/library/`, and `.quarto/` directories are excluded from Git because they contain local environments or generated files. They can be recreated using the instructions above.

The rendered website is committed in `docs/` for GitHub Pages deployment.